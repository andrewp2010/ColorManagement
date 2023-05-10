# Glossary

> **_Note:_** There are terms in the color management world that have been used incorrectly for years and have become very ambiguous. Those words will be marked with: _(ambiguous)_. I have done my best to define them as they should be.
    
### **Color**:  
> the psychological phenomena of perceiving light via the [Human Perceptual System](#human-perceptual-system). Compared to [chromaticity](#chromaticity), color is the physical stimuli and organic reaction of seeing light. Therefore, color is relative to any given context.

### **Color Space**:
> a model of describing [color](#color) that is defined by three [primaries](#primaries), a [whitepoint](#whitepoint), and [transfer functions](#transfer-function).

### **Chromaticity**:
> a coordinate that defines a mixture of visible light within an absolute [encoding](#encode) model. Compared to [color](#color), chromaticity is the mathematical value of perceived light.

### **CIE 1931 Color Space Model**:
> glues the visible spectrum of laser-like wavelengths to a human oriented concept known as [chromaticity](#chromaticity) in a single, convenient model.

### **CIE 1976 Color Space Model**:
> an attempt to make the 1931 model more [perceptually uniform](#perceptually-uniform), by non-uniformly scaling the [1931 model](#cie-1931-color-space-model).

### **Color Management Workflow**:
> the process of ensuring that consistent accurate [color](#color) is maintained throughout an entire animation pipeline.  
> **_See_**: [Color Management Workflow Page](./CMW.md)

### **Color Swatch/Pot**:
> colors used in a [DCC](#digital-content-creation-dcc) software’s interface, often in the form of a color picker.

### **Digital Content Creation (DCC)**:
> animation pipeline software.

### **Decode**:
> the process of converting [encoded](#encode) data back into its original format. This may involve converting binary data into a human-readable text. Decoding code values gives them context and meaning.

### **Display-Referred Image**:
> code values that have undergone [display transforms](#display-transform) appropriate for a specific output device. 
> **_Note_**: may be referred to as [display-linear](#linear-ambiguous) values, which highlights two important scene-referred encoding attribute: (1) [linear](#linear-ambiguous), (2) [standard dynamic range (SDR)](#standard-dynamic-range-image-sdr).

### **Display Transform**:
> an operation, or operators, that convert image data from scene-referred data to display-referred data. This includes any desired "looks" or color mastering. Also known as tone mapping, display rendering transform, output transform, view transform.  
> **_See_**: [Display Transform Page](#display-transform) for additional clarification.

### **Encode**:
> the process of converting data into a format that can be easily stored, or processed by a computer. This may involve converting data from its original form into a binary format.

### **Gamma _(ambiguous)_**:
> a numerical parameter that describes the [nonlinearity](#nonlinear) of [intensity](#light-intensity) reproduction.  
> **_See_**: [Transfer Functions Page](./TransferFunctions.md)

### **Gamut**:
> a volume, or area in a [color space](#color-space).

### **High Dynamic Range Image (HDR)**:
> a digital image with a value/color range larger than 0.0 to 1.0. It allows for greater detail in both dark and bright areas of the image.  
> **_See_**: [Standard Dynamic Range Image](#standard-dynamic-range-image)

### **Human Perceptual System**:
> the system that enables humans to sense and interpret the world by using their senses and cognitive processes.

### **Light Intensity**:
> the rate of energy from a light (i.e. a light’s brightness).  
> **_See_**: [Light Intensity Page](./OtherTopics/LightIntensity.md)

### **Linear _(ambiguous)_**:
> when an output is directly proportional to an input. In the context of digital [color](#color), it refers to how [radiometric light energy](#radiometric-light-energy) behaves, and how code value inputs and outputs can be described via light energy physics and math (i.e. 1 light + 1 light = 2 light).  
- **Display-Linear**: scene-linear code values that have undergone [display transforms](#display-transform) and are directly proportional to the [radiometric light energy](#radiometric-light-energy) from a given display.
- **Scene-Linear**: code values that reflect the [radiometric light energy](#radiometric-light-energy) of a given scene.
> **_Note_**: Linear is often misunderstood to be a [color space](#color-space) or to mean infinite [gamut](#gamut). This is incorrect. Linear values still exist within a [color space](#color-space) with respective [primaries](#primaries), and should always be described as scene-linear or display-linear.

### **Lookup Table (LUT)**:
> a technique for optimizing the evaluation of functions that are expensive to compute and inexpensive to cache.  
> **_See_** [LUT Page](./LUT.md) for additional clarification.

### **Luminance**:
> the perceptual [intensity](#light-intensity) of color.

### **Nonlinear**:
> when an output is not directly proportional to an input. Humans experience light nonlinearly. That is, we take in [linear](#linear-ambiguous) light but eventually bright is just bright.  
> **_See_**: [linear](#linear-ambiguous)

### **OpenColorIO (OCIO)**:
> an open source framework for configuring and applying color transformations. It has two major design goals: (1) **consistent color transforms**, and (2) **consistent image display**, across multi-application cinematic color pipelines. OCIO color configuration files define all of the conversions that may be used, including [display transforms](./Glossary.md/#display-transform), and has full support for both CPU and GPU pathways. It is designed to run both [scene-referred](./Glossary.md/#scene-referred-image) and [display-referred](./Glossary.md/#display-referred-image) imagery. OCIO does not make any assumptions about the imagery, and all color transformations are "opt in".

### **Perceptual Chromatic Adaptation**:
> when our [perceptual systems](#human-perceptual-system) adapt to a neutral achromatic axis (i.e. white), it shifts, bends, warps, and adjusts every single spectral combination in our field of view. In other words, the entire rest of our [color](#color) sensation will be skewed to that adaptation.  
> **_See_**: [white](#white), [whitepoint](#whitepoint)

### **Perceptual Intensity**:
> the phenomenon where [chromaticity](#chromaticity) with the same coded intensity will still appear to have different intensities.

### **Perceptually Uniform**:
> refers to a means of comparing values with corresponding perceptual differences

### **Primaries**:
> The values for red, green, and blue in a [color space](#color-space) that are derived from a [chromaticity model](#cie-1931-color-space-model). It defines a [color space](#color-space)’s [gamut](#gamut). The color of your display’s primaries will depend on the hardware.

### **Radiant Energy (Radiance)**:
> The physical energy value of light. Only a small sliver of the entire range of radiant energy is called visible light energy.

### **Radiometric Light Energy**:
> the physical energy carried by light, which can be measured and quantified. It is used to study and measure how light behaves in different environments.

### **Radiometrically Uniform**:
> uniform in terms of [radiometric light energy](#radiometric-light-energy).
> **_See_**: [radiometric light energy](#radiometric-light-energy)

### **Scene-Referred Image**:
> code values that represent a scene’s [radiometric light energy](#radiometric-light-energy).  
> **_Note_**: may be referred to as [scene-linear](#linear-ambiguous) values, which highlights two important scene-referred encoding attributes: (1) [linear](#linear-ambiguous), (2) [high dynamic range (HDRI)](#high-dynamic-range-image-hdri).

### **Spectrum Locus**:
> in a [chromaticity diagram](#cie-1931-color-space-model), it is the locus of points that represent monochromatic stimuli. Or, it is the infinitely thin, horseshoe shaped line that  represents all of the colors of the visible spectrum. The numbers around the locus represent the wavelengths of visible light in nanometers. 

### **Standard Dynamic Range Image (SDR)**:
> a standard  digital image with a value/color range from 0.0 to 1.0.  
> **_See_**: [High Dynamic Range Image](#high-dynamic-range-image-hdri)

### **Texture Map**:
> a 2D image applied to the surface of a 3D model to give it increased detail.

### **Transfer Function**:
> a formula that describes how code values relate to light energy inputs or outputs.
- **Electro-optical Transfer Function(EOTF, [decoder](#decode))**: converts the video signal into the [linear](#linear-ambiguous) light output of the display. When you send a signal to the screen for [decoding](#decode).
- **Opto-electronic Transfer Function (OETF, encoder)**: converts [linear](#linear-ambiguous) scene light into the video signal, typically within a camera. When you shoot or scan for [encoding](#encode).
> **_See_**: [Transfer Functions Page](./TransferFunctions.md)

### **White**:
> a mixture of visible lights that our [perceptual system](#human-perceptual-system) has fully adapted to. It can be expressed on the [CIE 1931 chromaticity plot](#cie-1931-color-space-model).  
> **_See_**: [Whitepoint](#whitepoint), [White Page](./ColorSpace.md/#white)

### **Whitepoint**:
> the [chromaticity](#chromaticity) in a [color space](#color-space) that defines [white](#white) to the standard viewer. Any set of [chromaticities](#chromaticity) lying on the neutral axis passing through the whitepoint, will be neutral to that [color space](#color-space). A [color space](#color-space)’s whitepoint is the direct result of a [transfer function](#transfer-function).
> **_See_**: [White Page](./ColorSpace.md/#white)