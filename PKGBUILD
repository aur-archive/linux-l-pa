# Maintainer:  Jordan Johnston <triplesquarednine@gmail.com>
# Contributor: Joakim Hernberg <jbh@alchemy.lu>
# Contributor: Ray Rashif <schiv@archlinux.org>
# Contributor: timbosa <tinny_tim@dodo.com.au>
# Contributor: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Thomas Baechler <thomas@archlinux.org>

#pkgbase=linux               # Build stock -ARCH kernel
pkgbase=linux-l-pa             # Build kernel with a different name
_srcname=linux-3.18
_pkgver=3.18.11
_rtpatchver=rt7
pkgver=${_pkgver}_${_rtpatchver}
pkgrel=1
arch=('i686' 'x86_64')
url="http://www.kernel.org/"
license=('GPL2')
makedepends=('xmlto' 'docbook-xsl' 'kmod' 'inetutils' 'bc')
_bfqver="BFQ-v7r7"
_bfqpath="https://pf.natalenko.name/mirrors/bfq/3.18.0-v7r7/"
options=('!strip')
source=("https://www.kernel.org/pub/linux/kernel/v3.x/${_srcname}.tar.xz"
        "https://www.kernel.org/pub/linux/kernel/v3.x/${_srcname}.tar.sign"
        "https://www.kernel.org/pub/linux/kernel/v3.x/patch-${_pkgver}.xz"
        "https://www.kernel.org/pub/linux/kernel/v3.x/patch-${_pkgver}.sign"
        "https://www.kernel.org/pub/linux/kernel/projects/rt/3.18/older/patch-${_pkgver}-${_rtpatchver}.patch.xz"
        "https://www.kernel.org/pub/linux/kernel/projects/rt/3.18/older/patch-${_pkgver}-${_rtpatchver}.patch.sign"
        # the main kernel config files
        'config' 'config.x86_64'
        # standard config files for mkinitcpio ramdisk
        'linux-l-pa.preset'
        'change-default-console-loglevel.patch'
        'fix-race-in-PRT-wait-for-completion-simple-wait-code_Nvidia-RT.patch'
        # <[UKSM support--]>
        'uksm-0.1.2.3-for-v3.18.patch'
        # <[--Compiler Optimization patches--]>
        'http://repo-ck.com/source/gcc_patch/enable_additional_cpu_optimizations_for_gcc_v4.9+_kernel_v3.15+.patch.gz'
        'custom-flags-kernel.patch'
        # <[--Increase mm vmMax_readahed--]>
        'mm_vmMax_readahead.patch'
        # <[--BFQ - I/O scheduler--] >
        "${_bfqpath}/0001-block-cgroups-kconfig-build-bits-for-${_bfqver}-3.18.patch"
        "${_bfqpath}/0002-block-introduce-the-${_bfqver}-I-O-sched-for-3.18.patch"
        "${_bfqpath}/0003-block-bfq-add-Early-Queue-Merge-EQM-to-${_bfqver}-for-3.18.0.patch"
        # <[--Realtime Linux Patches--]>
        "https://www.kernel.org/pub/linux/kernel/projects/rt/${_basekernel}/patch-${_pkgver}-${_rtpatchver}.patch.xz"
        # <[--Out-of-tree RT patches--]>
        'softirq-resurrect-threads.patch'
        'drivers-serial-call-flush_to_ldisc-when-the-irq-is-t.patch'
        # <[--Lower posix-cpu-timer kthreads to 98--]>
        'posix-cpu-timers_kthreads98.patch')

