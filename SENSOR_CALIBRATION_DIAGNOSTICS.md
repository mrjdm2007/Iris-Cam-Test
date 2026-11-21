# Iris Cam Test — sensor colour research

This repository is based on the successful **Iris Cam workflow #497** from 11 November 2026 (source commit `b1a6c8aec2e0c481bb7661210b3bcea2d0648af3`). The original Iris-Cam repository is not modified by this test project.

## Main-sensor calibration export

1. Install the latest debug APK from the **Build APK** workflow.
2. Select **Main 1x (camera ID 0)**.
3. Open **Tools → Export main sensor calibration report**.
4. Find the timestamped JSON file in `Downloads/IrisCamCalibration/`.
5. Upload it to this repository, preferably under `calibration-reports/`.

Repeat under stable daylight and indoor lighting. The report contains device/camera information, CFA arrangement, sensor dimensions, black/white levels, RAW/manual-sensor capabilities, reference illuminants, Camera2 colour/calibration/forward matrices, and the latest completed main-camera preview capture result (colour correction transform/gains, AWB state, neutral colour point and green split where available).

The report is device-reported Camera2 metadata. It is not a lab spectral sensitivity measurement and does not replace colour-chart validation.

## Inspired looks in this test build

The Inspired group contains only:
- Sony S-Cinetone (inspired)
- Nikon Natural Colour (inspired)
- Panasonic Lumix Cinelike D (inspired)
- ARRI Alexa 35 (inspired)

The Alexa 35 entry is an approximation for an already-rendered phone-camera image, not an official ARRI LogC4-to-Rec.709 transform or an exact camera match. Accurate sensor-specific tuning requires the exported metadata plus controlled reference-chart captures.

## RGB chroma controls

The LOOKS dialog provides independent Red, Green and Blue chroma sliders, each from 0–200%. **100% preserves the selected look's built-in channel trim**; lower or higher values reduce or increase that channel's chroma relative to luma rather than simply changing its brightness. Values persist across app restarts and are applied to preview, saved stills, and video output; video changes update the active renderer live.
