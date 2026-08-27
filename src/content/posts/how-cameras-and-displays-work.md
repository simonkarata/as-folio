---
title: How Cameras and Displays Work
description: From photons and lenses to pixels, color, refresh, and the images we see on screens
date: 2026-08-27
author: as-folio
draft: false
tags:
  - cameras
  - displays
  - digital-imaging
  - electronics
  - optics
---

Cameras and displays perform opposite transformations. A camera turns light into data, while a display turns data back into light. Together they form a complete image system: the scene produces photons, a sensor measures them, software processes the measurements, and a screen emits a new pattern of light for our eyes.

The process is not a perfect copy. Every stage has limits involving resolution, brightness, color, noise, timing, and the way human vision works. Understanding those limits explains why a photograph can look different from its subject and why two screens can show the same image differently.

## From Light to an Image

Visible light is electromagnetic radiation with wavelengths that the human eye interprets as colors. An object appears colored because it reflects some wavelengths more strongly than others. A camera lens gathers this reflected light and focuses it onto an image sensor.

A simplified camera pipeline is:

1. Light reflects from a scene.
2. The lens focuses that light onto the sensor.
3. The sensor converts photons into electrical charge.
4. Readout electronics convert charge into digital values.
5. An image processor applies color, exposure, noise, and sharpness corrections.
6. The camera stores the resulting image as a file or sends it to another device.

A display reverses the direction of this pipeline. It reads digital image values, converts them into electrical signals, controls light-producing or light-filtering elements, and sends light toward the viewer.

## The Camera Lens

A lens is an optical system made from one or more pieces of shaped glass or plastic. Its main job is to focus light, but it also influences field of view, brightness, distortion, depth of field, and sharpness.

The focal length determines how wide a scene appears. A short focal length produces a wide field of view, while a long focal length produces a narrower view with greater magnification. The sensor size also matters: the same lens can appear wider or narrower on different sensor formats.

The aperture is the opening through which light enters the camera. It is described by an f-number, such as f/2.0 or f/8. The f-number is the focal length divided by the diameter of the entrance pupil. A smaller f-number means a larger opening and more light.

A wider aperture also produces a shallower depth of field. Objects near the focus distance appear sharp while objects farther away become blurred. This effect depends on aperture, focal length, focus distance, and sensor size.

Lenses are imperfect. They can introduce chromatic aberration, distortion, vignetting, flare, and softness near the edges of the frame. Modern cameras often correct these problems digitally using lens profiles.

## Exposure: Aperture, Shutter, and Sensitivity

The amount of light recorded by a camera depends mainly on three controls:

- **Aperture:** Controls the size of the lens opening and affects depth of field.
- **Shutter speed:** Controls how long the sensor collects light and affects motion blur.
- **ISO sensitivity:** Changes how strongly the camera amplifies the sensor signal and affects visible noise.

These controls are often called the exposure triangle, although ISO does not create more light. A higher ISO makes a captured signal brighter, but it also makes the signal's noise more visible and can reduce the usable dynamic range.

A slow shutter can collect more light but may blur moving subjects or camera motion. A fast shutter freezes motion but requires more light or a wider aperture. Automatic exposure systems choose a compromise based on the scene and the selected camera mode.

## The Image Sensor

Most digital cameras use a complementary metal-oxide-semiconductor (CMOS) sensor. The sensor contains a grid of photosites. Each photosite collects charge when photons strike it. More photons produce a stronger electrical signal, so the photosite measures the brightness of a small region of the scene.

A sensor's resolution is the number of photosites across its width and height. More photosites can capture finer detail, but resolution alone does not guarantee a better image. Lens quality, focus accuracy, diffraction, noise, motion, and processing all affect the final result.

Photosites have a limited capacity called the full-well capacity. If too much light fills a photosite, the recorded value clips to white. At the dark end, the signal competes with read noise and thermal noise. The range between the brightest non-clipped signal and the darkest usable signal is the sensor's dynamic range.

Some cameras use a mechanical shutter, an electronic shutter, or both. A rolling electronic shutter reads different sensor rows at slightly different times. Fast motion can therefore appear tilted or distorted. A global shutter exposes and reads all pixels at once, which avoids that particular distortion but is more difficult to implement efficiently.

## Measuring Color

A typical sensor photosite measures the amount of light, not its color. To capture color, many sensors place a color filter array over the photosites. The most common arrangement is the Bayer pattern, which uses red, green, and blue filters. There are usually twice as many green samples because human vision is especially sensitive to luminance detail represented by green information.

The camera must estimate the missing color components for each pixel. This process is called demosaicing. The result is then adjusted for white balance, which compensates for the color of the illumination. A white object should appear white under daylight, warm indoor lighting, or shade even though the incoming light has different spectral properties.

Color is also described relative to a color space. Raw sensor measurements are not directly display-ready, so the image processor maps them into a working space such as sRGB or a wider-gamut space. JPEG images usually contain decisions about white balance, tone, color, and sharpening. Raw files preserve more sensor measurements and defer many of those decisions to later software.

## The Image Signal Processor

The image signal processor, or ISP, turns sensor readings into a usable image. Its work can include:

- Demosaicing color-filter data
- Correcting lens shading and defective pixels
- Reducing noise
- Selecting white balance and color transforms
- Recovering highlight and shadow detail when possible
- Applying tone curves and contrast
- Detecting faces, subjects, and focus regions
- Combining multiple exposures or frames
- Encoding the final image as JPEG, HEIF, or another format

Computational photography extends this process across several frames. A phone may combine exposures for high dynamic range, align frames to reduce noise, estimate depth for portrait blur, or use a learned model to sharpen fine detail. These techniques can produce results that would be difficult to obtain from a single exposure, but they may also create halos, smearing, or invented-looking texture when the input is ambiguous.

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