```
~/win11 > qemu-system-x86_64 -m 8G -smp 4 -enable-kvm -cpu host -hda windows11.img -cdrom /home/antivenom/Downloads/virtio-win-0.1.285.iso -boot d -net nic -net user -device virtio-balloon-pci -device virtio-serial-pci -device virtio-rng-pci 
qemu-system-x86_64: Could not access KVM kernel module: No such file or directory
qemu-system-x86_64: failed to initialize kvm: No such file or directory
~/win11 > sudo dmesg | grep -i kvm                                                                                                                            01:19:44 PM
~/win11 > sudo modprobe kvm_intel                                                                                                                     err 0|1 01:20:51 PM
~/win11 > ls -l /dev/kvm                                                                                                                                      01:21:05 PM
crw-rw----+ 1 root kvm 10, 232 Jan  1 13:21 /dev/kvm
~/win11 >                                                                                                                                                     01:21:14 PM



```

