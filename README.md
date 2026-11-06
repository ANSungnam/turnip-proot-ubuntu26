# turnip-proot-ubuntu26

Builds Mesa Turnip (freedreno Vulkan, KGSL backend) and Zink for **proot Ubuntu 26.04 arm64** on Android (tested target: Adreno 830).

The GitHub Actions workflow runs on an arm64 runner inside an `ubuntu:26.04` container and publishes `turnip-<mesa>-ubuntu26-arm64.tar.gz` as a release asset. It installs to `/opt/turnip`.

## Use

```sh
tar xzf turnip-*-ubuntu26-arm64.tar.gz -C /
export VK_ICD_FILENAMES=/opt/turnip/share/vulkan/icd.d/freedreno_icd.aarch64.json
export LD_LIBRARY_PATH=/opt/turnip/lib/aarch64-linux-gnu
export LIBGL_DRIVERS_PATH=/opt/turnip/lib/aarch64-linux-gnu/dri
export MESA_LOADER_DRIVER_OVERRIDE=zink TU_DEBUG=noconform
glxinfo -B
```
