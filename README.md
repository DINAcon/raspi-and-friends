# raspi-and-friends
HACKnight project at DINAcon 2024

The group in the AULA Hacknight is working on the [Souveräne Mini-Cloud](https://hacknight.dinacon.ch/project/85)
with a bunch of Raspberry Pi.

## Wifi

SSID: AULAthenet
Password: inter-nett
## Setup Raspi

## Tom

Hostname: raspberry-tom
IP: 192.168.102.136

Username: tom
Password: dinacon

## Mischa

Hostname: raspberry-mischa
IP: 192.168.102.151

Username: mischa
Password: dinacon

SSH: `ssh tom@192.168.102.136 `
### Foss

Hostname: foss (.local)

Username: janikvonrotz
Password: janikvonrotz

SSH: Enabled
SSH-Login: Password

ssh: `ssh janikvonrotz@`

## Setup K3S

Link: <https://docs.k3s.io/quick-start>

In the terminal of your laptop:

```bash
curl -sfL https://get.k3s.io | K3S_TOKEN=dinacon sh -
```

SSH to the rasperry pi.

Enable cgroup v2: <https://maxdon.tech/posts/k3s-raspberry-pi/>

```bash
echo ' cgroup_memory=1 cgroup_enable=memory' | sudo tee -a /boot/firmware/cmdline.txt
sudo reboot
```

Setup worker:

```bash
curl -sfL https://get.k3s.io | K3S_URL=https://HOST_IP_ADDRESS:6443 K3S_TOKEN=dinacon sh -
```

Check if node is ready on your laptop.

```bash
k3s kubectl get nodes
```
