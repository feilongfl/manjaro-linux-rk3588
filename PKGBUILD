# RK356X Quartz64
# Kernel Source Maintainer: Peter Geis
# Contributor: Furkan Kardame <f.kardame@manjaro.org>

pkgbase=linux-rk3588
_commit=d92c954614b7bc31364a0e1e3b93f26d9b30b544
_kernelname=${pkgbase#linux}
_desc="Kernel for Quartz64 (development version)"
pkgver=6.1.31
pkgrel=1
_srcname="linux-${pkgver/%.0/}"
arch=('aarch64')
url="https://github.com/neg2led/linux-quartz64"
license=('GPL2')
makedepends=('xmlto' 'docbook-xsl' 'kmod' 'inetutils' 'bc' 'git')
options=('!strip')
source=("http://www.kernel.org/pub/linux/kernel/v6.x/${_srcname}.tar.xz"
        '1001-add-rk3588.patch'
	'1002-net:-phy:-Add-driver-for-Motorcomm-yt8521-gigabit-ethernet-phy.patch'
        '1003-net:-phy:-fix-yt8521-duplicated-argument-to-or.patch'
        '1004-net:-phy:-add-Motorcomm-YT8531S-phy-id.patch'
        '1005-net:phy-fix-the-spelling-problem-of-Sentinel.patch'
        '1006-motorcomm:-change-the-phy-id-of-yt8521-and-yt8531s-to-lowercase.patch'
        '1007-Add-BIT-macro-for-Motorcomm-yt8521-yt8531-gigabit-ethernet-phy.patch'
        '1008-Add-dts-support-for-Motorcomm-yt8521-gigabit-ethernet-phy.patch'
        '1009-Add-dts-support-for-Motorcomm-yt8531s-gigabit-ethernet-phy.patch'
        '1010-Add-driver-for-Motorcomm-yt8531-gigabit-ethernet-phy.patch'
        '1011-add-regulator-rk860x.patch'
	'1012-fix-regulator-rk860x.patch'
	'1013-add-arm64-rk3588s-roc-pc.patch'
	'1014-add-usb-opi5.patch'
	'1015-add-m3-usb.patch'
	'1016-arm64-dts-rockchip-add-dts-for-Firefly-itx-rk3588j.patch'
	'1050-rockchip-add-SoC-headers-from-downstream-kernel.patch'
	'1051-phy-rockchip-inno-usb2-update-from-downstream-kernel.patch'
	'1052-arm64-dts-rockchip-rk3588-enable-usb2.patch'
	'config'
        'linux.preset'
        '60-linux.hook'
        '90-linux.hook')
md5sums=('72ac33b766704899f0a0d4d5e5fb02a9'
         '58eab213b222883f98157d3e26803157'
         '31da53f23eafd26e88e05c0288997e99'
         'b0d7208d2741e1b011506b3df03477fd'
         'bfa314ac78289882a37098895350a12b'
         '9c31604c50419d4243cdf983c9ca7e1f'
         'c40473c06fe00c6c4a7ea698b75e460b'
         'f977c2dd48305193b48273ec23e9722f'
         '6463c6636a9672d70607932201837481'
         'f662805ac1cc9a3151e49cbc3e4e0d05'
         'e675d8a1987ee9c309b40081f0949920'
         '4a11c1a466d977b1a38baddafd962035'
         'd03da09a0390e29d4bf38086d6a7dc1f'
         '4be87411dbd8cd9b9821acb791e8c09d'
         '68a346e3615e9c3ec6367ccd8d8daa3f'
         '7af54c2e95acbb9dc45230c4e87831c7'
         '0ccab1b29c09d0759142b772911bdf7e'
         'fd2983a88af94b2ee2e049da60f88832'
         'f6d50955e9b4cab6208b9df89310720c'
         '2d795ceb3281136a3040528f77b2966a'
         '95d3d39925143e6c5f417a355f15a6f4'
         'fbb7f2695efe0c83265cad1c5e6f0a81'
         'ce6c81ad1ad1f8b333fd6077d47abdaf'
         '3dc88030a8f2f5a5f97266d99b149f77')

prepare() {
    #sed -i s/'EXTRAVERSION = -rc7'/'EXTRAVERSION ='/ "${_srcname}"/Makefile
apply_patches() {
      local PATCH
      for PATCH in "${source[@]}"; do
          PATCH="${PATCH%%::*}"
          PATCH="${PATCH##*/}"
          [[ ${PATCH} = $1*.patch ]] || continue
          msg2 "Applying patch: ${PATCH}..."
          patch -N -p1 < "../${PATCH}"
      done
  }

  cd ${_srcname}

  # Assorted Manjaro ARM patches
  apply_patches 1

  # Assorted
  apply_patches 2
  
  # Assorted 
  apply_patches 3

  # Testing Patches
  apply_patches 4

    cat "${srcdir}/config" > ./.config

    # add pkgrel to extraversion
    sed -ri "s|^(EXTRAVERSION =)(.*)|\1 \2-${pkgrel}|" Makefile

    # don't run depmod on 'make install'. We'll do this ourselves in packaging
    sed -i '2iexit 0' scripts/depmod.sh
#    make oldconfig
#	make menuconfig
  # cp ./.config "${srcdir}/config"

}

build() {
  cd "${srcdir}/${_srcname}"

  # get kernel version
  make prepare

  # load configuration
  # Configure the kernel. Replace the line below with one of your choice.
  #make menuconfig # CLI menu for configuration
  #make nconfig # new CLI menu for configuration
  #make xconfig # X-based configuration
  #make oldconfig # using old config from previous kernel version
  # ... or manually edit .config

  # Copy back our configuration (use with new kernel version)
  #cp ./.config /var/tmp/${pkgbase}.config

  ####################
  # stop here
  # this is useful to configure the kernel
  #msg "Stopping build"
  #return 1
  ####################

  #yes "" | make config

  # build!
  unset LDFLAGS
  make ${MAKEFLAGS} Image modules
  # Generate device tree blobs with symbols to support applying device tree overlays in U-Boot
  make ${MAKEFLAGS} DTC_FLAGS="-@" dtbs
}

_package() {
  pkgdesc="The Linux Kernel and modules - ${_desc}"
  depends=('coreutils' 'kmod' 'initramfs' 'fbset')
  optdepends=('crda: to set the correct wireless channels of your country'
              'linux-firmware: Additional firmware files for common hardware')
  provides=('kernel26' "linux=${pkgver}")
  conflicts=('linux')
  backup=("etc/mkinitcpio.d/${pkgbase}.preset")
  install=${pkgname}.install

  cd "${srcdir}/${_srcname}"

  KARCH=arm64

  # get kernel version
  #_kernver="$pkgver-$pkgrel-MANJARO-ARM"
  _kernver="$(make kernelrelease)"
  _basekernel=${_kernver%%-*}
  _basekernel=${_basekernel%.*}

  mkdir -p "${pkgdir}"/{boot,usr/lib/modules}
  make INSTALL_MOD_PATH="${pkgdir}/usr" modules_install
  make INSTALL_DTBS_PATH="${pkgdir}/boot/dtbs" dtbs_install
  cp arch/$KARCH/boot/Image "${pkgdir}/boot/"

   # make room for external modules
  local _extramodules="extramodules-${_basekernel}${_kernelname}"
  ln -s "../${_extramodules}" "${pkgdir}/usr/lib/modules/${_kernver}/extramodules"

  # add real version for building modules and running depmod from hook
  echo "${_kernver}" |
    install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_extramodules}/version"

  # remove build and source links
  rm "${pkgdir}"/usr/lib/modules/${_kernver}/{source,build}

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "${_kernver}"

  # sed expression for following substitutions
  local _subst="
    s|%PKGBASE%|${pkgbase}|g
    s|%KERNVER%|${_kernver}|g
    s|%EXTRAMODULES%|${_extramodules}|g
  "

  # install mkinitcpio preset file
  sed "${_subst}" ../linux.preset |
    install -Dm644 /dev/stdin "${pkgdir}/etc/mkinitcpio.d/${pkgbase}.preset"

  # install pacman hooks
  sed "${_subst}" ../60-linux.hook |
    install -Dm644 /dev/stdin "${pkgdir}/usr/share/libalpm/hooks/60-${pkgbase}.hook"
  sed "${_subst}" ../90-linux.hook |
    install -Dm644 /dev/stdin "${pkgdir}/usr/share/libalpm/hooks/90-${pkgbase}.hook"

}

