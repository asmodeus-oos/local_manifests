# Local Manifests for Realme GT 2 Pro (ferrari / RMX3301) — Evolution X 12.3

Local manifests and setup instructions for building Evolution X 12.3 (Android 17) on Realme GT 2 Pro (SM8450).

## Setup & Build

```bash
# 1. Initialize Evolution X source tree
repo init -u https://github.com/Evolution-X/manifest -b cnb --git-lfs

# 2. Clone local manifest into .repo/local_manifests
git clone https://github.com/asmodeus-oos/local_manifests.git -b 17.0 .repo/local_manifests

# 3. Sync all sources
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags

# 4. Apply device patches to upstream repos
bash device/realme/ferrari/patches/apply-patches.sh

# 5. Build
source build/envsetup.sh
lunch lineage_ferrari-ap4a-userdebug
mka bacon
```

## Repositories Included in Manifest

| Component | Target Path | Host / Repository | Branch |
|---|---|---|---|
| Device Tree (ferrari) | `device/realme/ferrari` | GitHub: `asmodeus-oos/android_device_realme_ferrari` | `17.0` |
| Device Common (sm8450) | `device/oneplus/sm8450-common` | GitHub: `asmodeus-oos/android_device_oneplus_sm8450-common` | `17.0` |
| Hardware HAL | `hardware/oplus` | GitHub: `asmodeus-oos/android_hardware_oplus` | `17.0` |
| Kernel Source | `kernel/oneplus/sm8450` | GitHub: `asmodeus-oos/android_kernel_oneplus_sm8450` | `17.0` |
| Kernel Devicetrees | `kernel/oneplus/sm8450-devicetrees` | GitHub: `asmodeus-oos/android_kernel_oneplus_sm8450-devicetrees` | `17.0` |
| Kernel Modules | `kernel/oneplus/sm8450-modules` | GitHub: `asmodeus-oos/android_kernel_oneplus_sm8450-modules` | `17.0` |
| Display HAL (sm8450) | `hardware/qcom-caf/sm8450/display` | GitHub: `asmodeus-oos/android_hardware_qcom_display` | `17.0-caf-sm8450` |
| Display HAL (sm8450-6.6) | `hardware/qcom-caf/sm8450-6.6/display/hal` | GitHub: `asmodeus-oos/android_hardware_qcom_display` | `17.0-caf-sm8450-6.6` |
| Audio Primary (sm8450) | `hardware/qcom-caf/sm8450/audio/primary-hal` | GitHub: `asmodeus-oos/android_hardware_qcom_audio-ar` | `17.0-caf-sm8450` |
| Audio Primary (sm8450-6.6) | `hardware/qcom-caf/sm8450-6.6/audio/primary-hal` | GitHub: `asmodeus-oos/android_hardware_qcom_audio-ar` | `17.0-caf-sm8450-6.6` |
| Audio AGM (sm8450) | `hardware/qcom-caf/sm8450/audio/agm` | GitHub: `asmodeus-oos/android_vendor_qcom_opensource_agm` | `17.0-caf-sm8450` |
| Audio AGM (sm8450-6.6) | `hardware/qcom-caf/sm8450-6.6/audio/agm` | GitHub: `asmodeus-oos/android_vendor_qcom_opensource_agm` | `17.0-caf-sm8450-6.6` |
| Audio PAL (sm8450) | `hardware/qcom-caf/sm8450/audio/pal` | GitHub: `asmodeus-oos/android_vendor_qcom_opensource_arpal-lx` | `17.0-caf-sm8450` |
| Audio PAL (sm8450-6.6) | `hardware/qcom-caf/sm8450-6.6/audio/pal` | GitHub: `asmodeus-oos/android_vendor_qcom_opensource_arpal-lx` | `17.0-caf-sm8450-6.6` |
| Thermal HAL | `hardware/qcom-caf/thermal` | GitHub: `asmodeus-oos/android_hardware_qcom_thermal` | `17.0` |
| Vendor (ferrari) | `vendor/realme/ferrari` | GitLab: `asmodeus-oos/proprietary_vendor_realme_ferrari` | `17.0` |
| Vendor Common (sm8450) | `vendor/oneplus/sm8450-common` | GitLab: `asmodeus-oos/proprietary_vendor_oneplus_sm8450-common` | `17.0` |

> Note: Evolution X ROM repositories (`frameworks/base`, `frameworks/av`, `frameworks/native`, `frameworks/libs/systemui`, `packages/apps/Evolver`, `packages/apps/Settings`, `vendor/lineage`, `hardware/lineage/compat`) are tracked directly from upstream and patched via `bash device/realme/ferrari/patches/apply-patches.sh`.
