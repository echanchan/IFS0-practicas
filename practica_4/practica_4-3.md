# 🧪 Guía de Laboratorio - Parte 3

# Implementación de Consolas de Administración Gráfica: **Cockpit y Webmin**

----------

# 🎯 Objetivo de la práctica

Complementar la administración CLI de RAID y servicios Linux con herramientas de gestión gráfica vía navegador, permitiendo:

-   Supervisar arreglos RAID (`mdadm`)    
-   Monitorear CPU, RAM, red y almacenamiento    
-   Gestionar servicios del sistema    
-   Evaluar superficie de exposición y seguridad administrativa    

----------

# 🛰️ PARTE I – Instalación y Configuración de Cockpit

## 🔹 1. Instalación del paquete base

```bash
sudo apt update
sudo apt install cockpit -y
```

### 📘 Explicación de los comandos

|Comando|¿Qué hace?|
|----|----|
|`apt update`|Actualiza índice de repositorios|
|`apt install cockpit`|Instala servicio web de administración|
|`-y`|Acepta instalación automáticamente|

### 📌 ¿Qué es Cockpit?

Cockpit es una consola web nativa para administración de servidores Linux.  
Funciona como servicio `systemd` y escucha por defecto en el **puerto 9090**.

----------

## 🔹 2. Habilitar el servicio

```bash
sudo systemctl enable --now cockpit.socket
```

### 📘 Desglose

|Parámetro|Significado|
|----|----|
|`systemctl`|Administra servicios systemd|
|`enable`|Habilita inicio automático al arrancar|
|`--now`|Inicia el servicio inmediatamente|
|`cockpit.socket`|Servicio socket activado bajo demanda|

👉 Cockpit utiliza activación por socket (no corre constantemente hasta que se conecta un cliente).

----------

## 🔹 3. Acceso Web

```html
https://TU_IP:9090
```

### 🔐 Autenticación

Utiliza usuario local del sistema.

----------

## 🔹 4. Habilitar módulo de almacenamiento (RAID)

Si no aparece la pestaña **Storage**:

```bash
sudo apt install cockpit-storaged -y
```

### 📘 ¿Qué hace?

Instala integración con:

-   `udisks2`    
-   `mdadm`    
-   Gestión de volúmenes y RAID    

----------

# 🛠️ PARTE II – Instalación y Configuración de Webmin

## 🔹 1. Agregar repositorio oficial

```bash
curl -o setup-repos.sh https://raw.githubusercontent.com/webmin/webmin/master/setup-repos.sh
sudo sh setup-repos.sh
```

### 📘 Explicación

|Comando|Función|
|---|---|
|`curl`|Descarga archivo desde internet|
|`-o`|Guarda con nombre específico|
|`sh setup-repos.sh`|Ejecuta script bash|

👉 El script agrega repositorio APT oficial de Webmin.

----------

## 🔹 2. Instalar Webmin

```bash
sudo apt install webmin --install-recommends -y
```

### 📘 Parámetros

|Opción|Significado|
|---|---|
|`--install-recommends`|Instala paquetes sugeridos adicionales|

Webmin escucha en el **puerto 10000**.

----------

## 🔹 3. Acceso

```html
https://TU_IP:10000
```

### 📍 Navegación RAID

Hardware → Linux RAID

----------

# 🔐 PARTE III – Configuración del Firewall (UFW)

----------

## 🔹 Abrir puertos necesarios

```bash
sudo ufw allow 9090/tcp
sudo ufw allow 10000/tcp
sudo ufw reload
```

### 📘 Explicación

|Comando|Función|
|---|---|
|`ufw allow`|Permite tráfico entrante|
|`9090/tcp`|Puerto Cockpit|
|`10000/tcp`|Puerto Webmin|
|`reload`|Aplica cambios|

----------

# 🛡️ Consideraciones de Seguridad

|Herramienta|Seguridad por defecto|Nivel de exposición|
|---|---|---|
|Cockpit|Usa PAM y systemd|Baja|
|Webmin|Panel amplio con módulos|Media-Alta

----------

# 🧪 Verificación Técnica

Comprobar que servicios estén activos:

```bash
sudo systemctl status cockpit
sudo systemctl status webmin
```

Ver puertos abiertos:

```bash
sudo ss -tulnp | grep -E "9090|10000"
```

----------

# 🛑 Limpieza (Opcional)

Desinstalar si se desea revertir práctica:

```bash
sudo apt remove cockpit webmin -y
sudo ufw delete allow 9090/tcp
sudo ufw delete allow 10000/tcp
```
