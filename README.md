# Zurg + Plex + RealDebrid Guide
This guide would help you install a plex server combined with zurg and ReadDebrid for unlimited storage.
## Requeriments
zurg uses docker in order to run.
### Install Docker and Docker Compose
```bash
sudo pacman -S docker docker-compose
```
Enable the `docker` service
```bash
systemctl start docker.service
```
```bash
systemctl enable docker.service
```
### Install an AUR helper
If you dont already have one, install an AUR Helper.
 * yay:
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay-bin.git && cd yay-bin && makepkg -si
```
 * paru:
```bash
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```
## Installing Zurg
1. Clone the zurg repo `git clone https://github.com/debridmediamanager/zurg-testing.git`
2. `cd zurg-testing`
3. `sudo nano config.yml`
4. Replace "your token" with your token from the ReadlDebrid [website](https://real-debrid.com/apitoken)
5. `sudo mkdir -p /mnt/zurg`
6. Run `docker compose up -d`
7. `time ls -1R /mnt/zurg` You're done! If you do edits on your config.yml just do `docker compose restart zurg`.

A webdav server is also exposed to your localhost via port `9999`.
