# Zurg + Plex + RealDebrid Guide
This guide would help you install a plex server combined with zurg and ReadDebrid for unlimited storage.
## Requeriments
zurg uses docker in order to run.
### Install Docker and Docker Compose
```bash
sudo pacman -S docker docker-compose
```
Enable the `docker` service.
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
6. Run `sudo docker compose up -d`
7. `time ls -1R /mnt/zurg` You're done! If you do edits on your config.yml just do `docker compose restart zurg`.

A webdav server is also exposed to your localhost via port `9999`.
## Installing Plex
Plex is not availible in the arch repo's. Get it from the AUR:
```bash
yay -S plex-media-server
```
Enable the `plexmediaserver` service.
```bash
systemctl start plexmediaserver.service
```
```bash
systemctl enable plexmediaserver.service
```
## Configure Plex
To begin configuring the Plex Media Server, browse to http://localhost:32400/web/.

Follow the onscreen instructionsmmm, until you get to the "Media Library" part.

When you add libraries, choose zurg and then either movies or TV shows.

Also, in plex settings, under online media sources, disable the first 3 under general.
