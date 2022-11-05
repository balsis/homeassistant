# Мой конфиг умного дома

<details>
  <summary>Конфиг:</summary>
  
**Железо**:   Gigabyte Brix GB-BACE-3160 + Zigbee2MQTT (SONOFF Zigbee 3.0 USB Dongle)+ MQTT + Xiaomi Gateway 3;  
**Zigbee2MQTT**: 15 устройств (отопление, выключатели, теплый пол);  
**Xiaomi Gateway 3**: 16 устройств (датчики Xiaomi);  
**Passive BLE**: около 5 устройств;  
**Wifi**: Smartmi Humidifier, Philips Light Bulb, WLED подсветка, камера Tapo С110;  
**ADB**: Amazon Fire 4k max, Sberbox.
</details>  

<details>
  <summary>Общий вид команд для установки Home Assistant Supervised:</summary>
  
```bash
curl https://raw.githubusercontent.com/home-assistant/supervised-installer/master/installer.sh > installer.sh
sudo chmod +x ./installer.sh
sudo bash -x ./installer.sh -s -- -p /home/artur -d $PREFIX/smarthome/hassio
```
Частный конфиг для Ubuntu:

```bash
curl https://raw.githubusercontent.com/home-assistant/supervised-installer/master/installer.sh | bash -x ./installer.sh -s -- -p /home/artur/smarthome -d $PREFIX/hassio
```
Частный конфиг Debian 10 (в настоящее время работает):
```bash
curl -sL https://raw.githubusercontent.com/home-assistant/supervised-installer/master/installer.sh | bash -s -  -d /home/artur/smarthome/hassio
```

</details> 

<details>
  <summary>Интерфейс:</summary>
  
![alt text](https://github.com/balsis/pics/blob/main/Home%20Assistant%20-%20GUI.gif)
</details> 

<details>  
  <summary>Portainer и Zigbee2MQTT:</summary>
  
![alt text](https://github.com/balsis/pics/blob/main/docker.PNG)  
![alt text](https://github.com/balsis/pics/blob/main/z2m.JPG) 

</details> 
 
<details>  
  <summary> Удаление и переустановка контейнеров hassio:</summary> 


Остановка сервисов
```
sudo systemctl stop hassio-supervisor.service
sudo systemctl stop hassio-apparmor.service
```
Отключение сервисов
```
sudo systemctl disable hassio-supervisor.service
sudo systemctl disable hassio-apparmor.service
```

Удаление сервисов
```
sudo rm -rf /etc/systemd/system/hassio-supervisor.service
sudo rm -rf /etc/systemd/system/hassio-apparmor.service
```
Удаление всех файлов и папок
```
sudo rm -rf /usr/sbin/hassio-supervisor
sudo rm -rf /usr/sbin/hassio-apparmor
sudo rm -rf /usr/share/hassio/
```
</details> 
 
Шпаргалки:  
[Настройка NUT для IPPON 650 UPS с USB в Debian 10](https://github.com/balsis/homeassistant/blob/main/nut.md)


