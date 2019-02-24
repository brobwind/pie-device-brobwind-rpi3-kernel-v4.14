# Overlays for the Raspberry Pi platform

dtbo-$(CONFIG_ARCH_BCM2835) += \
	pwm-2chan.dtbo \
	sdtweak.dtbo \
	vc4-kms-v3d.dtbo \

dtbo-$(CONFIG_ARCH_BCM2835) += \
	bcm2710-rpi-3-b-android-fstab.dtbo \
	bcm2710-rpi-3-b-cpufreq.dtbo

targets += dtbs dtbs_install
targets += $(dtbo-y)

always		:= $(dtbo-y)
clean-files	:= *.dtbo
