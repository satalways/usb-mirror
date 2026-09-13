<p align="center">
  <img src="assets/usb_mirror.png" alt="USB Mirror icon" width="160">
</p>

# USB Mirror

USB Mirror is a Windows desktop utility for creating complete USB-drive backups and restoring raw disk images.

## Features

- Create a byte-for-byte `.img` backup of a USB drive.
- Write `.img` and hybrid bootable `.iso` images to USB drives.
- Preserve partition tables, boot records, filesystems, and unused sectors in IMG backups.
- Show live imaging progress with cancellation support.
- Restrict device selection to USB disks and reject Windows boot/system disks.
- Validate image size and sector alignment before writing.
- Require explicit `ERASE` confirmation for destructive operations.

## Download

Download the latest portable Windows package from [GitHub Releases](https://github.com/satalways/usb-mirror/releases/latest).

Use the ZIP package for normal installation:

1. Download `USB-Mirror-Windows-x64-v1.0.0.zip`.
2. Extract the complete archive to a folder.
3. Run `usb_mirror.exe` from inside that folder.
4. Approve the Windows administrator prompt.

The separately attached EXE is provided for convenience, but it still requires the DLL and `data` files contained in the ZIP package.

## Requirements

- Windows 10 or Windows 11, 64-bit
- A removable USB disk
- Administrator access

## Important safety information

Writing an IMG or ISO image permanently erases every partition and file on the selected USB disk. Confirm the physical disk name and capacity carefully before proceeding.

USB Mirror creates raw `.img` backups. It does not create ISO 9660/UDF files from USB drives; changing an IMG file's extension to `.iso` would not make it a true ISO image.

## Source code

The USB Mirror source repository is maintained privately.