sha256sums=('becc413cc9e6d7f5cc52a3ce66d65c3725bc1d1cc1001f4ce6c32b69eb188cbd'
            'SKIP'
            'e4c44f887f507b2470a5c2f1c286a38fec6e84c4d433c929981abab7b83f80d5'
            'SKIP'
            '4d5cf3c1a3660ad1376090fa5916aae38cf5fd8b240e47bde5ec969944edd1b6'
            'SKIP'
            '4b584754f0836f9650cb9764baba1323e40a1eac1c12b4ece8f78b2f754029e7'
            '3fc131789c9814d84aa7ba1be3ea132df788c79fa3c689385eb1158159dba635'
            '227e97e8b39384f7e5f3e6501f8a8a624e9e772c5a717bfb2e2ca2135f296011'
            '1256b241cd477b265a3c2d64bdc19ffe3c9bbcee82ea3994c590c2c76e767d99'
            '7a42d16108eb9a8eacadef3603527fa1beab857cc4db3bd228858488fb1f3fda'
            '8f810dd873e37d6144f70b440880f4fac9fb0f58bf0486bb6e873e38a74c010f'
            '819961379909c028e321f37e27a8b1b08f1f1e3dd58680e07b541921282da532'
            '407a850da196a58cc0302ab8e71f50dfc298fd067d1c0df813fc26cf22fcfe39'
            'cc0d4e0cd7da0a364c6a9756f915d4935735b2f37a1a899e067c2ed7e90f359d'
            '75a43175fb6f289215669a7aff23a86459bcf966303a24b4013a42da53fad035'
            '68045bcff777bc175e9f17ba46e0a8b13450c4546c6c9db3d9b9e2ed31af812d'
            'cda196f911af55f8c26e711040a66637aed03df9dfdc149aaf7fdbecf1bb19da'
            '4d5cf3c1a3660ad1376090fa5916aae38cf5fd8b240e47bde5ec969944edd1b6'
            'd2ebb6dc8f0354cdb4ef8e9e8e51b06a024e66e33d1c2e5a731be443a4275f40'
            '2398a30ce372bad67c2aec272197f94afa261b10fe8ae4a926f8fee01947e423'
            '17a277449434c96ff7f1e0a812d62fc67806c27cc128fcb2425d609bbe63f38b')

validpgpkeys=('ABAF11C65A2970B130ABE3C479BE3E4300411886' # Linus Torvalds
              '647F28654894E3BD457199BE38DBBDC86092693E' # Greg Kroah-Hartman
              '64254695FFF0AA4466CC19E67B96E8162A8CF5D1' # Sebastian Andrzej Siewior
              '5ED9A48FC54C0A22D1D0804CEBC26CDB5A56DE73' # Steven Rostedt
             )

