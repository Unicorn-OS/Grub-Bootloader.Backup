sch: https://www.google.com/search?q=grub-install+failed+to+get+canonical+path+%2Fcow

# Answer:
- https://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow
works!
- tested on Ubuntu 23.10 with Qubes OS also installed. relation: https://github.com/Uni-Key/Qubes.env/blob/main/.graph/Dual%20Boot/readme.md

```
mkdir /mnt/chrootdir
mount /dev/sda1 /mnt/chrootdir
for dir in proc dev sys etc bin sbin var usr lib lib64 tmp; do
    mkdir /mnt/chrootdir/$dir && mount --bind /$dir /mnt/chrootdir/$dir
done
chroot /mnt/chrootdir
grub-install /dev/sda # May not be required
update-grub2
```
