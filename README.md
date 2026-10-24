# Khalil Ali Professional Camera — Android source (development build)

Native Kotlin / CameraX Android app. **Not a compiled APK; compilation and device validation have not been performed in this environment.**

## Implemented in source (unverified at runtime)
- Real CameraX preview and still JPEG capture; tap-to-focus; pinch-to-zoom; front/rear camera selection; flash mode.
- Exposure-compensation dialog, where hardware supports it.
- Six deterministic non-generative photo looks; default KhalilAli. KhalilAli adds conservative luma shadow/highlight adjustment, microcontrast, chroma refinement, approximate skin-color protection, and edge-limited sharpening. This is **not** RAW development, multi-frame HDR, neural denoising, advanced white balance, or lens calibration.
- MediaStore photo saving, optional original preservation, in-app original/processed toggle comparison of the most recent capture, persistence of look and save-both preference.
- JPEG processing is limited to 8192 px maximum side for memory protection. On higher resolution captures the original is retained if Save Both is on; the processed result may be downsampled.

## Build
1. Open this directory in **Android Studio** with Android SDK 35, JDK 17, and network access for dependency resolution.
2. Sync Gradle project. Android Gradle Plugin 8.7.3, Kotlin 2.0.21, CameraX 1.4.1.
3. Run `gradle :app:assembleDebug` with Gradle 8.9, or use Android Studio **Build > Build APK(s)**. A Gradle Wrapper is **not included**; no Gradle distribution was available locally.
4. Expected output after successful build: `app/build/outputs/apk/debug/app-debug.apk`.
5. Install and validate on a physical phone; camera operation cannot be validated with source inspection alone.

## Known limitations / not implemented
- Not built or tested; APK absent.
- No physical 0.6x/3x/5x selection: current camera supports back/front and digital zoom only. Samsung auxiliary lens access depends on Camera2 exposure/vendor policy.
- No RAW, DNG, HEIF, high-res sensor mode selection, multi-frame HDR, computational night capture, bokeh, optical lens correction, segmentation, or face/eye detection.
- No real-time processed preview; preview shows unprocessed camera feed.
- Compare is a toggle of the latest saved original and processed images, not a draggable slider.
- Processing is single-frame pixel based, not the full pipeline requested. JPEG EXIF is not copied into processed export.
- UI and device quality acceptance tests remain outstanding.

## Privacy
Local photo capture and processing. CAMERA permission only. No account or upload.
