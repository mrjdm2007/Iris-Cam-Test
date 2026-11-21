# Iris Cam sensor calibration diagnostics

This test build includes a one-tap Camera2 metadata export for the rear main camera.

## Export from the phone

1. Install the debug APK produced by the repository's **Build APK** workflow.
2. Open Iris Cam and select **Main 1x (camera ID 0)**.
3. Open **Tools**.
4. Choose **Export main sensor calibration report**.
5. Find the JSON report in **Downloads/IrisCamCalibration/**.
6. Upload the JSON file to this repository, preferably under `calibration-reports/`.

Repeat the export under different stable lighting conditions (for example daylight and indoor lighting). Each export is timestamped and stored as a separate JSON file.

## What is collected

- Device/build information and camera ID.
- Sensor geometry, CFA arrangement, RAW/manual-sensor capability, black/white levels and exposure/sensitivity ranges.
- Camera2 colour, calibration and forward matrices for both reference illuminants, when the device exposes them.
- Latest completed main-camera preview capture result: applied colour-correction transform and gains, AWB mode/state, neutral colour point, exposure, ISO, dynamic black/white levels and Bayer green-split estimate, when available.

## Important limitations

This is a metadata report, not a lab measurement of spectral sensitivity and not a colour-chart measurement. Optional Camera2 keys may legitimately be absent or null. The live result is a snapshot of the latest completed preview frame, so repeat exports under different lighting to collect different AWB/neutral-point conditions.

The report does not change camera settings, apply colour correction, or upload anything automatically. The user chooses when and where to upload the JSON file.
