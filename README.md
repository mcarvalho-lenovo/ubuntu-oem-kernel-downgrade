# Downgrade OEM Kernel in Ubuntu to Version 6.5.0-1023

This guide explains how to downgrade the kernel on Ubuntu to the OEM version `6.5.0-1023`.

## Prerequisites

1. Access to a terminal with `sudo` privileges.
2. A stable internet connection.
3. Familiarity with basic Linux commands.

## Step-by-Step Guide

### 1. Check Current Kernel Version

Run the following command to check your current kernel version:

```bash
uname -r
```

### 2. Update the Package List

Ensure your system's package list is up to date:

```bash
sudo apt update
```

### 3. Search for Available OEM Kernels

List the available OEM kernel versions using the following command:

```bash
apt search linux-image-oem
```

Look for the specific version `6.5.0-1023` in the search results.

### 4. Install the Target Kernel Version

Install the specific OEM kernel version `6.5.0-1023` by running:

```bash
sudo apt install linux-image-6.5.0-1023-oem linux-modules-6.5.0-1023-oem
```

### 5. Update GRUB

After installation, update the GRUB bootloader to ensure the new kernel is available during boot:

```bash
sudo update-grub
```

### 6. Reboot and Select Kernel

Reboot the system to apply the changes:

```bash
sudo reboot
```

During the reboot process, press and hold the `Shift` key (or `Esc` on some systems) to open the GRUB menu. Select **Advanced options for Ubuntu**, and then choose the `6.5.0-1023-oem` kernel from the list.

### 7. Verify the Kernel Version

After the system boots, confirm the kernel version:

```bash
uname -r
```

Ensure the output shows `6.5.0-1023-oem`.

## Optional: Remove Unused Kernels

To free up disk space, you can remove older or unused kernel versions. First, list installed kernels:

```bash
dpkg --list | grep linux-image
```

Remove the unwanted kernel versions carefully:

```bash
sudo apt remove linux-image-<version>
```

Replace `<version>` with the specific kernel version you wish to remove.

Finally, clean up unused packages:

```bash
sudo apt autoremove
```

## Troubleshooting

- If the kernel does not appear in the GRUB menu, ensure it was installed correctly and re-run `sudo update-grub`.
- If you encounter boot issues, you can revert to a previous kernel version via the GRUB menu.

## Additional Resources

- Ubuntu OEM Kernel Documentation: [Ubuntu OEM Documentation](https://wiki.ubuntu.com/Kernel/OEM)
- GRUB Bootloader Documentation: [GNU GRUB Manual](https://www.gnu.org/software/grub/manual/)

---

This guide provides a detailed walkthrough to ensure the downgrade is performed safely. Use it responsibly and always back up critical data before making significant system changes.