_kernelname=${pkgbase#linux}

prepare() {
  cd "${srcdir}/${_srcname}"

  # add upstream patch
  patch -p1 -i "${srcdir}/patch-${_pkgver}"

  # add realtime patch
  msg "applying patch-${_pkgver}-${_rtpatchver}.patch"
  patch -p1 -i "${srcdir}/patch-${_pkgver}-${_rtpatchver}.patch"

  # add latest fixes from stable queue, if needed
  # http://git.kernel.org/?p=linux/kernel/git/stable/stable-queue.git
  
  # set DEFAULT_CONSOLE_LOGLEVEL to 4 (same value as the 'quiet' kernel param)
  # remove this when a Kconfig knob is made available by upstream
  # (relevant patch sent upstream: https://lkml.org/lkml/2011/7/26/227)
  patch -p1 -i "${srcdir}/change-default-console-loglevel.patch"

  # A patch to fix a problem that ought to be fixed in the NVIDIA source code.
  # Stops X from hanging on certain NVIDIA cards
  msg "fix-race-in-PRT-wait-for-completion-simple-wait-code_Nvidia-RT.patch"
  patch -p1 -i "${srcdir}/fix-race-in-PRT-wait-for-completion-simple-wait-code_Nvidia-RT.patch"

######## Zen kernel optimization/flags patch

  # add Custom Flag patch (Zen)
  msg "applying Custom flags patch"
  patch -Np1 -i "${srcdir}/custom-flags-kernel.patch" 

  msg "  ..    SUCCESS :)"

######## enable cpu optimizations (Graysky @ github)

  msg "applying enable_additional_cpu_optimizations_for_gcc_v4.9+_kernel_v3.15+.patch"
  patch -Np1 -i "${srcdir}/enable_additional_cpu_optimizations_for_gcc_v4.9+_kernel_v3.15+.patch"

  msg "  ..    SUCCESS :)"

######## bfq io scheduler support

  msg "Patching source with BFQ patches"
  for p in $(ls ${srcdir}/000{1,2,3}-block*.patch); do
      patch -Np1 -i "$p"
  done

######## UKSM support [in-kernel memory deduplication]

  msg "Patching with UKSM"
  cp "${srcdir}/uksm-0.1.2.3-for-v3.18.patch" ./
  patch -Np1 -i ./uksm-0.1.2.3-for-v3.18.patch

  msg "  ..    SUCCESS :)"

######## add mm_vmMax_readahead.patch / change max_readahead of the linux kernel.

  msg "applying mm_vmMax_readahead.patch"
  patch -Np1 -i "${srcdir}/mm_vmMax_readahead.patch"

  msg "  ..    SUCCESS :)"

######## Pulled from Debian rt patchset: drivers-serial-call-flush_to_ldisc-when-the-irq-is-t.patch

  # Ensure that flush_to_ldisc is called when the irq is threaded.

  msg "applying drivers-serial-call-flush_to_ldisc-when-the-irq-is-t.patch"
  patch -p1 -i "${srcdir}/drivers-serial-call-flush_to_ldisc-when-the-irq-is-t.patch"

  msg "  ..    SUCCESS :)"

####### Drop posix-cpu-timers rtprio to 98

  # This patch lowers the posix-cpu-timers to rtprio 98, basically to allow more room 
  # for a hypothetical high priority thread[s]. I am enabling this patch, in part, for 
  # the 'threadsirq' patch/feature [below]..

  msg "applying posix-cpu-timers_kthreads98.patch"
  patch -p1 -i "${srcdir}/posix-cpu-timers_kthreads98.patch"

  msg "  ..    SUCCESS :)"

####### threadsirqs: resurrecting softirq threads on linux-l-pa 3.14

  # enable/disable splitting of sirqs using kernel commandline 'threadsirqs', which allows the user
  # to prioritize them individually, allowing granular control.  imo, It makes sense to make this 
  # functionality available to rt users [note: really intended for machines with more cores / and certain
  # workloads / applications.  

#  msg "applying softirq-resurrect-threads.patch"
#  patch -p1 -i "${srcdir}/softirq-resurrect-threads.patch"

#  msg "  ..    SUCCESS :)"

# I'll have to get a new version, must ask for it ;)

  msg "All patches have successfully been applied"

  if [ "${CARCH}" = "x86_64" ]; then
    cat "${srcdir}/config.x86_64" > ./.config
  else
    cat "${srcdir}/config" > ./.config
  fi

  if [ "${_kernelname}" != "" ]; then
    sed -i "s|CONFIG_LOCALVERSION=.*|CONFIG_LOCALVERSION=\"-${pkgrel}${_kernelname}\"|g" ./.config
    sed -i "s|CONFIG_LOCALVERSION_AUTO=.*|CONFIG_LOCALVERSION_AUTO=n|" ./.config
  fi

  # set extraversion to pkgrel
#  sed -ri "s|^(EXTRAVERSION =).*|\1 -${pkgrel}|" Makefile

  # don't run depmod on 'make install'. We'll do this ourselves in packaging
  sed -i '2iexit 0' scripts/depmod.sh

  # get kernel version
  make prepare

  # load configuration
  # Configure the kernel. Replace the line below with one of your choice.
  #make menuconfig # CLI menu for configuration
  #make nconfig # new CLI menu for configuration
  #make xconfig # X-based configuration
  #make oldconfig # using old config from previous kernel version
  # ... or manually edit .config

  # rewrite configuration
  yes "" | make config >/dev/null
}

build() {
  cd "${srcdir}/${_srcname}"

  make ${MAKEFLAGS} LOCALVERSION= bzImage modules
}

_package() {
  pkgdesc="The ${pkgbase/linux/Linux} kernel and modules"
  [ "${pkgbase}" = "linux" ] && groups=('base')
  depends=('coreutils' 'linux-firmware' 'kmod' 'mkinitcpio>=0.7')
  optdepends=('crda: to set the correct wireless channels of your country')
  provides=("kernel26${_kernelname}=${_pkgver}")
  conflicts=("kernel26${_kernelname}")
  replaces=("kernel26${_kernelname}")
  backup=("etc/mkinitcpio.d/${pkgbase}.preset")
  install=linux-l-pa.install

  cd "${srcdir}/${_srcname}"

  KARCH=x86

  # get kernel version
  _kernver="$(make LOCALVERSION= kernelrelease)"
  _basekernel=${_kernver%%-*}
  _basekernel=${_basekernel%.*}

  mkdir -p "${pkgdir}"/{lib/modules,lib/firmware,boot}
  make LOCALVERSION= INSTALL_MOD_PATH="${pkgdir}" modules_install
  cp arch/$KARCH/boot/bzImage "${pkgdir}/boot/vmlinuz-${pkgbase}"

  # set correct depmod command for install
  cp -f "${startdir}/${install}" "${startdir}/${install}.pkg"
  true && install=${install}.pkg
  sed \
    -e  "s/KERNEL_NAME=.*/KERNEL_NAME=${_kernelname}/" \
    -e  "s/KERNEL_VERSION=.*/KERNEL_VERSION=${_kernver}/" \
    -i "${startdir}/${install}"

  # install mkinitcpio preset file for kernel
  install -D -m644 "${srcdir}/linux-l-pa.preset" "${pkgdir}/etc/mkinitcpio.d/${pkgbase}.preset"
  sed \
    -e "1s|'linux.*'|'${pkgbase}'|" \
    -e "s|ALL_kver=.*|ALL_kver=\"/boot/vmlinuz-${pkgbase}\"|" \
    -e "s|default_image=.*|default_image=\"/boot/initramfs-${pkgbase}.img\"|" \
    -e "s|fallback_image=.*|fallback_image=\"/boot/initramfs-${pkgbase}-fallback.img\"|" \
    -i "${pkgdir}/etc/mkinitcpio.d/${pkgbase}.preset"

  # remove build and source links
  rm -f "${pkgdir}"/lib/modules/${_kernver}/{source,build}
  # remove the firmware
  rm -rf "${pkgdir}/lib/firmware"
  # gzip -9 all modules to save 100MB of space
  find "${pkgdir}" -name '*.ko' -exec gzip -9 {} \;
  # make room for external modules
  ln -s "../extramodules-${_basekernel}${_kernelname:--ARCH}" "${pkgdir}/lib/modules/${_kernver}/extramodules"
  # add real version for building modules and running depmod from post_install/upgrade
  mkdir -p "${pkgdir}/lib/modules/extramodules-${_basekernel}${_kernelname:--ARCH}"
  echo "${_kernver}" > "${pkgdir}/lib/modules/extramodules-${_basekernel}${_kernelname:--ARCH}/version"

  # Now we call depmod...
  depmod -b "${pkgdir}" -F System.map "${_kernver}"

  # move module tree /lib -> /usr/lib
  mkdir -p "${pkgdir}/usr"
  mv "${pkgdir}/lib" "${pkgdir}/usr/"

  # add vmlinux
  install -D -m644 vmlinux "${pkgdir}/usr/lib/modules/${_kernver}/build/vmlinux"
}

_package-headers() {
  pkgdesc="Header files and scripts for building modules for ${pkgbase/linux/Linux} kernel"
  provides=("kernel26${_kernelname}-headers=${_pkgver}")
  conflicts=("kernel26${_kernelname}-headers")
  replaces=("kernel26${_kernelname}-headers")

  install -dm755 "${pkgdir}/usr/lib/modules/${_kernver}"

  cd "${srcdir}/${_srcname}"
  install -D -m644 Makefile \
    "${pkgdir}/usr/lib/modules/${_kernver}/build/Makefile"
  install -D -m644 kernel/Makefile \
    "${pkgdir}/usr/lib/modules/${_kernver}/build/kernel/Makefile"
  install -D -m644 .config \
    "${pkgdir}/usr/lib/modules/${_kernver}/build/.config"

  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/include"

  for i in acpi asm-generic config crypto drm generated keys linux math-emu \
    media net pcmcia scsi sound trace uapi video xen; do
    cp -a include/${i} "${pkgdir}/usr/lib/modules/${_kernver}/build/include/"
  done

  # copy arch includes for external modules
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/arch/x86"
  cp -a arch/x86/include "${pkgdir}/usr/lib/modules/${_kernver}/build/arch/x86/"

  # copy files necessary for later builds, like nvidia and vmware
  cp Module.symvers "${pkgdir}/usr/lib/modules/${_kernver}/build"
  cp -a scripts "${pkgdir}/usr/lib/modules/${_kernver}/build"

  # fix permissions on scripts dir
  chmod og-w -R "${pkgdir}/usr/lib/modules/${_kernver}/build/scripts"
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/.tmp_versions"

  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/arch/${KARCH}/kernel"

  cp arch/${KARCH}/Makefile "${pkgdir}/usr/lib/modules/${_kernver}/build/arch/${KARCH}/"

  if [ "${CARCH}" = "i686" ]; then
    cp arch/${KARCH}/Makefile_32.cpu "${pkgdir}/usr/lib/modules/${_kernver}/build/arch/${KARCH}/"
  fi

  cp arch/${KARCH}/kernel/asm-offsets.s "${pkgdir}/usr/lib/modules/${_kernver}/build/arch/${KARCH}/kernel/"

  # add docbook makefile
  install -D -m644 Documentation/DocBook/Makefile \
    "${pkgdir}/usr/lib/modules/${_kernver}/build/Documentation/DocBook/Makefile"

  # add dm headers
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/md"
  cp drivers/md/*.h "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/md"

  # add inotify.h
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/include/linux"
  cp include/linux/inotify.h "${pkgdir}/usr/lib/modules/${_kernver}/build/include/linux/"

  # add wireless headers
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/net/mac80211/"
  cp net/mac80211/*.h "${pkgdir}/usr/lib/modules/${_kernver}/build/net/mac80211/"

  # add dvb headers for external modules
  # in reference to:
  # http://bugs.archlinux.org/task/9912
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/dvb-core"
  cp drivers/media/dvb-core/*.h "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/dvb-core/"
  # and...
  # http://bugs.archlinux.org/task/11194
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/include/config/dvb/"
  cp include/config/dvb/*.h "${pkgdir}/usr/lib/modules/${_kernver}/build/include/config/dvb/"

  # add dvb headers for http://mcentral.de/hg/~mrec/em28xx-new
  # in reference to:
  # http://bugs.archlinux.org/task/13146
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/dvb-frontends/"
  cp drivers/media/dvb-frontends/lgdt330x.h "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/dvb-frontends/"
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/i2c/"
  cp drivers/media/i2c/msp3400-driver.h "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/i2c/"

  # add dvb headers
  # in reference to:
  # http://bugs.archlinux.org/task/20402
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/usb/dvb-usb"
  cp drivers/media/usb/dvb-usb/*.h "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/usb/dvb-usb/"
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/dvb-frontends"
  cp drivers/media/dvb-frontends/*.h "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/dvb-frontends/"
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/tuners"
  cp drivers/media/tuners/*.h "${pkgdir}/usr/lib/modules/${_kernver}/build/drivers/media/tuners/"

  # add xfs and shmem for aufs building
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/fs/xfs"
  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build/mm"
  # removed in 3.17 series
  # cp fs/xfs/xfs_sb.h "${pkgdir}/usr/lib/modules/${_kernver}/build/fs/xfs/xfs_sb.h"

  # copy in Kconfig files
  for i in $(find . -name "Kconfig*"); do
    mkdir -p "${pkgdir}"/usr/lib/modules/${_kernver}/build/`echo ${i} | sed 's|/Kconfig.*||'`
    cp ${i} "${pkgdir}/usr/lib/modules/${_kernver}/build/${i}"
  done

  chown -R root.root "${pkgdir}/usr/lib/modules/${_kernver}/build"
  find "${pkgdir}/usr/lib/modules/${_kernver}/build" -type d -exec chmod 755 {} \;

  # strip scripts directory
  find "${pkgdir}/usr/lib/modules/${_kernver}/build/scripts" -type f -perm -u+w 2>/dev/null | while read binary ; do
    case "$(file -bi "${binary}")" in
      *application/x-sharedlib*) # Libraries (.so)
        /usr/bin/strip ${STRIP_SHARED} "${binary}";;
      *application/x-archive*) # Libraries (.a)
        /usr/bin/strip ${STRIP_STATIC} "${binary}";;
      *application/x-executable*) # Binaries
        /usr/bin/strip ${STRIP_BINARIES} "${binary}";;
    esac
  done

  # remove unneeded architectures
  rm -rf "${pkgdir}"/usr/lib/modules/${_kernver}/build/arch/{alpha,arc,arm,arm26,arm64,avr32,blackfin,c6x,cris,frv,h8300,hexagon,ia64,m32r,m68k,m68knommu,metag,mips,microblaze,mn10300,openrisc,parisc,powerpc,ppc,s390,score,sh,sh64,sparc,sparc64,tile,unicore32,um,v850,xtensa}
}

_package-docs() {
  pkgdesc="Kernel hackers manual - HTML documentation that comes with the ${pkgbase/linux/Linux} kernel"
  provides=("kernel26${_kernelname}-docs=${_pkgver}")
  conflicts=("kernel26${_kernelname}-docs")
  replaces=("kernel26${_kernelname}-docs")

  cd "${srcdir}/${_srcname}"

  mkdir -p "${pkgdir}/usr/lib/modules/${_kernver}/build"
  cp -al Documentation "${pkgdir}/usr/lib/modules/${_kernver}/build"
  find "${pkgdir}" -type f -exec chmod 444 {} \;
  find "${pkgdir}" -type d -exec chmod 755 {} \;

  # remove a file already in linux package
  rm -f "${pkgdir}/usr/lib/modules/${_kernver}/build/Documentation/DocBook/Makefile"
}

pkgname=("${pkgbase}" "${pkgbase}-headers" "${pkgbase}-docs")
for _p in ${pkgname[@]}; do
  eval "package_${_p}() {
    $(declare -f "_package${_p#${pkgbase}}")
    _package${_p#${pkgbase}}
  }"
done

# vim:set ts=8 sts=2 sw=2 et:
