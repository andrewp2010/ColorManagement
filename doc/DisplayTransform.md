# Display Transform

[Display Transform](./Glossary.md/#DispalyTransform): an operation, or operators, that convert image data from [scene-referred](./Glossary.md/#scene-referred-image) data to [display-referred](./Glossary.md/#display-referredoutput-referred-image) data, or vice versa. This includes any additional "looks" or color mastering. Also known as tone mapping, display rendering transform, output transform, view transform, etc.

When tone mapping is discussed, generally it refers to an S-curve operator to help map [HDR](./Glossary.md/#high-dynamic-range-image-hdri) images to [SDR](./Glossary.md/#standard-dynamic-range-image) images. However, this is only one small operator out of several in a general display transform.

## Display Transform Operators

A potentially incomplete list of additional operators:
- **_Input Conversion_**: convert input ([Texture Map](./Glossary.md/#texture-map), [Color Swatch](./Glossary.md/#color-space)) [color space](./Glossary.md/#color-space) into the rendering [color space](./Glossary.md/#color-space).
- **_[Gamut](./Glossary.md/#gamut) Compression/Mapping_**: handling [chromaticities](./Glossary.md/#chromaticity) which lie outside of the target output [gamut](./Glossary.md/#gamut).
> **_NOTE_**: in digital RGB land, the path-to-white must be engineered. Values do not magically go to white on a digital monitor. They can "only reach" 100% emission on R, G, and B channels; therefore, data compression/mapping is often necessary.
- **_[Whitepoint](./Glossary.md/#whitepoint)_**: creatively change the [whitepoint](./Glossary.md/#whitepoint) in order to create a warmer or cooler image regardless of what display device [whitepoint](./Glossary.md/#whitepoint) we are outputting to.
- **_Display Gamut Conversion_**: convert from a rendering [color space](./Glossary.md/#color-space) to a display [color space](./Glossary.md/#color-space).
- **_Inverse [EOTF](./Glossary.md/#transfer-function)_**: the display's [electro-optical transfer inverse](./Glossary.md/#transfer-function) to apply to image data before emitting light from the display.
- **_Clamp_**: clamping the [scene-referred image](./Glossary.md/#scene-referred-encoding) into [SDR](./Glossary.md/#standard-dynamic-range-image) data, to simulate what is going to happen when we write the image out into an integer data format.

> **_NOTE_**: For optimization reasons, many display transform operators are often baked into a [LUT](./Glossary.md/#lookup-table-lut). See [LUT Page](./LUT.md) for more information.

## What happens if you do not use a Display Transform?

Your shot will be overexposed, and you will have to manually compensate for it. Without a display transform, you will never get the right amount of energy in your scene; consequently, you will loose some bouncing from Global Illumination, and Sub-Surface Scattering (among other things).