_package-headers() {
  pkgdesc="Header files and scripts for building modules for linux kernel - ${_desc}"
  provides=("linux-headers=${pkgver}")
  conflicts=('linux-headers')
  cd ${_srcname}
  local _builddir="${pkgdir}/usr/lib/modules/${_kernver}/build"

  install -Dt "${_builddir}" -m644 Makefile .config Module.symvers
  install -Dt "${_builddir}/kernel" -m644 kernel/Makefile

  mkdir "${_builddir}/.tmp_versions"

  cp -t "${_builddir}" -a include scripts

  install -Dt "${_builddir}/arch/${KARCH}" -m644 arch/${KARCH}/Makefile
  install -Dt "${_builddir}/arch/${KARCH}/kernel" -m644 arch/${KARCH}/kernel/asm-offsets.s 
  #arch/$KARCH/kernel/module.lds

  cp -t "${_builddir}/arch/${KARCH}" -a arch/${KARCH}/include

  install -Dt "${_builddir}/drivers/md" -m644 drivers/md/*.h
  install -Dt "${_builddir}/net/mac80211" -m644 net/mac80211/*.h

  # http://bugs.archlinux.org/task/13146
  install -Dt "${_builddir}/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # http://bugs.archlinux.org/task/20402
  install -Dt "${_builddir}/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "${_builddir}/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "${_builddir}/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # add xfs and shmem for aufs building
  mkdir -p "${_builddir}"/{fs/xfs,mm}

  # copy in Kconfig files
  find . -name Kconfig\* -exec install -Dm644 {} "${_builddir}/{}" \;

  # remove unneeded architectures
  local _arch
  for _arch in "${_builddir}"/arch/*/; do
    [[ ${_arch} == */${KARCH}/ ]] && continue
    rm -r "${_arch}"
  done

  # remove documentation files
  rm -r "${_builddir}/Documentation"

  # remove now broken symlinks
  find -L "${_builddir}" -type l -printf 'Removing %P\n' -delete

  # strip scripts directory
  local file
  while read -rd '' file; do
    case "$(file -bi "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip $STRIP_SHARED "$file" ;;
    esac
  done < <(find "${_builddir}" -type f -perm -u+x ! -name vmlinux -print0 2>/dev/null)
  #strip $STRIP_STATIC "${_builddir}/vmlinux"
  
  # remove unwanted files
  find ${_builddir} -name '*.orig' -delete
}

pkgname=("${pkgbase}" "${pkgbase}-headers")
for _p in ${pkgname[@]}; do
  eval "package_${_p}() {
    _package${_p#${pkgbase}}
  }"
done
 

