# Wasm3 packages for OpenWrt

wasm3 is the fastest WebAssembly interpreter.

## Build from source

Before building, please get familiar with [OpenWrt build system](https://openwrt.org/docs/guide-developer/build-system/start) and how to [build OpenWrt packages](https://openwrt.org/docs/guide-developer/build.a.package).

```bash
echo "src-git wasm3 git://github.com/wasm3/wasm3-openwrt-packages.git" >> ./feeds.conf
./scripts/feeds update -a
./scripts/feeds install -p wasm3 -a
make menuconfig
```
Select ```Languages -> WebAssembly -> wasm3```
```
make -j8
```

## Build just wasm3
```
make package/wasm3/compile V=s
```

## Rebuild wasm3
```
make package/wasm3/{clean,compile,install} V=s
```

## Install on device

```
scp ./bin/packages/<your_arch>/wasm3/wasm3_*.ipk root@DEVICE:/tmp
# Then on device:
opkg install /tmp/wasm3_*.ipk
```
