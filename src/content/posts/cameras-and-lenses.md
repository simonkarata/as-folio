---
title: 'Cameras and Lenses'
description: How light, optics, and exposure work together to turn a scene into an image
date: 2024-02-14
author: simon
draft: false
tags:
  - cameras
  - optics
  - physics
  - photography
  - imaging
---
---

A camera is, at its core, a controlled light-measuring device. It captures the light coming from a scene and records it on a sensor or film so it can be preserved, reproduced, and viewed later. The basic idea is simple, but the physics behind it is subtle: light travels in straight lines, changes direction when it passes through transparent materials, and can be focused by curved surfaces so that an image of the world is formed at a specific plane.

The most important element is the lens. A lens is made of glass or plastic shaped so that light rays entering at different angles are bent toward a common point. In a simple convex lens, rays from a distant object are refracted as they pass through the curved surfaces and converge on the sensor plane. This convergence creates an image: each point in the scene corresponds to a point on the sensor, with brightness determined by how much light reaches it and sharpness determined by how precisely the rays come together.

The key optical quantity is focal length. A lens with a shorter focal length bends light more strongly and produces a wider field of view, so it captures more of the scene. A longer focal length bends the rays less aggressively and narrows the field of view, making distant subjects appear larger. This is why a wide-angle lens feels like it stretches the scene and a telephoto lens compresses the apparent distance between objects. The physics behind this is the geometry of refraction and the relationship between object distance, image distance, and focal length, captured by the thin-lens equation.

The lens also controls exposure through its aperture. The aperture is a variable opening that determines how much light reaches the sensor. A larger opening, such as f/1.8, admits more light and allows shorter exposures or better performance in low light. A smaller opening, such as f/11, admits less light and increases depth of field, meaning more of the scene stays in focus. This happens because a wider aperture produces a larger cone of light rays, which makes focusing more sensitive to object distance, while a smaller aperture reduces that sensitivity.

The shutter and sensor complete the process. The shutter acts like a timed gate, allowing light through for a precise duration. The sensor then converts the incoming photons into electrical signals, which are sampled and processed into a digital image. In a digital camera, each pixel measures the intensity of light falling on it, and color is reconstructed by filtering the light into red, green, and blue channels. The final image is therefore a map of brightness and color produced from the incoming light field that the lens has gathered and focused.

There is an elegant tradeoff at the heart of camera design. A larger sensor can collect more light and usually gives better image quality, especially in low light and at high ISO settings. A larger aperture can gather more light and blur the background more strongly, which is often used artistically. A smaller aperture can increase sharpness across more of the frame, but it also demands more light or longer exposure. In every case, the camera is not creating light; it is organizing and recording the light that already exists in the scene.

Understanding cameras and lenses is really understanding light itself. The lens shapes the path of photons, the aperture governs how much of that light is admitted, the shutter decides how long it is allowed to act, and the sensor turns that physical signal into a digital representation. The result is an image that is not a perfect copy of reality but a carefully engineered reconstruction of it, shaped by geometry, optics, and timing.

## Photography
Photography transformed the way people record, remember, and understand the world. From its earliest beginnings in the 19th century, the medium moved from a scientific experiment to a powerful artistic and documentary practice. Its development changed not only how images were made, but also how societies experienced time, memory, and truth.

The invention of the camera obscura and later the daguerreotype made it possible to capture a moment with unprecedented accuracy. Early photographers explored portraiture, landscapes, and urban scenes, while also documenting wars, labor, and everyday life. Photography quickly became a tool for both artistic expression and social observation.

In the 20th century, photography expanded through new technologies such as film, color processing, and portable cameras. Movements like documentary photography, photojournalism, and street photography brought the medium into public debate, revealing social realities and shaping modern visual culture. Artists also used photography to challenge ideas of authorship, identity, and representation.

Today, photography continues to evolve through digital imaging, smartphones, and global online networks. It remains central to journalism, science, advertising, and personal memory, while also opening new questions about authenticity, surveillance, and the role of images in contemporary life.

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