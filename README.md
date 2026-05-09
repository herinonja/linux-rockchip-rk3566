# linux-rockchip

Custom Linux kernel build for **Rockchip RK3566 Radxa Zero 3W**.

# Installation :

sudo apt install dwarves

sha256sum -c SHA256SUMS

sudo dpkg -i linux-headers-radxa-zero3w-rk3566_7.0.3-1_arm64.deb

sudo dpkg -i linux-image-radxa-zero3w-rk3566_7.0.3-1_arm64.deb

sudo dpkg -i aic8800-firmware_*.deb

sudo dpkg -i aic8800-sdio-dkms_*.deb

sudo tee /etc/apt/apt.conf.d/99-rk3566-custom-kernel >/dev/null <<'EOF'
DPkg::Post-Invoke {
  "if [ -f /boot/Image-7.0.3-radxa-zero3w ]; then ln -sf Image-7.0.3-radxa-zero3w /boot/Image; fi";
  "if [ -f /boot/uInitrd-7.0.3 ]; then ln -sf uInitrd-7.0.3 /boot/uInitrd; fi";
};
EOF

sudo reboot



