---
title: Displays 
description: pixels, color, refresh, and the images we see on screens
date: 2025-12-14
author: simon
draft: false
tags:
  - displays
  - digital-imaging
  - electronics
---
## Overview

Display technology has undergone a dramatic transformation over the past century, from the earliest cathode ray tubes to today's cutting-edge micro-LED and quantum dot displays. This book traces the technological, engineering, and commercial forces that drove each innovation, examining how the search for brightness, resolution, portability, and visual fidelity reshaped computing and entertainment.

## Key Concepts & Metrics Defined

- **Brightness (nits):** Luminous intensity; typical range 100–1000+ nits depending on application
- **Color gamut:** Percentage of CIE 1931 color space reproducible by a display
- **Contrast ratio:** Peak luminance divided by black level
- **Response time:** Milliseconds to transition between color states
- **Pixel pitch:** Distance between subpixel centers; affects perceived sharpness
- **Refresh rate:** Frames per second (Hz); higher rates reduce flicker
- **Resolution:** Number of horizontal × vertical pixels or dots per inch (PPI)

## Timeline: Display Milestones

| Year | Milestone |
| --- | --- |
| 1927 | Philo Farnsworth demonstrates first fully electronic television |
| 1954 | Color television standards established (NTSC, PAL, SECAM) |
| 1960s | Computer CRTs become standard in data centers |
| 1973 | First flat-panel LCD prototype (Sharp) |
| 1985 | Laptop computers with LCD panels emerge |
| 2002 | LCD sales exceed CRT sales globally |
| 2007 | iPhone introduces capacitive touchscreen |
| 2017 | OLED panels widely adopted in flagship smartphones |
| 2020 | Foldable phones with flexible displays reach consumers |
| 2023 | Micro-LED displays scale to commercial production |

## How a Display Creates Light

A display is a two-dimensional array of image elements called pixels. Each pixel usually contains red, green, and blue subpixels. By controlling the intensity of these subpixels, the display produces a wide range of colors through additive color mixing.

A display value is not normally perceived linearly. Doubling a digital code value does not necessarily look like twice the brightness. Transfer functions such as the sRGB curve or a power-law gamma encode brightness in a way that better matches human perception and the behavior of display hardware.

The display pipeline typically looks like this:

1. Software provides image data to the graphics system.
2. The graphics processor composes windows, text, video, and effects.
3. A display interface transmits pixel values and timing information.
4. The display controller places values into a frame buffer.
5. Pixel circuits set the brightness of the subpixels.
6. The display emits or modulates light for the viewer.

## LCD, OLED, and MicroLED

Liquid-crystal displays (LCDs) use a backlight behind a layer of liquid crystals and color filters. The liquid crystals control how much backlight passes through each subpixel. An LCD can be bright and efficient, but its black level depends on how well the liquid-crystal layer and backlight prevent light from leaking through.

Organic light-emitting diode (OLED) displays use self-emitting organic pixels. Each pixel produces its own light, so an unlit pixel can be very dark and contrast can be extremely high. OLED response times are generally fast, although brightness, power consumption, viewing conditions, and long-term pixel wear remain important design considerations.

MicroLED displays also use self-emitting pixels, but with microscopic inorganic LEDs. They can combine high brightness, strong contrast, and long life, though manufacturing very large numbers of tiny, precisely matched emitters is difficult and expensive.

Some LCD displays use local dimming. Groups of backlight LEDs are dimmed independently so dark parts of an image receive less light. Local dimming can improve contrast, but the zones are larger than individual pixels, so bright objects against dark backgrounds may produce a glow called blooming.

## Resolution, Refresh, and Motion

Resolution describes how many pixels a display has. A higher pixel density can make text and fine details appear sharper, especially when viewed close up. Perceived sharpness also depends on viewing distance, optical focus, image scaling, contrast, and the quality of the source image.

Refresh rate is the number of times per second the display updates its image, measured in hertz. A 60 Hz display updates sixty times per second, while a 120 Hz display can update twice as often. Higher refresh rates can make scrolling and animation look smoother and can reduce the time between user input and a visible update.

Pixel response time describes how quickly a pixel changes from one value to another. Slow response can cause motion smearing or ghosting even when the refresh rate is high. Variable refresh technologies allow the display to synchronize its update rate with the rendered frame rate, reducing tearing and uneven motion.

A frame is not always presented to the entire display at once. With a typical scanout process, rows are transmitted from top to bottom. If the graphics system changes the frame buffer while scanout is in progress, the display may show parts of two frames. This is screen tearing. Synchronization methods coordinate rendering and scanout to prevent it.

## Brightness, Contrast, and HDR

Brightness describes how much light a display emits, while contrast describes the relationship between its brightest and darkest visible values. A display with high peak brightness can show intense highlights, but black level and ambient room light determine how much contrast the viewer actually perceives.

High dynamic range (HDR) content uses a wider brightness range and often a wider color gamut than standard dynamic range content. HDR only works as intended when the camera, image format, operating system, application, display, and viewing environment all handle the relevant metadata and transfer function consistently.

A display cannot show detail outside its physical limits. If an image contains values brighter than the panel can produce, tone mapping compresses them into the available range. Poor tone mapping can make an image look flat, too dark, or clipped.

## Why the Same Image Looks Different

A camera records a scene from one viewpoint and under one exposure. A display recreates that scene using a different light source, a different color gamut, and a limited set of pixels. Differences can arise from:

