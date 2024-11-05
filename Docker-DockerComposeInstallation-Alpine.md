# Installation Docker-DockerCompose On Alpine Linux
## 1. Network Configuration(Opsiyonel, Alpine setup yapılmış ise gerek yok.)

```bash
vi /etc/network/interfaces
```
```bash
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static (statik ip vermek için)
    #address 192.168.1.100   # IP adresini buraya gir
    #netmask 255.255.255.0   # Ağ maskesini buraya gir
    #gateway 192.168.1.1     # Varsayılan geçidi buraya gir
```
## 2. Network Service Restart(Opsiyonel, Alpine setup yapılmış ise gerek yok.)

```bash
rc-service networking restart
```
## 3. Change Hostname From ETC File(Opsiyonel, Alpine setup yapılmış ise gerek yok.)
```bash
vi /etc/hostname
#my-new-hostname
```
## 4. Hostname Değişikliğini Hemen Uygula(Opsiyonel, Alpine setup yapılmış ise gerek yok.)
```bash
hostname my-new-hostname
```
## 5. Root Kullanıcısı İçin Şifre Oluşturma(Opsiyonel, Alpine setup yapılmış ise gerek yok.)
```bash
passwd
```
## 6. OpenSSH Kurulumu(Opsiyonel, Alpine setup yapılmış ise gerek yok.)
```bash
apk update
apk add openssh
  ```
### SSH Servisini Başlatma ve Otomatik Başlangıca Ekleme
```bash
rc-service sshd start
```
### SSH servisinin Yeniden Başlatmada Otomatik Olarak Çalışması İçin:
```bash
rc-update add sshd
```
### SSHD Config Değiştirme
```bash
vi /etc/ssh/sshd_config
```
```bash
PermitRootLogin yes #(başındaki # işaretini kaldır)
```
```bash
rc-service sshd restart
```
## 7. Docker Install
### Community Deposunu Etkinleştirin
```bash
vi /etc/apk/repositories
```
### Dosya İçeriğini Aşağıdaki gibi Değiştir
```bash
https://dl-cdn.alpinelinux.org/alpine/v3.20/main
https://dl-cdn.alpinelinux.org/alpine/v3.20/community
#media/cdrom/apks
```
```bash
apk update
apk add docker
```
### Docker'ı Başlatın ve Her Yeniden Başlatmada Otomatik Olarak Çalışması İçin Etkinleştirin
```bash
rc-service docker start
rc-update add docker
```
## 12. Docker Compose Intall
```bash
apk add docker-compose
```
