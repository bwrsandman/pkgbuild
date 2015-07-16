FROM base/archlinux
RUN printf "[archlinuxfr]\nSigLevel = Never\nServer = http://repo.archlinux.fr/\$arch\n" >> /etc/pacman.conf
RUN pacman -Sy --noconfirm
RUN pacman -S archlinux-keyring --noconfirm
RUN pacman -Su --noconfirm
RUN pacman-db-upgrade
RUN pacman -S sudo yaourt base-devel --noconfirm --needed

RUN useradd user -G wheel
RUN echo "%wheel ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

USER user
COPY PKGBUILD /tmp/
RUN cd /tmp && makepkg --syncdeps --noconfirm
