---
title: Real-Time Multi-User Gaze Interaction for Immersive 360° Environments
date: 2026-08-09
description: A wearable gaze-driven interaction system for large-scale immersive 360° museum displays, supporting four users with marker-free calibration and low-light robustness.
tags: [gaze, immersive, interaction, museum, visualization]
categories: [demo]
toc: true
relatedPosts: true
---

This paper presents a real-time, multi-user gaze-driven interaction system designed for large-scale, immersive 360° 3D visualization environments, such as those found in museums and science centers.

## Core Problem

Existing interaction methods for immersive 360° displays — laser pointers, handheld controllers, or fixed camera arrays — often disrupt user immersion, limit mobility, or lack the precision needed for natural interaction. Gaze tracking is a natural modality, but it is rarely applied to fully immersive 360° spaces because of:

- low-light conditions in theater-style installations,
- the need for true multi-user support,
- the challenge of mapping egocentric gaze to a panoramic display without markers.

## Proposed Solution

The authors developed a custom wearable system that integrates several components to address these challenges.

### Hardware

- Lightweight active shutter 3D glasses (Volfoni Edge RF),
- Modified to include a Pupil Labs Neon eye-tracking module,
- Two IR eye cameras plus one wide-field RGB scene camera.

### Processing

- A portable Android device (Moto Edge 40 Pro),
- Handles real-time gaze estimation and wireless synchronization,
- Supports low-latency interaction across multiple users.

### Algorithm

- A feature-matching approach using XFeat,
- Aligns the scene camera's view with the 360° footage shown on the cylindrical screen,
- Enables accurate gaze mapping onto the display without fiducial markers.

## Key Capabilities

- **Marker-Free & Mobile:** Users move freely within the 9.5m diameter, 4m high cylindrical display without external tracking infrastructure.
- **Multi-User Support:** Up to four simultaneous users are supported with an average latency of ~80ms for responsive gaze interaction.
- **Low-Light Robustness:** Designed to work in the dark environments typical of immersive theaters and exhibition spaces.

## Demonstrated Applications

The system was validated in two interactive museum scenarios using a digitized version of *The Fall of the Rebel Angels*.

1. **Interactive Animation:** Users fixate on specific elements in the artwork for a set dwell time, triggering highlights and animation effects.
2. **Collaborative AI Narrative:** Multiple users jointly select objects via gaze, then a Large Language Model (ChatGPT) generates a contextual narrative about the selected elements.

## Conclusion

This work bridges the gap between natural gaze interaction and large-scale immersive environments. It offers a scalable, low-latency solution that enhances collaborative engagement in educational and cultural installations without the visual or physical distractions of traditional controllers.
