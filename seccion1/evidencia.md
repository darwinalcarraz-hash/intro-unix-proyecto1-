# Section 1: Cryptographic Keys Implementation

## Group Members
* Darwin Alcarraz
* Cayetano Córdova
* Jordan Reyes

## Answers to Section 1
1. LUKS, dm-crypt and the Device Mapper
dm-crypt is the subsystem of the Linux kernel that performs real-time block encryption. LUKS is the header standard that manages keys and metadata; their relationship is that of "administrator" (LUKS) and "executor" (dm-crypt). The Device Mapper acts as a virtual bridge: it creates an intermediate (mapped) device where data is encrypted before touching the physical disk and decrypted before reaching the operating system.
2. Full Encryption
FDE (Full Disk Encryption) encrypts every sector of the disk, including metadata and free space. Its advantages are full system protection (including /tmp and swap) and hiding the directory structure; Its limitations are that it requires a separate unencrypted /boot partition and higher CPU consumption when booting. File encryption acts only on specific folders; Its advantages are flexibility for multiple users and that it does not require disk formatting, but its limitations are that it exposes metadata (names/sizes) and does not protect temporary system files.
3. LVM layers (PV, VG, LV)
LVM organizes storage into three levels: the PV (Physical Volume) is the physical resource (LUKS partition), the VG (Volume Group) is the virtual pool that groups those resources, and the LV (Logical Volume) is the virtual partitions that the user formats and mounts. Compared to traditional partitioning, LVM offers the advantage of hot resizing volumes (without shutting down the server) and the ability to create Snapshots to make consistent backups of the running system.
4. Boot Process
When you power on the VM, the BIOS loads GRUB from the (unencrypted) /boot partition. GRUB loads the Kernel and the initramfs (temporary file system in RAM), which contains the cryptsetup modules. It is at this moment, before mounting the root (/), when the system requests the password to open the LUKS container. Once validated, the kernel scans the LVM within the decrypted volume, activates the logical volumes, and continues with normal OS boot.

## List of Evidences (Installation Steps)
The following 15 screenshots document the Full Disk Encryption (FDE) setup:

### Part 1: Installer and Partitioning
1. **Screenshot 1:** Booting the Debian 13 (Trixie) graphical installer.
2. **Screenshot 2:** Language, location, and keyboard configuration.
3. **Screenshot 4:** Setting the hostname as `debian-[group]`.
4. **Screenshot 4:** Selecting "Guided - use entire disk and set up encrypted LVM".
5. **Screenshot 5:** Selecting the disk for partitioning.
6. **Screenshot 6:** Confirming the scheme for /home, /var, and /tmp partitions.
7. **Screenshot 7:** Configuring the LUKS encryption passphrase (100-bit entropy).

### Part 2: LVM Configuration
8. **Screenshot 8:** Creating the Physical Volume (PV) and Volume Group (VG).
9. **Screenshot 9:** Defining Logical Volumes (LV) for root, swap, and home.
10. **Screenshot 10:** Final summary of the partition table before writing to disk.

### Part 3: Post-Installation Verification
11. **Screenshot 11:** The GRUB bootloader asking for the LUKS passphrase.
12. **Screenshot 12:** Output of the `lsblk` command showing the encrypted tree.
13. **Screenshot 13:** Output of `pvs` and `vgs` showing LVM abstraction layers.
14. **Screenshot 14:** Output of `lvs` showing the status of logical volumes.
15. **Screenshot 15:** Output of `cryptsetup status` confirming active encryption.
