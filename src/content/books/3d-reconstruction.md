---
title: '3D Reconstruction'
author: 'Richard Szeliski'
status: interested
released: 2010
categories: computer vision, 3d reconstruction, geometry
importance: 5
---

3D reconstruction is the process of recovering the shape, appearance, and spatial arrangement of real-world objects from sensor data. It lies at the intersection of computer vision, geometry, and graphics, and enables applications such as augmented reality, robotics, cultural heritage digitization, and autonomous navigation.

Modern reconstruction pipelines use multiple images, depth sensors, or video to estimate camera poses, reconstruct surfaces, and produce textured 3D models. Key techniques include structure-from-motion, multi-view stereo, depth fusion, point cloud registration, and neural scene representations. Successful 3D reconstruction combines robust feature matching, geometric optimization, and careful handling of occlusions, noise, and lighting variation.

A strong foundation in projective geometry, optimization, and image formation is essential for understanding how 2D measurements translate into 3D structure. Advances in learning-based methods now complement classical geometry with neural priors and differentiable rendering, making 3D reconstruction a central research area in both academic and practical computer vision.

Novel techniques such a Gaussian splatting have emerged and raised the bar on the richness of quality in 3D reconstructed object. 

Tradeoffs however need to be considered while comparing with other methods such as Neural Radiance Fields (NeRFs). 
