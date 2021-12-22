# Wasm3 packages for OpenWrt

wasm3 is the fastest WebAssembly interpreter.

## Using static [prebuilt binaries](https://github.com/wasm3/wasm3-openwrt-packages/releases/latest)

```sh
$ cd /tmp/
$ wget -O wasm3 https://github.com/wasm3/wasm3-openwrt-packages/releases/download/v0.5.0/wasm3-linux-mipsel-sf
$ chmod a+x wasm3
$ ./wasm3 --version
Wasm3 v0.5.0 on mipsel mips1
Build: Dec 22 2021 15:24:31, GCC 11.2.1 20211120
$ wget -O coremark.wasm https://github.com/wasm3/wasm3/raw/main/test/wasi/coremark/coremark.wasm
$ ./wasm3 coremark.wasm
(wait for results)
```

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
