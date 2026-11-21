# Iris Cam Test — sensor colour research

This repository is based on the successful **Iris Cam workflow #497** from 11 November 2026 (source commit `b1a6c8aec2e0c481bb7661210b3bcea2d0648af3`). The original Iris-Cam repository is not modified by this test project.

## Per-lens Camera2 metadata export

1. Install the latest debug APK from the **Build APK** workflow.
2. Select **Main 1x (camera ID 0)**, keep the preview on a steady, evenly lit scene for 10–15 seconds, then open **Tools → Export selected lens calibration report**.
3. Repeat for **Wide 0.7x (camera ID 2)** and **Tele 2.7x (camera ID 3)**. Export only after each lens has been selected and its preview has settled.
4. Find the three timestamped JSON files in `Downloads/IrisCamCalibration/`. Each filename includes the selected lens label and camera ID.
5. Upload all three JSON files together, preferably under `calibration-reports/`.

Keep the phone pointed at the same stationary scene and avoid changing the lighting between exports. The wait is to allow preview capture metadata to settle; it is not a physical colour measurement. Each report contains the selected camera's device-reported sensor dimensions, CFA arrangement, black/white levels, RAW/manual-sensor capabilities, reference illuminants, Camera2 colour/calibration/forward matrices, and latest completed capture result (colour correction transform/gains, AWB state, neutral colour point and green split where available).

The capture-result section is populated only after that camera has produced a completed preview result in the current app session. Missing optional keys are reported as `null`. The report is device-reported Camera2 metadata, not a lab spectral sensitivity measurement. A later validation stage needs RAW/DNG captures of the same known colour chart under controlled lighting.

## Inspired looks in this test build

The Inspired group contains only:
- Sony S-Cinetone (inspired)
- Nikon Natural Colour (inspired)
- Panasonic Lumix Cinelike D (inspired)
- ARRI Alexa 35 (inspired)

The Alexa 35 entry is an approximation for an already-rendered phone-camera image, not an official ARRI LogC4-to-Rec.709 transform or an exact camera match. Accurate sensor-specific tuning requires the exported metadata plus controlled reference-chart captures.

## RGB chroma controls

The LOOKS dialog provides independent Red, Green and Blue chroma sliders, each from 0–200%. **100% preserves the selected look's built-in channel trim**; lower or higher values reduce or increase that channel's chroma relative to luma rather than simply changing its brightness. Values persist across app restarts and are applied to preview, saved stills, and video output; video changes update the active renderer live.
