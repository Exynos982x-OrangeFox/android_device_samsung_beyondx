# OrangeFox Recovery device tree for the Samsung Galaxy S10 5G (beyondx)

| Device | Samsung Galaxy S10 5G |
| :-- | :-- |
| Codename | beyondx |
| Models | SM-G977B, SM-G977N |
| SoC | Exynos 9820 |

Common tree: [android_device_samsung_exynos9820-common](https://github.com/Exynos982x-OrangeFox/android_device_samsung_exynos9820-common)

## Kernel

The prebuilt `Image` and `dtbo.img` are extracted from the official LineageOS 23.2 `recovery.img` of
2026-10-21 (sha256 `502caad0dce27645974893712a8528e03fba719e06a2c9e22f97d1ac8dcbfb7e`), built from
[android_kernel_samsung_exynos9820](https://github.com/LineageOS/android_kernel_samsung_exynos9820/tree/a412cfaf86b980ce35cae96a35f678c8ea551575)
with `exynos9820-beyondx_defconfig`.

## Building

```sh
git clone https://gitlab.com/OrangeFox/sync.git
cd sync
./orangefox_sync.sh --branch 12.1 --path ~/fox_12.1

cd ~/fox_12.1
git clone -b fox_12.1 https://github.com/Exynos982x-OrangeFox/android_device_samsung_beyondx device/samsung/beyondx
git clone -b fox_12.1 https://github.com/Exynos982x-OrangeFox/android_device_samsung_exynos9820-common device/samsung/exynos9820-common

export FOX_BUILD_DEVICE=beyondx
source build/envsetup.sh
lunch twrp_beyondx-eng
mka adbd recoveryimage
```

The recovery image is written to `out/target/product/beyondx/`, along with an Odin-flashable `.tar`.
