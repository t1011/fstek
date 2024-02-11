необходимо написать плейбук ansible для применения его на множестве хостов rhel 7 посредством файла инвентаря в котором предусмотреть следующее:
1. создать в директории /etc/sysctl.d файл 77-fstek.conf со следующими параметрами и сразу применить их:
kernel.dmesg_restrict=1.
kernel.kptr_restrict=2
net.core.bpf_jit_harden=2
kernel.perf_event_paranoid=3
kernel.kexec_load_disabled=1
kernel.unprivileged_bpf_disabled=1
user.max_user_namespaces=0
vm.unprivileged_userfaultfd=0
dev.tty.ldisc_autoload=0
vm.mmap_min_addr = 4096
kernel.randomize_va_space = 2
kernel.yama.ptrace_scope=3
fs.protected_symlinks=1
fs.protected_hardlinks=1
fs.protected_fifos=2
fs.protected_regular=2
fs.suid_dumpable=0
2. в файл /etc/default/grub корректно добавить следующие параметры:
vsyscall=none
tsx=off
init_on_alloc=1
slab_nomerge
iommu=force
iommu.strict=1
iommu.passthrough=0
mitigations=auto,nosmt
debugfs=no-mount
