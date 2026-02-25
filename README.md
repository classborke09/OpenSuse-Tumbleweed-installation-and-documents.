# OpenSuse-Tumbleweed-installation-and-documents.

# Unlike Arch Linux or Gentoo, OpenSuse installation pretty straight foward actually, this docs is mainly about troubleshoot for my need.

``
ERROR: the validation of PCR 15 failed
ERROR: Missing measure-pcr-prediction file
Use ‘measure-pcr-validator.ignore=yes’ in cmdline to bypass the check
*** The system will be halted. Press any key …
``
* You might be encounted this issue when decrypt drive with tpm2, this [link](https://github.com/openSUSE/sdbootutil/issues/308) will explain why. TLDR, make sure file measure-pcr-prediction present in both /var/lib/sdbootutil/ and /boot/efi/EFI/systemd/ . If not, use this command with root:
```
sdbootutil update-predictions --measure-pcr
```
