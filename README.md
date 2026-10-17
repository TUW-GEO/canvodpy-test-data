<!-- Python & Package Manager -->
[![Python](https://img.shields.io/badge/python-3.14-blue.svg)](https://www.python.org/)
[![uv](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/uv/main/assets/badge/v0.json)](https://github.com/astral-sh/uv)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-%23FE5196?logo=conventionalcommits&logoColor=white)](https://conventionalcommits.org)

<!-- Identity -->
[![canVODpy](https://img.shields.io/badge/canVODpy-test--data-2d6a4f)](https://github.com/nfb2021/canvodpy)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19708759.svg)](https://doi.org/10.5281/zenodo.19708759)
[![CLIMERS @ TU Wien](https://img.shields.io/badge/CLIMERS-TU_Wien-006699)](https://www.tuwien.at/en/mg/geo/climers)
[![VODnet](https://img.shields.io/badge/-VODnet-2d6a4f?labelColor=555555&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAAAAXNSR0IArs4c6QAAAHhlWElmTU0AKgAAAAgABAEaAAUAAAABAAAAPgEbAAUAAAABAAAARgEoAAMAAAABAAIAAIdpAAQAAAABAAAATgAAAAAAAABIAAAAAQAAAEgAAAABAAOgAQADAAAAAQABAACgAgAEAAAAAQAAAA6gAwAEAAAAAQAAAA4AAAAAjn8NzQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAflJREFUKBWtUEtoE1EUPe+9SczHiam/aixtqi1E7aai4kK0CAVBDFZwrQs3xp2KIriYtiKuav3QRVxYKIjFVihWrCBIaaWioKidQBsxi3SwYmMmkxidYWaemYEEKUgRPHDhXu4575x3gf+NKfVD3UQ2u/Zv7wrLF8mPfV2ZH1ZCNIM7xUCAHHjyfN6wQ8mZo3vvE4Av57tzOjfd/WZpivfJSW5wkzvomnzFe2SFTyyU+iFJtCpk1eaRfOIw84TuRsN7kEkVMDzyEjPvUtga2YiDTRFM5+m+F8XYHMZuzDqaWlQf8yVMpmJ0/DUu9g6hVNQAy8au3W04NHAV85oFRulZS+LDkIjtWmcyHT6vQHYoXwrouTWKkv4LLOAHE4N4K6dxZ2AISl4DpawVDVrYcXSFZtTPGSV8IatjUVErJ+Cwbdstx3Vw8CG+pmQIHg+HUVlWo7aSp/qz9Kn3W5p5S/x4DJ8/lfGt4kAow7bmBpQ9fuQ3RUFtM4Uz61Qk/vijbpLbgtc61n05zjQ1hCvXHmB9fT3OnT8NOWfi+uxP0IJxE4S4jrXzxrffm1xlb75Aud/cEFmD9vYW6KaNUoUmCpS3BblUPNk45sR0UBM6Qzx2qd9LVnfqujGS+64puaX8olEuj4uMHHnc2dTrcFZGtCOMxv11KxP/kfEbTTzNcyb5ar0AAAAASUVORK5CYII=&logoColor=white)](https://vodnet.netlify.app)

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/nfb2021/canvodpy/main/docs/assets/logo/canvodpy_logo_dark_mode.svg">
    <img alt="canVODpy logo" src="https://raw.githubusercontent.com/nfb2021/canvodpy/main/docs/assets/logo/canvodpy_logo_bright_mode.svg" width="312">
  </picture>
</p>

# canVODpy Test Data

Real GNSS observations for testing [canVODpy](https://github.com/nfb2021/canvodpy)
and running its [demo notebooks](https://github.com/nfb2021/canvodpy-demo):
pairs of receivers, one below the canopy and one with an open view of the
sky, from four sites and in five file formats, together with the orbit and
clock products needed to process them.

## Sites

| Site | Location | Receivers (station codes) | Formats | Period |
| ---- | -------- | ------------------------- | ------- | ------ |
| Rosalia | Rosalia Research Forest, Austria | `ROSR01TUW` reference, `ROSA01TUW` canopy | RINEX v3.04, SBF, NMEA | 2025-01-01, 96 files of 15 min at 5 s |
| MOFLUX | Missouri Ozark site, Missouri, US | `MOZR01CAL` reference, `MOZA01CAL` canopy | RINEX v2.11 | 2025-01-01, 24 files of 1 h at 15 s |
| Hainich | Hainich National Park, Germany | `HAIR02MPI` reference, `HAIA02MPI` canopy | NMEA (u-blox NEO-M9N) | 2026-01-01, 1 file of 1 h at 1 s |
| ExampleSite | an MPI-BGC field site (name withheld) | `EXPR01MPI` reference, `EXPA01MPI` canopy | stripped RINEX v3.05 | 2025-01-01, 1 file per receiver |

Rosalia also has the RINEX v3.04 navigation files of both receivers
(2025-01-01, 96 files each).

## Use

canVODpy includes this repository as a git submodule at
`packages/canvod-readers/tests/test_data/`:

```bash
git clone --recurse-submodules https://github.com/nfb2021/canvodpy.git
```

The demo notebooks don't read this repository directly. On first use they
download zips built from it, which are stored in the Hugging Face dataset
[`nfb2021/canvodpy-demo-data`](https://huggingface.co/datasets/nfb2021/canvodpy-demo-data),
and cache them locally.

## File names

The observation files follow the
[canVOD filename convention](https://canvodpy.eu/packages/naming/overview/),
for example:

```text
ROSA01TUW_R_20250010015_15M_05S_AA.rnx
```

| Part | Meaning |
| ---- | ------- |
| `ROS` | site |
| `A` | receiver type: `A` below the canopy, `R` reference |
| `01` | receiver number |
| `TUW` | data provider |
| `R` | receiver-generated data |
| `2025001` | year and day of year |
| `0015` | start time (GPS time) |
| `15M` | file period |
| `05S` | sampling interval |
| `AA` | content code |
| `rnx` | file type: `rnx`, `sbf` or `nmea` |

The navigation files keep their RINEX short names (`rref001a00.25p`,
`ract001a00.25p`).

## Structure

```text
valid/
├── rinex_v3_04/01_Rosalia/
│   ├── 01_reference/01_GNSS/01_raw/25001/   # 96 files ROSR01TUW_*.rnx
│   ├── 02_canopy/01_GNSS/01_raw/25001/      # 96 files ROSA01TUW_*.rnx
│   ├── 01_SP3/                              # orbits of 2025-001
│   └── 02_CLK/                              # clocks of 2025-001
├── rinex_v3_04_nav_data/
│   ├── 01_reference/                        # 96 files rref001*.25p
│   └── 02_canopy/                           # 96 files ract001*.25p
├── rinex_v2_11/02_Moflux/
│   ├── 01_reference/25001/                  # 24 files MOZR01CAL_*.rnx
│   └── 02_canopy/25001/                     # 24 files MOZA01CAL_*.rnx
├── sbf/01_Rosalia/
│   ├── 01_reference/25001/                  # 96 files ROSR01TUW_*.sbf
│   └── 02_canopy/25001/                     # 96 files ROSA01TUW_*.sbf
├── nmea/
│   ├── 01_Rosalia/
│   │   ├── 01_reference/                    # 96 files ROSR01TUW_*.nmea
│   │   └── 02_canopy/                       # 96 files ROSA01TUW_*.nmea
│   └── 02_Hainich/
│       ├── 01_reference/                    # HAIR02MPI_*.nmea
│       └── 02_canopy/                       # HAIA02MPI_*.nmea
├── rinex_v3_05_stripped/01_ExampleSite/
│   ├── 01_reference/25001/                  # EXPR01MPI_*.rnx
│   └── 01_canopy/25001/                     # EXPA01MPI_*.rnx
├── broadcast_ephemerides/02_canopy/         # empty
├── aux_data/
│   ├── 01_SP3/                              # orbits, 2024-366 to 2025-002
│   ├── 02_CLK/                              # clocks, 2024-366 to 2025-002
│   └── aux_2025001.zarr/                    # orbits and clocks of 2025-001 on a 5 s grid
└── run_history/
    └── run_history.sqlite                   # anonymized run history for the run dashboard
invalid/                                     # 36 malformed RINEX v3 files
```

## Run history

`valid/run_history/` is a log folder with the run history of nine
canVODpy runs: the same seven days of two receivers, processed with 1 to
126 worker processes, one run per worker count, plus a warm-up run whose
orbit download failed for three days. `canvodpy dashboard --logs-dir
valid/run_history` opens it in the run dashboard; canVODpy's dashboard
tests and demo notebook use it.

It is anonymized: the person, institution, funding and site are the
test persona of `canvod.utils.testing` (site Fangorn), the machine is an
example machine (no real CPU, core counts, memory, operating system,
host name or process ids), the paths start at `/data/example`, and the
file index is empty. The timings, results, problems and the changes of
CPU, memory and free disk during the runs are kept. canVODpy's
`scripts/anonymize_run_history.py` wrote it.

## Orbits and clocks

Final products of the Center for Orbit Determination in Europe (CODE) for
2025-01-01 and the days before and after it. canVODpy joins each day's
orbits and clocks with those of the neighboring days, so the whole day is
interpolated, never extrapolated.

| Files | Product | Interval |
| ----- | ------- | -------- |
| `COD0MGXFIN_{2024366,2025001,2025002}0000_01D_05M_ORB.SP3` | multi-GNSS orbits | 5 min |
| `COD0MGXFIN_{2024366,2025001,2025002}0000_01D_30S_CLK.CLK` | satellite clocks | 30 s |

`aux_2025001.zarr` holds the orbits (`X`, `Y`, `Z`, `Vx`, `Vy`, `Vz`) and
clock offsets (`clock_offset`, in seconds) of 2025-01-01 on the 5 s grid of
the Rosalia observations, as `canvodpy run` computes them from the three
days above (`canvod.auxiliary.interpolation.interpolate_aux_day`).

## Stripped RINEX v3.05

The ExampleSite files hold signal-to-noise ratios only: every observation
type in their `SYS / # / OBS TYPES` records starts with `S`, and the
pseudorange, carrier phase and Doppler observations are left out. canVODpy
reads them with `canvod.readers.rinex.v3_05_stripped.Rnxv3StrippedObs`,
which refuses a file with any other observation type
(`StrippedRinexError`).

## Malformed files

`invalid/` holds 36 RINEX v3 observation files, each broken in one way:
truncated, corrupted, structurally wrong, wrongly encoded, or with rare
content such as leap seconds and event epochs. canVODpy's reader tests use
them to check that each one fails with a clear error
(`packages/canvod-readers/tests/test_rinex_corruption.py`).

## Data providers

| Contributor | Affiliation | Data |
| ----------- | ----------- | ---- |
| Nicolas François Bader | CLIMERS, TU Wien | Rosalia RINEX v3.04, SBF, NMEA |
| Wouter Dorigo | CLIMERS, TU Wien | Rosalia RINEX v3.04, SBF, NMEA |
| Eugenio Diaz-Pines | Forest Demonstration Centre, BOKU University; Institute of Soil Research, BOKU University | Head of Rosalia Research Forest |
| Konstantin Schellenberg | FSU Jena / MPI-BGC | Hainich NMEA; stripped RINEX v3.05 (ExampleSite) |
| Vincent Humphrey | MeteoSwiss | MOFLUX RINEX v2.11 |
| Christian Frankenberg | Caltech | MOFLUX RINEX v2.11 |

## Citation

The dataset is published on Zenodo:
[doi:10.5281/zenodo.19708759](https://doi.org/10.5281/zenodo.19708759).
Citation metadata are in [`CITATION.cff`](CITATION.cff).

## License

[Apache License 2.0](LICENSE)

## Affiliation

[Climate and Environmental Remote Sensing Research Unit (CLIMERS)](https://www.tuwien.at/en/mg/geo/climers)
Department of Geodesy and Geoinformation, TU Wien
