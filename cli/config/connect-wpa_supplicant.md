Guía para conectarse a internet mediante wpa_supplicant.
--

## 1. Identificar el dispositio de red

Comando que muestra los dispositivos y su configuración.

```bash
sudo iwconfig
```

## 2. Realizar escaneo de redes disponibles

Comando para mostrar las redes disponibles.
**Reemplazar *dispositivo.red* con tu dispositivo.** (regularmente es wlp3s0 o wlo1)

```bash
sudo iwlist *dispositivo-red* scan | grep ESSID
```

## 3. Agregar la red al archivo de configuración.

**Reemplazar *ESSID* y *contraseña* con el nombre de la red sin comillas, y su contraseña.**

```bash
sudo wpa_passphrase *ESSDI* *contraseña* | sudo tee /etc/wpa_supplicant.conf
```

## 4. Solicitar la conexión.

**Reemplazar *dispositivo.red* con tu dispositivo.** (regularmente es wlp3s0 o wlo1)

```bash
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i *dispositivo-red*
```

## 5. Generar IP y hosteo mediante DHCP

**Reemplazar *dispositivo.red* con tu dispositivo.** (regularmente es wlp3s0 o wlo1)

```bash
sudo dhclient *dispositivo-red*
```
