# Setup HomeAsistant with Raspbian

## Raspbian

### Download and install Raspbian
Check out the [official docummentation](https://www.raspberrypi.org/downloads/raspbian/)

### Configure Raspbian

```bash
sudo raspi-config
```

### Install pre-requisites

```bash
sudo -s
apt-get upgrade
apt-get update
apt-get install -y bash jq curl avahi-daemon dbus network-manager apparmor-utils apt-transport-https 
apt-get install -y ca-certificates software-properties-common
```

## Docker

### Download and install Docker

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
systemctl enable --now docker
```

## Hass.io

### Download and install Hass.io

```bash
curl -sL https://raw.githubusercontent.com/home-assistant/hassio-installer/master/hassio_install.sh | bash -s -- -m raspberrypi3
```

## Portainer

### Download and install Portainer

```bash
docker pull portainer/portainer
docker run --restart=always -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer
```

### Check if Portainer is running

```bash
docker ps
```

You should see three containers - portainer, homeassistant and hass-io-supervisor.

### Access Hass.io and Portainer

* Hass.io - http://localhost:8123
* Portainer - http://localhost:9000