- Lens and sensor response
- White-balance and color-profile choices
- Exposure and highlight clipping
- Compression and resizing
- Display calibration
- Viewing angle and ambient light
- Brightness and HDR tone mapping
- Differences in software color management

Color management attempts to keep these differences predictable. A color profile describes how a device represents color, and software can convert colors between spaces. Calibration measures the actual behavior of a display and creates a correction profile. Without calibration, an image may be technically valid but still appear too warm, too cool, too bright, or too saturated on a particular screen.

## The Complete Picture

Cameras and displays are best understood as connected measurement and reproduction systems. The camera samples light in space and time, turns those samples into numbers, and applies assumptions about color and human vision. The display takes those numbers and generates a new arrangement of light using its own physical limits.

The image we see is therefore the result of a chain: optics, sensor physics, electronics, algorithms, file formats, graphics systems, panel technology, and perception. Improving one link can help, but the final experience depends on how well the entire chain preserves the details that matter in the scene.




## Part I: The Cathode Ray Era (1920s–1980s)

### Chapter 1: Discovering the Electron Beam
- The physics of cathode ray tubes (CRTs)
- Early television experiments and oscilloscope adoption
- Phosphor chemistry and color reproduction challenges
- The race between RCA, Philco, and European manufacturers

### Chapter 2: CRTs in Computing
- Monochrome vector displays for early computers
- The transition to raster graphics
- IBM and the mainframe terminal market
- Graphics standards and the Apple II revolution

### Chapter 3: Color CRTs and the Consumer Market
- Shadow mask technology and color purity
- Dot pitch, convergence, and image quality metrics
- Monitor sizes and market segmentation
- The rise of arcade games and home consoles

## Part II: The Flat Panel Revolution (1990s–2000s)

### Chapter 4: Thin Film Transistors and LCD Displays
- LCD physics: liquid crystals and polarized light
- Backlight technologies (CCFL to LED)
- The invention of TFT-LCDs and mass production
- Color filters and subpixel rendering

### Chapter 5: Mobile Displays and Miniaturization
- Challenges of small-form-factor production
- Laptops and the rise of 16:9 widescreen
- Touchscreen integration and capacitive sensing
- Display resolution wars and pixel density

### Chapter 6: Large-Format LCDs
- Behind-the-scenes of TV manufacturing
- Panel economics and supply chain globalization
- Achieving brightness for bright environments
- Color accuracy standards (sRGB, DCI-P3)

## Part III: Organic and Advanced Technologies (2000s–2020s)

### Chapter 7: OLED Displays
- Organic electroluminescence and self-emissive pixels
- Early OLED prototypes at Cambridge Display Technology
- Samsung and LG's competing manufacturing paths
- Pixel degradation, burn-in, and longevity challenges

### Chapter 8: OLED Dominates Mobile
- Apple's iPhone X and the all-screen revolution
- Flexible displays and foldable phones
- AMOLED manufacturing challenges and yield rates
- Comparison with competing technologies

### Chapter 9: Micro-LED and Mini-LED
- Inorganic LED displays and pixel-level control
- Chiplet technology and transfer printing
- High brightness and outdoor visibility
- Applications in AR/VR and large displays

### Chapter 10: Quantum Dot Displays
- Colloidal quantum dot synthesis
- Quantum dot enhancement films (QDEF) for LCDs
- QD-OLED and QD-LED hybrids
- Wide color gamuts and energy efficiency

## Part IV: Emerging Frontiers (2020s and Beyond)

### Chapter 11: VR and AR Displays
- Pixel density requirements for immersion
- Micro-OLED for headsets
- Holographic and light-field displays
- Motion sickness and visual comfort

### Chapter 12: Rollable and Stretchable Displays
- Flexible substrate materials (plastic, graphene)
- Rollable TV prototypes from Samsung and LG
- Stretchable electronics for wearables
- Manufacturing scalability

### Chapter 13: E-Ink and Reflective Displays
- Electronic paper technology
- Electrophoretic displays and bistability
- E-readers, digital signage, and smart clothing
- Low power consumption advantages

### Chapter 14: Future Directions
- Holographic and volumetric displays
- Brain-computer interfaces and retinal displays
- Sustainable manufacturing and recycling
- The role of AI in display optimization


# The Evolution of Holograms

Holography began as a fascinating optical technique in the mid-20th century, transforming the way people thought about light, image formation, and three-dimensional visualization. What started as a scientific curiosity soon became a powerful tool for communication, research, and entertainment.

## Early Foundations

The roots of holography lie in the study of wave interference and diffraction. Researchers discovered that light waves could be recorded and reconstructed in ways that preserved depth and structure, making it possible to create images that appeared to float in space.

## From Science to Innovation

As the technology matured, holograms moved beyond laboratory demonstrations. They found applications in security, data storage, medical imaging, and display systems. Their ability to present information in a visually striking and spatially rich form made them valuable in both scientific and commercial settings.

## Modern Developments

Today, holography is being reshaped by advances in computational imaging, laser systems, and digital display technologies. New approaches are making holograms more realistic, interactive, and accessible, with potential uses in education, design, entertainment, and virtual collaboration.

## Why It Matters

The evolution of holograms reflects a broader story of human innovation: turning abstract physics into practical experiences. As the technology continues to improve, holograms may become an increasingly important part of how we see, learn, and communicate.

Holography is a near future here with us, ready for adoption and integration. 