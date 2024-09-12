# Build with MPLABX Github Actions

TEST

This action will build a MPLAB X project.

It runs on Linux Ubuntu 18.04 and uses:

- MPLAB 5.40
  - Removed Packs not targeting PIC32MX/MZ to reduce image size
- xc32 v2.41
- Peripheral libraries for PIC32

## Inputs

### `project`

**Required** The path to the project to build (relative to the repository). For example: 'firmware.X'.

### `configuration`

The configuration of the project to build. Defaults to `default`.

## Outputs

GH Outputs: None. The finished built files are moved to /github/workspace/output, so they can be used in later steps in the same run.

## Example usage

Add the following `.github/workflows/build.yml` file to your project:

```yaml
name: Build
on: [push]

jobs:
  build:
    name: Build project
    runs-on: ubuntu-latest
    steps:
      - name: Download source
        uses: actions/checkout@v1

      - name: Build library
        uses: FlippievanDyk/ghactions-mplabx@master
        with:
          project: firmware.X
          configuration: default
```

Thanks to

----

[SOUNDBOKS](https://github.com/SOUNDBOKS/ghactions-mplabx-xc32), for many of the changed made vs the original repo.
