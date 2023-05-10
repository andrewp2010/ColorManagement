# LookUp Table (LUT)

Lookup table (LUT): a technique for optimizing the evaluation of functions that are expensive to compute and inexpensive to cache.

You can put many things in LUTs, from [transfer functions](./Glossary.md/#transfer-function) to various [display transform](./Glossary.md/#display-transform) operators.

> **_Note_**: To the best of my understanding LUTs contain many cached [display transforms](./Glossary.md/#display-transform) operators or [transfer functions](./Glossary.md/#transfer-function), therefore, all LUTs are considered [display transforms](./Glossary.md/#display-transform); but individual [display transform](./Glossary.md/#display-transform) operators or [transfer functions](./Glossary.md/#transfer-function) are not considered LUTs, unless cached properly

## LUT Types:

There are two types of LUTs:

- **<u>1D LUT</u>**: affects all RGB channels the same way; they generally contain a [transfer function](./Glossary.md/#transfer-function) or S-curve type function. It allows to display [HDR](./Glossary.md/#high-dynamic-range-image-hdr) images on [SDR](./Glossary.md/#standard-dynamic-range-image-sdr) monitors. May include operators like: brightness, gamma, contrast, color balance.
> **_Note_**: 1D LUTs does not allow you to switch from one [gamut](./Glossary.md/#gamut) to another.

- **3D LUT**: it affects RGB channels differently. This take the shape of a 3x3 matrix.
> **_Note_**: 3D LUTs allows you to switch from one [gamut](./Glossary.md/#gamut) to another.

## Application Tips:

It is crucial that anyone rendering or doing look development use the same LUT. Texturing in a [color space](./Glossary.md/#color-space) but rendering in the same [color space](./Glossary.md/#color-space) with a LUT can give drastic discrepancies. An [OCIO](./Glossary.md/#opencolorio-ocio) configuration is the easiest way to share a LUT between different softwares. See the [OCIO Page](./OCIO.md) for additional information.

"We generally need to test our look development assets under different HDRIs (or lighting conditions) to make sure they react well. Same goes with LUTs. It is not uncommon to work the assets under "neutral" studio LUT and check how it looks under the show LUT." - [Chris Brejon](./WorksCited.md)