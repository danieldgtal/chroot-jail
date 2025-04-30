cat <<EOF > README.md
# chroot-lab

Minimal chroot jail for filesystem isolation demonstration. Created as part of daily cloud learning practice.

EOF

cat <<'EOF' > chroot-lab.sh
#!/bin/bash
set -e

JAIL=/opt/myjail
mkdir -p $JAIL/{bin,lib,lib64}
cp /bin/bash $JAIL/bin/
cp /lib/x86_64-linux-gnu/libtinfo.so.6 $JAIL/lib/
cp /lib/x86_64-linux-gnu/libc.so.6 $JAIL/lib/
cp /lib64/ld-linux-x86-64.so.2 $JAIL/lib64/

echo "To enter the jail: sudo chroot /opt/myjail /bin/bash"
EOF

chmod +x chroot-lab.sh

