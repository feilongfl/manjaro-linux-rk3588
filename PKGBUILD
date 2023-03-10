# RK356X Quartz64
# Kernel Source Maintainer: Peter Geis
# Maintainer: Dan Johansen <strit@manjaro.org>
# Contributor: Spikerguy <shareahack@hotmail.com>

pkgbase=linux-rk3588
_commit=26bab1be400998807e9f83a088ff75134e42aa1a
#_srcname=linux-quartzpro64-${_commit}
_kernelname=${pkgbase#linux}
_desc="Kernel for Quartz64 (development version)"
pkgver=6.2.3
pkgrel=2
_srcname="linux-${pkgver/%.0/}"
arch=('aarch64')
url="https://github.com/neg2led/linux-quartz64"
license=('GPL2')
makedepends=('xmlto' 'docbook-xsl' 'kmod' 'inetutils' 'bc' 'git')
options=('!strip')
source=("http://www.kernel.org/pub/linux/kernel/v6.x/${_srcname}.tar.xz"
        '1001-dt-bindings-soc-rockchip-add-initial-rk3588-syscon-c.patch'
	'1002-arm64-dts-rockchip-Add-rk3588-pinctrl-data.patch'
	'1003-arm64-dts-rockchip-Add-base-DT-for-rk3588-SoC.patch'
	'1004-dt-bindings-arm-rockchip-add-initial-rk3588-boards.patch'
	'1005-arm64-dts-rockchip-Add-rk3588-evb1-board.patch'
	'1006-arm64-dts-rockchip-Add-rock-5a-board.patch'
	'1007-arm64-dts-rockchip-Add-rock-5b-board.patch'
	'1008-clk-RK808-reduce-struct-rk808-usage.patch'
	'1009-mfd-rk808-convert-to-device-managed-resources.patch'
	'1010-mfd-rk808-use-dev_err_probe.patch'
	'1011-mfd-rk808-replace-struct-i2c_client-with-struct-devi.patch'
	'1012-mfd-rk808-split-into-core-and-i2c.patch'
	'1013-mfd-rk8xx-i2c-use-device_get_match_data.patch'
	'1014-dt-bindings-mfd-add-rk806-binding.patch'
	'1015-mfd-rk8xx-add-rk806-support.patch'
	'1016-pinctrl-rk805-add-rk806-pinctrl-support.patch'
	'1017-regulator-expose-regulator_find_closest_bigger.patch'
	'1018-regulator-rk808-add-rk806-support.patch'
	'1019-regulator-add-rk860x-support.patch'
	'1020-arm64-dts-rockchip-rk3588-add-pmic-design-variants.patch'
	'1021-thermal-rockchip-Simplify-getting-match-data.patch'
	'1022-thermal-rockchip-Simplify-clock-logic.patch'
	'1023-thermal-rockchip-Use-dev_err_probe.patch'
	'1024-thermal-rockchip-Simplify-channel-id-logic.patch'
	'1025-thermal-rockchip-Support-dynamic-sized-sensor-array.patch'
	'1026-thermal-rockchip-Support-RK3588-SoC-in-the-thermal-d.patch'
	'1027-cpufreq-rockchip-Introduce-driver-for-rk3588.patch'
	'1028-dt-bindings-rockchip-thermal-Support-the-RK3588-SoC-.patch'
	'1029-arm64-dts-rockchip-rk3588-add-cpu-frequency-scaling-.patch'
	'1030-arm64-dts-rockchip-enable-cpu-freq-scalling-evb1.patch'
	'1031-arm64-dts-rockchip-enable-cpu-freq-scalling-rock5x.patch'
	'1033-dt-bindings-mmc-rockchip-dw-mshc-Add-RK3588-compatib.patch'
	'1034-arm64-dts-rockchip-rk3588-Add-sdmmc-node.patch'
	'1035-arm64-dts-rockchip-Add-support-for-SD-card-for-Rock5x.patch'
	'1036-arm64-dts-rockchip-Add-support-user-led-Rock5a-5b.patch'
	'1040-phy-rockchip-add-RK3588-combphy-support.patch'
	'1041-phy-rockchip-support-multiple-PCIe-3.0-lanes-on-RK35.patch'
	'1042-irqchip-gic-v3-add-hackaround-for-rk3568-its.patch'
	'1043-arm64-dts-rockchip-rk3588-add-pcie-controllers.patch'
	'1045-arm64-dts-rockchip-enable-pcie-rock5x.patch'
	'1050-rockchip-add-SoC-headers-from-downstream-kernel.patch'
	'1051-phy-rockchip-inno-usb2-update-from-downstream-kernel.patch'
	'1052-arm64-dts-rockchip-rk3588-enable-usb2.patch'
	'1054-arm64-dts-rockchip-enable-usb2-rock5x.patch'
	'1002-arm64-dts-rockchip-add-dts-for-Orange-PI-5-rk3588s.patch::https://github.com/spikerguy/linux-quartzpro64/commit/26bab1be400998807e9f83a088ff75134e42aa1a.patch'
	'1011-arm64-dts-rockchip-add-dts-for-Orange-PI-5-rk3588s.patch ::https://github.com/spikerguy/linux-quartzpro64/commit/83363c2cdd622e98c7a904974a5cdab71cba109b.patch'
	#'1001-arm64-dts-rockchip-add-dts-for-Orange-PI-5-rk3588s.patch'
	#'1008-net:-phy:-Add-driver-for-Motorcomm-yt8521-gigabit-ethernet-phy.patch'
	#'1009-net:-phy:-fix-yt8521-duplicated-argument-to-or.patch'
	#'1010-net:-phy:-add-Motorcomm-YT8531S-phy-id.patch'
	'1002-net:phy-fix-the-spelling-problem-of-Sentinel.patch'
	'1003-motorcomm:-change-the-phy-id-of-yt8521-and-yt8531s-to-lowercase.patch'
	'1004-Add-BIT-macro-for-Motorcomm-yt8521-yt8531-gigabit-ethernet-phy.patch'
	'1005-Add-dts-support-for-Motorcomm-yt8521-gigabit-ethernet-phy.patch'
	'1006-Add-dts-support-for-Motorcomm-yt8531s-gigabit-ethernet-phy.patch'
	'1007-Add-driver-for-Motorcomm-yt8531-gigabit-ethernet-phy.patch'
	#'1011-add-regulator-rk860x.patch'
	#'1012-fix-regulator-rk860x.patch'
	'config'
        'linux.preset'
        '60-linux.hook'
        '90-linux.hook')
md5sums=('c6f5873837275e6ba35736bbe2370cbe'
         'd922063808f230664156f729920755ab'
         'b9dab837c4654e75b7d0f9ae78f50e41'
         '3c42f6a8b97ec00806720c8759f992e3'
         'c3ef548816421cca6bd0fd853035b927'
         '22f027de8454af268d8a5dae10762773'
         '5be59196ef427e779f5e9d9a6fc61326'
         'f62bfda830e16c50c1e704b61d12b926'
         '50bc286fff66d5b787bcc8b35a2949ab'
         '33a4e37b0490ac046cfcbc3ef6548c74'
         '2c53048c07fa133c3a7866fb3acd7129'
         'a372d96ac9e74909d1413b90055d6cbe'
         '369b3b68423d715c0daaf57b7b5a3e0f'
         'ada9d9e504389271bc91f30d2afce14a'
         'bf29faff72aceb34af8880ea1bcae5d0'
         '59ff36f0bac4423ca089109482073b90'
         'eca684ac59133945f3d20c142b01e500'
         '789063aac9525eaab0e179f1308f8716'
         '1d9f026c91d6c85f9040b59a02ca06d4'
         '2fa04433bf8d2530ceef8280b9c17c84'
         'cad9dc14e1dfb9dd96cb1a9c29fc6e75'
         '6a70513bb8ef68fe9250c7eb1ca73155'
         'c6c5cacd08274029d21ef480052f7e24'
         '05bb842be99e7cb6af48c8363aa90c73'
         'f40a5ccc71f143c9abe55a4d190284cd'
         '8685077a303a0241422dbc0bee2af5c0'
         'f8ff26e86043155d39d443fe83f69dce'
         '3266bacbc4b997be68fc28916f6960f8'
         'c8c7708f32db3f6662197c36e8133b49'
         'a0631610bc62d1043f25ee4db0fb7511'
         'e59272700a98cdc0d5429daa9833174b'
         'e87d23f39803e5e9818c324ba21e83e5'
         '33d2c840ec81792bfd1fe43f9d1b1a4f'
         'd5c413e1de46adc442c599a789dadde8'
         '6ad4ce4c1e377c1afb90c0fbbd4558c1'
         '95ff6e10fdc1f455843466a80fa9550e'
         '837730c92cb6e1b78df7a6c75114db12'
         '1a77379e3b5c02ae8e83c083f5de716c'
         'd9e84e84c6dc946bd24c22643ebe83a5'
         '9d96a79ca90ea746a7b26035dcc3f56a'
         'fc4541a30055da7b576cd6a2250a78e1'
         'fd2983a88af94b2ee2e049da60f88832'
         'f6d50955e9b4cab6208b9df89310720c'
         '2d795ceb3281136a3040528f77b2966a'
         'fd533c949b41afe0c62b27f3b67e47b3'
         '6c8a675d8d41dac46285ecd9e0aa8447'
         '0a113d0c6f13031732782b1bfca2b731'
         '9c31604c50419d4243cdf983c9ca7e1f'
         'c40473c06fe00c6c4a7ea698b75e460b'
         'f977c2dd48305193b48273ec23e9722f'
         '6463c6636a9672d70607932201837481'
         'f662805ac1cc9a3151e49cbc3e4e0d05'
         'e675d8a1987ee9c309b40081f0949920'
         '03746024db61b918d3d460bd25a7d8de'
         '86d4a35722b5410e3b29fc92dae15d4b'
         'ce6c81ad1ad1f8b333fd6077d47abdaf'
         '3dc88030a8f2f5a5f97266d99b149f77')

prepare() {
    #sed -i s/'EXTRAVERSION = -rc7'/'EXTRAVERSION ='/ "${_srcname}"/Makefile

# Patches
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

# cd "${srcdir}/${_srcname}"
cd ${_srcname}
  # Assorted Manjaro ARM patches
  apply_patches 1

  # Assorted Pinebook, PinePhone and PineTab patches
  apply_patches 2
  
  # Assorted rk356x patches
  apply_patches 3

  # Pinebook Pro patches by Megi: https://github.com/torvalds/linux/compare/master...megous:linux:pbp-6.2
  # apply_patches 4

    cat "${srcdir}/config" > ./.config

    # add pkgrel to extraversion
    sed -ri "s|^(EXTRAVERSION =)(.*)|\1 \2-${pkgrel}|" Makefile

    # don't run depmod on 'make install'. We'll do this ourselves in packaging
    sed -i '2iexit 0' scripts/depmod.sh
#    make oldconfig
#	make menuconfig
 #	cp ./.config "${srcdir}/config"

}

build() {
#  cd "${srcdir}/${_srcname}"
cd ${_srcname}
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

#  cd "${srcdir}/${_srcname}"
cd ${_srcname}
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
 

