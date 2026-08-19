---
title: Gaussian Splatting
description: How 3D Gaussian Splatting represents and renders real-world scenes for fast, photorealistic novel-view synthesis
date: 2026-08-19
author: as-folio
draft: false
math: true
tags:
  - gaussian-splatting
  - 3d-reconstruction
  - computer-vision
  - neural-rendering
  - spatial-computing
---

Gaussian Splatting is a technique for reconstructing and rendering three-dimensional scenes from photographs or video. Instead of representing a scene as a mesh or generating every pixel with a large neural network, it models the scene as a collection of semi-transparent 3D particles called Gaussians.

Each Gaussian has a position, size, orientation, color, and opacity. Together, millions of these small primitives form a continuous visual representation of an object or environment. When viewed from a new camera position, the Gaussians are projected onto the image plane and blended from front to back. The result can be rendered interactively while retaining much of the appearance of the original photographs.

## The Core Idea

A three-dimensional Gaussian describes a soft region of space rather than a single point. Its shape is defined by a mean position and a covariance matrix:

$$
G(\mathbf{x}) = \exp\left(-\frac{1}{2}(\mathbf{x}-\boldsymbol{\mu})^T \boldsymbol{\Sigma}^{-1}(\mathbf{x}-\boldsymbol{\mu})\right)
$$

Here, $\boldsymbol{\mu}$ is the Gaussian's center and $\boldsymbol{\Sigma}$ controls its scale and orientation. A spherical Gaussian has the same size in every direction, while an anisotropic Gaussian can stretch along surfaces, edges, and other useful directions.

In practice, a Gaussian also stores view-dependent color coefficients, usually represented with spherical harmonics. These coefficients allow its color to change slightly as the camera moves, which helps reproduce highlights and other changes in appearance that a fixed RGB value cannot describe.

## From Images to a Scene

A typical Gaussian Splatting workflow has four stages.

### 1. Capture

The scene is photographed from many overlapping viewpoints. A handheld camera, a phone, or a multi-camera rig can be used, provided the images contain enough detail and coverage. Sharp images and consistent exposure are especially important because reconstruction quality depends on the visual evidence in the input.

Moving objects can create artifacts. For a basic reconstruction, the most reliable captures are made while the scene remains static and the camera moves around it.

### 2. Estimate Camera Poses

The system must determine where each camera was located and how it was oriented when an image was taken. Structure-from-motion tools such as COLMAP are commonly used for this step. They detect visual features, match them across images, and jointly estimate camera poses and a sparse point cloud.

These poses provide the geometric coordinate system in which the Gaussians will be optimized. If the camera estimates are inaccurate, the rendered scene may appear blurry, warped, or unstable even when the input images look good.

### 3. Initialize and Optimize Gaussians

The sparse point cloud is used to initialize a set of 3D Gaussians. During training, the system renders the current Gaussian scene from the known camera viewpoints and compares those images with the original photographs.

Optimization adjusts the Gaussian parameters to reduce the difference between rendered and reference images. The process can also split Gaussians in areas that need more detail and remove Gaussians that contribute little to the scene. This adaptive refinement lets the representation spend more primitives on edges, textured surfaces, and difficult lighting.

A simplified image loss can be written as:

$$
\mathcal{L} = (1-\lambda)\mathcal{L}_{\text{photo}} + \lambda\mathcal{L}_{\text{structural}}
$$

The photometric term measures pixel-level color differences, while the structural term encourages perceptual similarity. The exact loss varies between implementations, but the central loop remains the same: render, compare, and update.

### 4. Render New Views

At render time, each 3D Gaussian is projected into the camera view as a 2D ellipse. The projected primitives are sorted approximately by depth and composited using alpha blending. A pixel's final color is influenced by the Gaussians along its viewing ray:

$$
C = \sum_{i=1}^{N} T_i \alpha_i c_i, \qquad
T_i = \prod_{j=1}^{i-1}(1-\alpha_j)
$$

In this expression, $c_i$ is the color of a Gaussian, $\alpha_i$ is its contribution, and $T_i$ is the amount of light that remains after passing through the preceding Gaussians. Efficient GPU rasterization makes this compositing process fast enough for interactive applications.

## Why It Is Fast

Neural radiance fields, or NeRFs, usually query a neural network at many points along each camera ray. That approach can produce impressive results, but rendering may require a large number of network evaluations for every frame.

Gaussian Splatting moves much of the work into a rasterization-style pipeline. Instead of repeatedly sampling a neural field, the renderer projects explicit primitives and blends them. This makes the representation well suited to real-time viewing, camera exploration, and interactive tools.

