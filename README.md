# Realme GT2 Pro (ferrari / RMX3301) — LineageOS 23.3

Local manifests and build instructions for the Realme GT2 Pro (SM8450 / Snapdragon 8 Gen 1).

## Quick Setup

```bash
# 1. Initialize LineageOS 23.3 source
repo init -u https://github.com/LineageOS/android.git -b lineage-23.3 --git-lfs

# 2. Clone this manifest repo
git clone https://github.com/asmodeus-oos/local_manifests.git .repo/local_manifests

# 3. Sync all sources
repo sync -c -j$(nproc --all) --force-sync

# 4. Apply device patches (UDFPS fixes, AGM audio, display HAL)
bash device/realme/ferrari/patches/apply-patches.sh

# 5. Build
source build/envsetup.sh
lunch lineage_ferrari-ap4a-userdebug
mka bacon
```

## What patches are applied

The `apply-patches.sh` script applies the following patches **idempotently** (safe to run multiple times):

### frameworks/base (3 patches)
| Patch | Purpose |
|---|---|
| `0001` | UDFPS overlay cleanup — prevents SystemUI crashes during lock/unlock transitions |
| `0002` | Show UDFPS dim layer during AOD — fixes full-screen HBM flash on AOD fingerprint press |
| `0003` | Near-black dim during AOD UDFPS — uses calibrated alpha for AOD panel luminance |

### hardware/qcom-caf/sm8450/audio/agm + sm8450-6.6/audio/agm (1 patch each)
| Patch | Purpose |
|---|---|
| `0001` | AGM: Support sku-agnostic ACDB ODM path |

### hardware/qcom-caf/sm8450/display (3 patches)
| Patch | Purpose |
|---|---|
| `0001` | SDM: Support Samsung FINGERPRINT_MASK DRM property |
| `0002` | SDM: Operate FINGERPRINT_MASK for oplus optical UDFPS |
| `0003` | SDM: Support pixelworks soft iris color calibration |

## Repositories

| Repository | Branch | Host |
|---|---|---|
| `device/realme/ferrari` | `lineage-23.3` | GitHub |
| `device/oneplus/sm8450-common` | `lineage-23.3` | GitHub |
| `hardware/oplus` | `lineage-23.3` | GitHub |
| `kernel/oneplus/sm8450` | `lineage-23.3` | GitHub |
| `kernel/oneplus/sm8450-devicetrees` | `lineage-23.3` | GitHub |
| `kernel/oneplus/sm8450-modules` | `lineage-23.3` | GitHub |
| `vendor/realme/ferrari` | `lineage-23.2` | GitLab |
| `vendor/oneplus/sm8450-common` | `lineage-23.2` | GitLab |
