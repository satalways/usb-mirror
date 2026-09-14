<p align="center">
  <img src="assets/usb_mirror.png" alt="USB Mirror icon" width="160">
</p>

# USB Mirror

USB Mirror is a Windows desktop utility for creating, mounting, and restoring USB-drive images.

## Features

- Create a byte-for-byte `.img` backup of a USB drive.
- Create a fixed `.vhd` backup that Windows can mount and browse.
- Export files from a single mounted USB volume to a Windows-mountable UDF `.iso` archive.
- Write `.img`, fixed `.vhd`, and compatible hybrid `.iso` images to USB drives.
- Preserve partition tables, boot records, filesystems, and unused sectors in IMG backups.
- Validate completed backups before assigning their final filename.
- Show live imaging progress with cancellation support.
- Show continuous progress while Windows prepares USB files and writes an ISO.
- Show the live percentage in the Windows title, taskbar progress bar, and taskbar icon badge.
- Show an immediate native splash while the application runtime loads.
- Restrict device selection to USB disks and reject Windows boot/system disks.
- Validate image size and sector alignment before writing.
- Require explicit `ERASE` confirmation for destructive operations.
- Provide detailed failures with the operation stage, byte offset, technical information, and a diagnostic log.
- Lock USB volumes for reliable raw writes, then refresh restored volumes and
  assign drive letters when Windows supports their filesystems.

## Download

Download the latest Windows packages from [GitHub Releases](https://github.com/satalways/usb-mirror/releases/latest).

For a normal installation, download `USB-Mirror-Setup-v1.4.0.exe`. The installer includes the complete application, creates shortcuts, and provides uninstall support.

For portable use:

1. Download `USB-Mirror-Windows-x64-v1.4.0.zip`.
2. Extract the complete archive to a folder.
3. Run `usb_mirror.exe` from inside that folder.
4. Approve the Windows administrator prompt.

Do not separate `usb_mirror.exe` from the DLL and `data` files included in the installed or portable package.

The current packages are not code-signed, so Windows may display an **Unknown publisher** or SmartScreen warning. Verify the SHA-256 hashes shown in the release notes before running a downloaded package.

## Requirements

- Windows 10 or Windows 11, 64-bit
- A removable USB disk
- Administrator access

## Important safety information

Writing an IMG, VHD, or ISO image permanently erases every partition and file on the selected USB disk. Confirm the physical disk name and capacity carefully before proceeding.

IMG and VHD are complete disk backups. ISO export is a file-level archive from one mounted USB volume: it does not preserve the partition table, unused sectors, filesystem metadata, or arbitrary boot configuration. Changing an IMG file's extension to `.iso` does not convert it.

## Version history

### Version 1.4.0

- Added exclusive USB-volume locking to prevent Windows from rejecting raw
  image writes at byte offset zero.
- Added a restore-success alert and automatic storage refresh and drive-letter
  assignment for visible Windows-supported volumes.
- Added an immediate native Windows splash so launch feedback appears before
  the Flutter runtime finishes loading.
- Added continuous ISO preparation progress instead of leaving long USB
  staging operations at zero percent.
- Added distinct ISO scanning, preparation, filesystem building, writing, and
  verification statuses.
- Fixed Unicode status corruption and decoding failures between Windows
  PowerShell and the application.
- Excluded protected Windows maintenance folders such as `System Volume
  Information` and `$RECYCLE.BIN` from file-oriented ISO exports.

### Version 1.3.0

- Added Windows-mountable fixed VHD backup and validated VHD-to-USB restoration.
- Added Windows-mountable UDF ISO export for USB disks with one mounted volume.
- Added a branded startup splash screen.
- Added taskbar progress, percentage icon badges, and completion/error states.
- Added a success alert with the verified output path.
- Improved physical-disk reads and writes with precise byte-offset diagnostics and retries for transient I/O errors.
- Added partial-file creation and exact-size validation so failed backups cannot appear complete.
- Added a proper Windows installer alongside the complete portable ZIP package.

### Version 1.2.1

- Uses a fixed 920 × 640 application window sized for the working interface.
- Centers the window when the application starts.
- Disables resizing and maximizing to prevent awkward empty space or layout changes.

### Version 1.2.0

- Shows live imaging percentage in the native Windows title, such as `USB Mirror — 47%`.
- Shows `Complete`, `Failed`, or `Canceled` in the title when processing ends.
- Makes progress visible in Alt+Tab and the Windows taskbar preview while using another application.

### Version 1.1.1

- Fixed failures on the final raw-disk read when USB capacity is not an exact multiple of the copy buffer size.
- Added persistent, selectable error details showing the failed processing stage and Windows exception.
- Added diagnostic logs under `%LOCALAPPDATA%\\USB Mirror\\logs`.
- Added checks for insufficient destination space and attempts to save an image onto the USB being backed up.

### Version 1.1.0

- Added an About USB Mirror dialog.
- Displays the installed application version and build number.
- Added a direct link to this public repository for downloads, release notes, and documentation.

### Version 1.0.0

- Initial Windows release.
- Added raw USB-to-IMG backup and IMG/ISO-to-USB restoration.
- Added USB-only device checks, destructive-write confirmation, progress reporting, cancellation, and administrator elevation.

## Source code

The USB Mirror source repository is maintained privately.
