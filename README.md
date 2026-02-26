# OpenSuse-Tumbleweed-installation-and-documents.

## Packages to install
```
zypper install ibus ibus-unikey qemu virt-manager libvirt vde2 iptables systemd-networkd swtpm android-tools google-noto-sans-cjk-fonts flatseal btop vim ptyxis ghostty paper showtime resources android-tools android-udev-rules syncthing secrets impression extension-manager keepassxc vulkan-tools vulkan-loader
```

## Packages to remove
```
zypper remove gnome-connections gnome-maps yelp nano evince gnome-chess totem gnome-photos gnome-photos lightsoff swell-foop quadrapassel yast2 yast2-alternatives opensuse-welcome opensuse-welcome-launcher gnome-packagekit seahorse gnome-system-monitor iagno dconf-editor gnome-console
```

## Nvidia
https://en.opensuse.org/SDB:NVIDIA_drivers

## Edit hostname
* just edit **/etc/hostname**

## Wayland for electron
Add ``ELECTRON_OZONE_PLATFORM_HINT=auto`` to ``/etc/environment``

## TPM2 
https://news.opensuse.org/2024/09/20/quickstart-fde-yast2/


## Troubleshoot
<pre>
ERROR: the validation of PCR 15 failed
ERROR: Missing measure-pcr-prediction file
Use ‘measure-pcr-validator.ignore=yes’ in cmdline to bypass the check
*** The system will be halted. Press any key …
</pre>

* You might be encounted this issue when decrypt drive with tpm2, this [link](https://github.com/openSUSE/sdbootutil/issues/308) will explain why. TLDR, make sure file **measure-pcr-prediction** is present in both **/var/lib/sdbootutil/** and **/boot/efi/EFI/systemd/** . If not, use this command with root:
```
sdbootutil update-predictions --measure-pcr
```
