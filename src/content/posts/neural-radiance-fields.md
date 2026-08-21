---
title: Neural Radiance Fields (NeRFs)
description: How neural radiance fields learn 3D scenes from images and render photorealistic novel views
date: 2026-08-21
author: as-folio
draft: false
math: true
tags:
  - neural-radiance-fields
  - nerf
  - 3d-reconstruction
  - computer-vision
  - neural-rendering
---

Neural radiance fields, usually called NeRFs, are a way to represent a three-dimensional scene using a neural network. Given a position in space and a viewing direction, the network predicts the color and density of the scene at that location. A renderer then samples those predictions along camera rays to synthesize images from viewpoints that were not present in the original photographs.

Unlike a traditional mesh, a NeRF does not begin with explicit polygons, textures, or a scene graph. It learns a continuous function from calibrated images. The result is an implicit representation: the scene is not stored as a list of visible surfaces, but as a field that can be queried throughout space.

## The Core Idea

A basic NeRF models a function of position and direction:

$$
F_{\theta}(\mathbf{x}, \mathbf{d}) = (\mathbf{c}, \sigma)
$$

Here, $\mathbf{x} = (x, y, z)$ is a three-dimensional position, $\mathbf{d}$ is the viewing direction, $\mathbf{c}$ is the predicted RGB color, and $\sigma$ is the density at that point. The parameters $\theta$ belong to a multilayer perceptron, or MLP, that is optimized during training.

Density mainly describes the scene's underlying geometry. Color can depend on the viewing direction, allowing the field to reproduce effects such as glossy highlights, reflections, and other view-dependent appearance. This separation is useful because a surface may occupy the same location while looking different from different angles.

## From Images to a Radiance Field

A typical NeRF workflow has four important ingredients.

### 1. Capture Images

The scene is photographed from many overlapping viewpoints. The images should cover the object or environment well, with enough visual detail for the network to associate changes in appearance with changes in position and camera angle.

NeRF assumes that the scene is mostly static during capture. Moving people, changing shadows, and uncontrolled exposure can make it difficult to learn one consistent field.

### 2. Calibrate the Cameras

For every training image, the system needs the camera's position, orientation, and often its focal parameters. Structure-from-motion tools can estimate these values from image correspondences. The camera poses define the rays that connect image pixels to points in the reconstructed scene.

Accurate calibration is essential. If the poses are wrong, the network receives contradictory evidence: the same physical feature appears to occupy incompatible locations. The result may be blurry geometry, distorted surfaces, or floating artifacts.

### 3. Sample Points Along Rays

For a pixel, the renderer casts a ray through the scene. A point along that ray can be written as:

$$
\mathbf{r}(t) = \mathbf{o} + t\mathbf{d}
$$

where $\mathbf{o}$ is the camera origin, $\mathbf{d}$ is the ray direction, and $t$ is the distance from the camera. The renderer evaluates the NeRF at a sequence of sampled distances $t_1, t_2, \ldots, t_N$.

Positional encoding is commonly used to map coordinates into a richer set of sinusoidal features before they enter the MLP. This helps the network represent high-frequency details that are difficult to learn from raw coordinates alone.

### 4. Optimize the Network

The sampled colors are composited into a predicted pixel color and compared with the corresponding pixel in the training image. The network weights are updated to reduce this image-space error across many rays and viewpoints.

A simple training objective is:

$$
\mathcal{L}(\theta) = \sum_{r \in \mathcal{R}} \left\| \hat{C}_{\theta}(r) - C(r) \right\|_2^2
$$

where $C(r)$ is the observed color for ray $r$ and $\hat{C}_{\theta}(r)$ is the color rendered by the current network.

## Volume Rendering

The key operation in a NeRF is differentiable volume rendering. Each sample contributes color according to its density and its visibility along the ray:

$$
\hat{C}(\mathbf{r}) = \sum_{i=1}^{N} T_i \alpha_i \mathbf{c}_i
$$

with

$$
\alpha_i = 1 - \exp(-\sigma_i \delta_i), \qquad
T_i = \prod_{j=1}^{i-1}(1-\alpha_j)
$$

Here, $\sigma_i$ is the predicted density at sample $i$, $\delta_i$ is the distance to the next sample, $\alpha_i$ is the probability that the sample contributes to the ray, and $T_i$ is the transmittance from the camera to that sample. In plain terms, points contribute strongly when they are dense and have not been hidden by material closer to the camera.

Because the rendering equations are differentiable, the error in a pixel can flow backward through the ray samples and into the neural network. This lets ordinary gradient-based optimization learn a scene directly from images.

## Why NeRFs Look Convincing

