# KILLER

Ini adalah [Marzban](https://github.com/Gozargah/Marzban) yang sudah saya tambahkan nginx untuk konfigurasi koneksi WebSocket dan XHTTP pada single port. </br>
WebSocket sudah support untuk 443 TLS, 80 HTTP dan Wildcard path, contoh /enter-your-custom-path/trojan </br>
XHTTP sudah support untuk 443 TLS Quic </br>

Disclaimer: Proyek ini hanya untuk pembelajaran dan komunikasi pribadi, mohon jangan menggunakannya untuk tujuan ilegal. </br>
Credit aplikasi full to [Gozargah Marzban](https://github.com/Gozargah), saya hanya edit sedikit untuk instalasi sederhana bagi pemula . </br>

# Special Thanks to
- [Gozargah](https://github.com/Gozargah/Marzban)
- [hamid-gh98](https://github.com/hamid-gh98)
- [x0sina](https://github.com/x0sina/marzban-sub)

# List Protocol yang support
- VLess
- VMess
- Trojan

# Yang harus dipersiapkan
- VPS dengan minimal spek 1 Core 1 GB ram
- Domain yang sudah di pointing ke CloudFlare
- Pemahaman dasar perintah Linux

# Sistem VM yang dapat digunakan
- Debian 11 </br>
- Debian 12 [**RECOMMENDED**] </br>
- Ubuntu 20.04 </br>

# Instalasi
  ```html
 apt-get update && apt-get upgrade -y && apt dist-upgrade -y && update-grub && reboot
 ```
Pastikan anda sudah login sebagai root sebelum menjalankan perintah dibawah
 ```html

Ubuntu

 wget https://raw.githubusercontent.com/wibusantun/Killer/main/ubuntu.sh && chmod +x ubuntu.sh && ./ubuntu.sh

Debian

wget https://raw.githubusercontent.com/wibusantun/Killer/main/debian.sh && chmod +x debian.sh && ./debian.sh
 ```

Buka panel Marzban dengan mengunjungi https://domainmu/dashboard <br>

Jika ingin mengubah konfigurasi env variable 
```html
marzban edit-env
 ```
Perintah Restart service Marzban 
```html
marzban restart
 ```
Perintah Cek Logs service Marzban 
```html
marzban logs
 ```
Perintah ganti Core Xray marzban
```html
marzban core-update
 ```
Perintah untuk sett backup marzban
```html
 marzban backup-service
 ```
Perintah Cek update service Marzban
```html
marzban update
 ```
Perintah untuk ke Menu Warp
```html
warp
 ```
atau selebih nya bisa cek 
```html
warp --help
 ```

# Cloudflare Sett

Pastikan SSL/TLS Setting pada cloudflare sudah di set menjadi full
![image](https://github.com/GawrAme/MarLing/assets/97426017/3aeedf09-308e-41b0-9640-50e4abb77aa0) </br>

Lalu pada tab **Network** pastikan gRPC dan WebSocket sudah ON 
![image](https://github.com/GawrAme/MarLing/assets/97426017/65d9b413-fda4-478a-99a5-b33d8e5fec3d)



# Setting Host Marzban
 
 Saat masuk ke panel, setting host di menu kanan atas <br>
 ![image](https://github.com/GawrAme/MarLing/assets/97426017/6b96bce7-39c7-4b5c-b01e-8dfdea91cb47) </br>

Lalu ubah variabel {SERVER_IP} dibawah menjadi domain yang sudah di pointing tadi <br>
# CONTOH
![image](https://github.com/GawrAme/MarLing/assets/97426017/191a485c-07a7-4a28-88d3-b66fa403abc7)
</br>

# Setting WIRE WARP
The routing rules are as follows:

        	   {
                "type":"field",
                "outboundTag":"WARP-socks5-v6",
                "domain":[
                    "domain:ip.sb",
                    "domain:test-ipv6.com",
                    "domain:ip6.me",
                    "geosite:openai"
                ]
            },

For outbound writing, add an outbound setting of the freedom protocol and then go through the proxy:


       {
            "tag":"warp",
            "protocol":"socks",
            "settings":{
                "servers":[
                    {
                        "address":"127.0.0.1",
                        "port":40000
                    }
                ]
            }
        },
        {
            "tag":"WARP-socks5-v6",
            "protocol":"freedom",
            "settings":{
                "domainStrategy":"UseIPv6"
            },
            "proxySettings":{
                "tag":"warp"
            }
        }

