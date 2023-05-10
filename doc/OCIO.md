# OpenColorIO (OCIO)

**_OpenColorIO (OCIO)_**: an open source framework for configuring and applying color transformations. It has two major design goals: (1) **consistent color transforms**, and (2) **consistent image display**, across multi-application cinematic color pipelines. OCIO color configuration files define all of the conversions that may be used, including [display transforms](./Glossary.md/#display-transform), and has full support for both CPU and GPU pathways. It is designed to run both [scene-referred](./Glossary.md/#scene-referred-image) and [display-referred](./Glossary.md/#display-referred-image) imagery. OCIO does not make any assumptions about the imagery, and all color transformations are "opt in".

An OCIO configuration is the easiest way to share a [LUT](./Glossary.md/#lookup-table-lut) between different programs.

## OCIO Configuration Components:

```
# MINIMAL OCIO CONFIGURATION

ocio_profile_version: 1

search_path: "luts:looks"
strictparsing: true
luma: [0.2126, 0.7152, 0.0722]

description: A filmlike dynamic range encoding

roles:
  default: Linear
  reference: Linear
  scene_linear: Linear
  data: Non-Colour Data
  compositing_log: Filmic Log Encoding
  color_timing: Filmic Log Encoding
  default_byte: sRGB OETF
  default_float: Linear
  default_sequencer: sRGB OETF
  color_picking: sRGB OETF
  texture_paint: sRGB OETF
  matte_paint: Filmic Log Encoding

displays:
  sRGB:
    - !<View> {name: Linear Raw, colorspace: Linear}
    - !<View> {name: sRGB OETF, colorspace: sRGB OETF}
    - !<View> {name: Filmic Base Contrast, colorspace: Filmic Log Encoding, look: Base Contrast}

colorspaces:
  - !<ColorSpace>
    name: Filmic Log Encoding
    family:
    equalitygroup:
    bitdepth: 32f
    description: |
      Log based filmic shaper with 16.5 stops of latitude, and 25 stops of dynamic range.
    isdata: false
    allocation: lg2
    allocationvars: [-12.473931188, 12.526068812]
    from_reference: !<GroupTransform>
        children:
          - !<AllocationTransform> {allocation: lg2, vars: [-12.473931188, 12.526068812]}
          - !<FileTransform> {src: desat65cube.spi3d, interpolation: best}
          - !<AllocationTransform> {allocation: uniform, vars: [0, 0.66]}
    to_reference: !<AllocationTransform> {allocation: lg2, vars: [-12.473931188, 4.026068812], direction: inverse}

looks:
  - !<Look>
    name: Base Contrast
    process_space: Filmic Log Encoding
    transform: !<FileTransform> {src: Filmic_to_0-70_1-03.spi1d, interpolation: linear}
```

- **_Role_**: various software functions (ie: color picking, texture painting, compositing, etc)
- **_Display_**: monitor with its color space characteristics ([primaries](./Glossary.md/#primaries), [whitepoint](./Glossary.md/#whitepoint), [EOTF](./Glossary.md/#transfer-function))
- **_View_**: the [display transform](./Glossary.md/#display-transform) we see the images through (ACES, Raw, Log, etc.)
- **_Look_**: creative preference or grading

## Application Tips:

- **OCIO is NOT implemented the exact same way in all softwares.** With OCIOv2, there is an effort trying to normalize it though. In other words, [DCCs](./Glossary.md/#digital-content-creation-dcc) may use different OCIO roles, or the same roles for different purposes (for example, "reference" and "color_picking" are ambiguous).
- Most [DCC](./Glossary.md/#digital-content-creation-dcc) softwares do not permit interactive "Look Overrides", like a dropdown menu that would let you easily choose them from a list. A workaround is to create multiple views with a different look in each one.
- With OCIOv1, there are some visual differences between the CPU and the GPU processor that may cause you a little bit of headache. This is now fixed in OCIOv2.