A NeRF is trained against many views at once. To match those views, it must place density in locations that explain the observed silhouettes and textures. It must also learn how appearance changes with viewing direction.

This joint optimization produces more than a collection of memorized photographs. Within the range of the training cameras, the learned field can interpolate smoothly between viewpoints. Fine texture, soft edges, and complex visibility effects can emerge from the continuous representation without being explicitly modeled as separate assets.

The quality is still closely tied to the capture. NeRFs are strongest when the scene is static, the camera poses are accurate, and the training views provide broad coverage.

## Strengths

### Photorealistic Novel Views

NeRFs can synthesize detailed images from camera positions that were not included in the training set. This makes them useful for virtual cameras, immersive experiences, and visualizing objects from difficult angles.

### Continuous Scene Representation

The field can be queried at arbitrary points rather than only at mesh vertices or texture coordinates. This gives the representation a natural way to model irregular surfaces, soft boundaries, and view-dependent appearance.

### Differentiable Rendering

The complete image formation process is differentiable. Researchers can therefore optimize scene parameters, camera poses, appearance, or even downstream objectives through the renderer.

### Flexible Extensions

The original formulation has inspired methods for unbounded scenes, dynamic objects, semantic labeling, relighting, generative completion, and 3D-aware editing. It is better understood as a family of representations than as one fixed architecture.

## Limitations

NeRFs also have practical limitations.

- **Rendering can be slow:** A single pixel may require many neural-network evaluations, and an image contains thousands or millions of pixels.
- **Training is computationally expensive:** Learning a high-quality field can require substantial GPU time and memory.
- **Geometry is not automatically clean:** Density can explain images without forming a watertight, metrically accurate surface.
- **Dynamic scenes are difficult:** A single static field cannot easily represent objects that move or lighting that changes during capture.
- **Unseen viewpoints can fail:** The network may hallucinate or stretch content when asked to render areas with little training coverage.
- **Editing is indirect:** Conventional mesh editing tools do not map naturally onto the weights of an MLP.
- **Large environments are challenging:** A single field may struggle with scale, memory, and camera coverage in outdoor or city-sized scenes.

These limitations have motivated faster representations and hybrid pipelines. Many practical systems combine neural fields with meshes, depth sensors, point clouds, or explicit primitives.

## NeRFs and Gaussian Splatting

NeRFs and Gaussian Splatting solve a similar problem but use different scene representations. A NeRF stores the scene in the parameters of a neural function and renders it by sampling along rays. Gaussian Splatting stores explicit 3D primitives and renders them by projecting and compositing those primitives.

The distinction creates a useful tradeoff:

| Property | NeRF | Gaussian Splatting |
| --- | --- | --- |
| Representation | Implicit neural field | Explicit 3D Gaussians |
| Rendering | Ray sampling and network queries | Projection and rasterization |
| Training | Neural optimization | Primitive optimization |
| Novel-view quality | High with good coverage | High with good coverage |
| Interactive rendering | More difficult in the original form | A central design goal |
| Editing and geometry | Indirect and approximate | More explicit, but still appearance-focused |

Neither representation is universally better. NeRFs remain valuable when differentiability, continuous querying, or view-dependent modeling is central. Gaussian Splatting is often preferable when responsive rendering and explicit scene primitives matter most.

## Applications

- **Virtual production:** Place a virtual camera inside a captured location and explore shots without rebuilding the set.
- **Cultural heritage:** Preserve objects and spaces as viewable 3D records.
- **Product visualization:** Present objects with realistic appearance from many angles.
- **Robotics:** Use learned scene representations for perception and simulation research.
- **Telepresence:** Reconstruct people or environments for remote viewing.
- **Real estate and inspection:** Create navigable records of buildings and infrastructure.
- **Augmented and virtual reality:** Render captured environments as immersive spatial content.

## The Future of Neural Fields

Current research is focused on making neural fields faster, smaller, more editable, and more reliable outside the training views. Hash-grid encodings, distillation, tensor decompositions, and other acceleration methods reduce the cost of network queries. Hybrid methods combine fields with explicit geometry or primitives to improve rendering speed and control.

Other important directions include dynamic and 4D fields, semantic scene understanding, relighting, generative scene completion, and streaming representations for large environments. These approaches point toward systems that do not merely replay captured appearance, but understand and manipulate scenes in a more structured way.

## Conclusion

Neural radiance fields changed how computer vision and graphics approach 3D reconstruction. Instead of reconstructing a scene only as polygons or point samples, they learn a function that describes density and appearance throughout space.

Their strength comes from the connection between learning and rendering: the same differentiable model that explains the training images can generate new views. NeRFs are not a replacement for every 3D representation, but they provide a powerful foundation for photorealistic view synthesis and continue to influence the design of modern neural scene representations.
