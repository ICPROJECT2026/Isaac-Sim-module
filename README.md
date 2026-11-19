# Upper Assembly URDF Model

## Overview

This repository contains a URDF description of a robot assembly named
`upper_assembly`.

The URDF defines the model's links, joints, visual geometry, collision geometry,
and inertial properties. It can be used as the robot-description input for
software that supports the URDF format.

## Model Structure

The robot description contains six links:

- `base_link`
- `lift_link`
- `arm1_link`
- `arm2_link`
- `extension_link`
- `rack_link`

It also defines five joints:

| Joint | Type | Parent link | Child link |
|---|---|---|---|
| `lift_slide` | Prismatic | `base_link` | `lift_link` |
| `shoulder_yaw` | Revolute | `lift_link` | `arm1_link` |
| `elbow_yaw` | Revolute | `arm1_link` | `arm2_link` |
| `arm_extension` | Prismatic | `arm2_link` | `extension_link` |
| `tool_rack_slide` | Prismatic | `extension_link` | `rack_link` |

The file includes joint axes and limits, as well as inertial, visual, and
collision descriptions for the links.

## Repository Contents

```text
.
├── upper_assembly.urdf
└── meshes/
    ├── *.obj
    └── ...
```

**Important:** The URDF references geometry files using relative paths such as
`./meshes/rack_link_visual.obj`. The referenced mesh files must be placed in a
`meshes` directory next to the URDF file, preserving their filenames and
relative paths. Uploading the URDF alone does not include those mesh assets, so
a viewer may not be able to display the complete model until the meshes are
also provided.

## Usage

1. Download or clone this repository.
2. Keep `upper_assembly.urdf` and the `meshes/` directory in the same project
   directory.
3. Open or import the URDF in a URDF-compatible robotics tool.
4. If the visual or collision geometry is missing, check that every referenced
   mesh file exists at the relative path specified in the URDF.

## File Format

- **URDF** — Unified Robot Description Format, an XML-based format for describing
  robot models.

## Notes

- This repository documents the model structure described in the supplied URDF.
- Joint motion, simulation behavior, and appearance depend on the software and
  assets used to load the model.
- Mesh assets are separate files and should be committed to the repository if
  the model is intended to be viewed or simulated by others.
