---
title: "Computer Graphics — Course Outline"
summary: "A semester-length undergraduate course covering fundamentals of computer graphics, rendering, modeling, and GPU pipelines. Includes lectures, labs, assignments, and project suggestions."
author: "Course Team"
level: "Undergraduate / Graduate Intro"
credits: 3
duration: "12 weeks"
---

# Computer Graphics — Course Outline

## Course Description

An introduction to computer graphics covering mathematical foundations, 2D/3D transformations, viewing and projection, rasterization and the graphics pipeline, illumination and shading, texture mapping, geometric modeling, and an introduction to real-time and physically based rendering. The course combines lectures, hands-on labs using OpenGL/WebGL or a modern graphics API, weekly assignments, and a capstone project.

## Learning Objectives

- Understand the mathematical foundations for 3D graphics: linear algebra, matrices, and coordinate systems.
- Implement the basic graphics pipeline: modeling, viewing, projection, clipping, and rasterization.
- Describe and implement shading and lighting models: Phong, Blinn-Phong, and basics of PBR.
- Apply texture mapping, mipmapping, and sampling techniques to improve visual quality.
- Use GPUs via OpenGL/WebGL (or a modern API) to build interactive applications.
- Analyze trade-offs between performance and visual fidelity and profile simple graphics programs.
- Design and implement a small graphics project integrating learned topics.

## Prerequisites

- Calculus, linear algebra (vectors, matrices), and basic programming (C/C++/JavaScript/Python).
- Familiarity with data structures and algorithms is helpful.

## Course Structure

- Lectures: 2 per week (90 minutes total)
- Labs: 1 per week (hands-on, using OpenGL/WebGL or small framework)
- Assignments: 8–10 small programming/homework tasks
- Midterm: one theoretical/programming exam
- Final project: small team project with demo and report

## Weekly Schedule (12 weeks)

- Week 1 — Introduction & Math Review
  - Course overview, applications, history
  - Review: vectors, matrices, homogeneous coordinates
  - Lab: setting up dev environment, simple 2D drawing

- Week 2 — 2D/3D Transformations
  - Translation, rotation, scaling, composition
  - Affine transforms and homogeneous coordinates
  - Lab: implement transformation stack, scene graph basics

- Week 3 — Viewing & Projection
  - Camera models, view transformations, orthographic vs perspective
  - Projection matrices and clipping
  - Lab: implement camera controls and projection

- Week 4 — Rasterization Pipeline
  - Vertex processing, primitive assembly, rasterization basics
  - Scan conversion, line drawing, triangle rasterization
  - Lab: software rasterizer for triangles (simple)

- Week 5 — Texturing & Sampling
  - Texture coordinates, sampling, filtering, mipmaps
  - Texture atlases and UV mapping
  - Lab: apply textures and implement texture filtering

- Week 6 — Shading & Lighting Models
  - Ambient, diffuse, specular lighting; Phong and Blinn-Phong
  - Gouraud vs Phong shading
  - Lab: implement per-vertex and per-fragment shading

- Week 7 — Midterm & Intermediate Topics
  - Midterm exam (theory + programming)
  - Introduction to normal mapping and bump mapping
  - Lab: normal mapping demo

- Week 8 — Geometry & Modeling
  - Parametric curves and surfaces (Bezier, B-splines)
  - Mesh representations, normals, adjacency
  - Lab: simple mesh loader and inspection tool

- Week 9 — Advanced Rasterization & Optimization
  - Depth buffering, stencil buffer, back-face culling
  - Level-of-detail, culling techniques, batching
  - Lab: implement depth test and simple frustum culling

- Week 10 — Introduction to Programmable Pipeline
  - GLSL / shader programming basics, vertex and fragment shaders
  - Uniforms, attributes, varyings, buffer objects
  - Lab: write shaders for lighting and texturing

- Week 11 — Introduction to Real-time & PBR Concepts
  - Physically Based Rendering overview, BRDF basics
  - Image-based lighting, environment maps
  - Lab: implement a PBR demo or simplified BRDF

- Week 12 — Rendering Effects, Project Demos & Wrap-up
  - Post-processing, shadow mapping, screen-space effects
  - Final project presentations and demos
  - Course summary and next steps in graphics research

## Labs & Assignments (Examples)

- Lab 1: Dev environment + 2D drawing (WebGL or OpenGL starter)
- Lab 2: Transformation stack and camera
- Lab 3: Software rasterizer (triangles)
- Lab 4: Texture mapping and filtering
- Lab 5: Shader basics — implement Phong shading
- Assignment: Implement a small 3D scene renderer with camera controls
- Assignment: Implement normal mapping and a simple LOD system

## Final Project Ideas

- Simple real-time renderer with multiple light types and shadows
- PBR material viewer with environment lighting and IBL
- Terrain rendering with LOD and texture splatting
- GPU particle system (fire, smoke) using instanced rendering
- Procedural modeling (trees, buildings) with L-systems

## Assessment & Grading (Example)

- Labs and assignments: 40%
- Midterm exam: 20%
- Final project: 30%
- Participation / quizzes: 10%

## Recommended Textbooks & Resources

- Primary: "Fundamentals of Computer Graphics" by Peter Shirley et al.
- Alternative: "Computer Graphics: Principles and Practice" by Foley, van Dam, et al.
- Online: LearnOpenGL (learnopengl.com), WebGL fundamentals (webglfundamentals.org)
- Shader reference: The Book of Shaders (thebookofshaders.com)

## Tools & Libraries

- OpenGL (desktop), WebGL (web), or graphics frameworks (three.js, BGFX)
- GLSL for shader development; optional HLSL/Vulkan for advanced courses
- Development: C/C++, Python with moderngl, or JavaScript with WebGL/Three.js

## Assessment Rubric (Project)

- Correctness & functionality: 40%
- Visual quality & technical complexity: 25%
- Code quality & documentation: 15%
- Performance & optimization: 10%
- Presentation & report: 10%

## Extensions & Advanced Topics (optional)

- Ray tracing and path tracing fundamentals
- Global illumination techniques
- Advanced GPU techniques, compute shaders
- VR/AR rendering considerations

## Notes for Instructors

- Adapt weekly pacing to a quarter or semester system (12–14 weeks vs 10 weeks).
- Choose APIs based on students' background: WebGL/Three.js for accessibility, OpenGL for lower-level understanding, or Vulkan/DirectX for advanced courses.
- Provide starter code and continuous integration for assignment testing where possible.

---

If you want this file placed somewhere else or need a shorter/longer version, tell me where and I will adjust it.
