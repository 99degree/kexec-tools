# fork of kexec-tool

## how to compile static kexec
refer to https://gist.github.com/Gnurou/7191098

compile ad arm64 binary

./bootstrap

LDFLAGS=-static ./configure --host=aarch64-linux-gnu --without-zlib --without-lzma

make

## put build/sbin/kexec it into ramdisk then issue below to kexec boot:

adb push Image.gz dtb ramdisk.img.gz /tmp

adb shell

kexec -s Image.gz --dtb dtb --ramdisk ramdisk.img.gz --reuse-cmdline

kexec -e

done reboot