The speed advantage does not mean that Gaussian Splatting is free. A detailed scene may contain millions of Gaussians, and each primitive stores position, covariance, opacity, and appearance data. Memory usage and scene loading time can therefore become important constraints.

## Strengths

### High Visual Quality

The representation can preserve fine texture, complex lighting, and small geometric details that are difficult to capture with a simple mesh. Novel views often look convincing when they stay within the range of viewpoints represented in the training images.

### Interactive Rendering

GPU splatting can support responsive playback and camera movement. This is useful for digital twins, virtual production, cultural heritage, product visualization, and immersive scene browsers.

### Flexible Geometry

A mesh requires explicit surfaces and topology. Gaussians are more tolerant of irregular structures, thin details, and partially reconstructed regions. They can represent visual appearance without first solving every geometric question perfectly.

### Simple View Exploration

Once the scene has been trained, users can move through it from viewpoints that were not present in the original capture. This makes Gaussian Splatting a practical format for visualizing spaces rather than merely displaying a collection of photographs.

## Limitations

Gaussian Splatting is primarily an appearance representation, not a complete physical model of the world.

- **Unseen views can fail:** The scene may look convincing from familiar angles but produce floaters, holes, or stretched textures from poorly covered viewpoints.
- **Dynamic scenes are difficult:** Standard pipelines assume that the scene is static. People, foliage, reflections, and changing illumination can leave ghosting artifacts.
- **Geometry is implicit:** The Gaussians describe where visual evidence exists, but they do not automatically provide clean surfaces, watertight meshes, or reliable measurements.
- **Transparency and reflections are ambiguous:** A photograph does not always reveal whether a color belongs to a surface, a reflection, or an object behind glass.
- **Large scenes consume memory:** High-quality captures can require millions of primitives, which affects storage, transmission, and mobile rendering.
- **Editing is not always intuitive:** Moving or deleting part of a Gaussian scene is less predictable than editing a conventional mesh or texture map.

These limitations matter when the output must support collision detection, engineering measurements, physically accurate lighting, or extensive object-level editing. In those cases, a hybrid workflow may combine Gaussian Splatting for appearance with meshes, depth maps, or semantic scene representations for structure.

## Applications

Gaussian Splatting is useful wherever realistic scene appearance and fast viewpoint changes are more important than perfect geometry.

- **Digital twins:** Create navigable visual records of buildings, factories, and infrastructure.
- **Cultural heritage:** Preserve and share archaeological sites, artworks, and historical spaces.
- **Virtual production:** Explore captured locations and plan shots before or during filming.
- **Real estate and inspection:** Present spaces remotely and document their visual condition.
- **Robotics and simulation:** Build visual environments for navigation and perception research.
- **Extended reality:** Display captured environments in augmented or virtual reality experiences.
- **Scientific visualization:** Examine objects and specimens from viewpoints that are difficult to access physically.

## Gaussian Splatting and Spatial Computing

Spatial computing systems need more than a picture. They need a representation that can be positioned in space, rendered from different viewpoints, and connected to sensors and interaction systems. Gaussian Splatting is attractive because it provides a strong visual layer while remaining compatible with camera poses and 3D coordinate systems.

A practical spatial-computing application might use a Gaussian scene for photorealistic background rendering, a mesh for collision and occlusion, and semantic labels for selecting real-world objects. This division of responsibilities is often more useful than expecting one representation to solve appearance, geometry, physics, and interaction equally well.

## The Future

Research is moving toward smaller representations, better support for dynamic scenes, improved geometric consistency, and more controllable editing. Other directions include semantic Gaussians, generative scene completion, streaming large environments, and integration with conventional graphics pipelines.

The most important shift is conceptual. 3D scenes no longer need to be treated as either hand-built meshes or opaque neural networks. Gaussian Splatting occupies a productive middle ground: it is explicit enough to render efficiently and flexible enough to reproduce the irregular visual structure found in real photographs.

## Conclusion

Gaussian Splatting offers a compelling way to turn photographs into interactive three-dimensional experiences. By representing a scene as many optimized, viewable primitives, it combines high visual fidelity with the speed of a rasterization-oriented renderer.

It is not a universal replacement for meshes, NeRFs, or physically based scene descriptions. Its best use is as part of a broader 3D pipeline, especially when realistic appearance and fast novel-view rendering are the primary goals. As capture, compression, and dynamic-scene methods improve, Gaussian Splatting is likely to become an important building block for digital twins, immersive media, and spatial computing.
