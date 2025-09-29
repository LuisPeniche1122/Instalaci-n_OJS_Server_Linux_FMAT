# Instalación_OJS_Server_Linux_FMAT

# Guía para instalar OJS en un servidor Linux (Ubuntu Server 24.04)

## Requisitos previos
Antes de comenzar, asegúrate de contar con:

- Un servidor con **Ubuntu Server 24.04** o similar.  
- Acceso a la terminal con permisos de **usuario administrador (sudo)**.  
- Conexión a internet (para descargar paquetes).  

### Componentes necesarios
- **Apache** → Servidor web que permitirá acceder a OJS desde el navegador.  
- **PHP** → Lenguaje en el que está desarrollado OJS.  
- **MariaDB** → Sistema de base de datos donde se almacenará la información de la revista.  

⚠️ Antes de instalar, actualiza el sistema:
```bash
sudo apt update && sudo apt upgrade -y
````

---

## Paso 1: Instalación de los requisitos

### 1.1 Instalar Apache

Instala Apache:

```bash
sudo apt install apache2 -y
```

Arranca Apache y configúralo para que inicie automáticamente:

```bash
sudo systemctl enable --now apache2
```

Verifica que Apache esté activo:

```bash
sudo systemctl status apache2 --no-pager
```

Habilita el módulo `rewrite`:

```bash
sudo a2enmod rewrite
sudo systemctl restart apache2
```

---

### 1.2 Instalar PHP y extensiones necesarias

Instala PHP y las extensiones necesarias:

```bash
sudo apt install php libapache2-mod-php php-mysql php-gd php-xml php-mbstring php-curl php-zip unzip wget tar -y
```

Verifica la versión de PHP:

```bash
php -v
```

---

### 1.3 Instalar y configurar MariaDB

Instala MariaDB:

```bash
sudo apt install mariadb-server mariadb-client -y
```

Arranca y habilita el servicio:

```bash
sudo systemctl enable --now mariadb
```

Ejecuta el asistente de configuración segura:

```bash
sudo mysql_secure_installation
```

Se recomienda responder lo siguiente:

* **Enter current password for root** → Enter
* **Switch to unix_socket authentication?** → N
* **Change the root password?** → Y (elige una contraseña segura)
* **Remove anonymous users?** → Y
* **Disallow root login remotely?** → Y
* **Remove test database?** → Y
* **Reload privilege tables now?** → Y

---

## Paso 2: Crear base de datos para OJS

Ingresa a MariaDB como administrador:

```bash
sudo mysql -u root -p
```

Crea la base de datos y el usuario (reemplaza el ojsuser y TuPasswordSeguro123! por los datos que desees):

```sql
CREATE DATABASE ojs;
CREATE USER 'ojsuser'@'localhost' IDENTIFIED BY 'TuPasswordSeguro123!';
GRANT ALL PRIVILEGES ON ojs.* TO 'ojsuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

---

## Paso 3: Descargar e instalar OJS

Dirígete a la carpeta de Apache:

```bash
cd /var/www/html
```

Descarga y descomprime OJS (ajusta la versión a la más reciente):

```bash
sudo wget https://pkp.sfu.ca/ojs/download/ojs-3.3.0-16.tar.gz
sudo tar -xvzf ojs-3.3.0-16.tar.gz
sudo mv ojs-3.3.0-16 ojs
```

---

## Paso 4: Ajustar permisos

Otorga permisos a Apache sobre los archivos:

```bash
sudo chown -R www-data:www-data /var/www/html/ojs
sudo chmod -R 755 /var/www/html/ojs
```

---

## Paso 5: Crear carpeta de archivos privados

Crea un directorio seguro para almacenar artículos y PDFs:

```bash
sudo mkdir /var/www/ojs_files
sudo chown -R www-data:www-data /var/www/ojs_files
```

---

## Paso 6: Configurar Apache para OJS

Crea un archivo de configuración:

```bash
sudo nano /etc/apache2/sites-available/ojs.conf
```

Agrega el siguiente contenido (ajusta `ServerName` con tu dominio o IP):

```apache
<VirtualHost *:80>
    ServerName tu_dominio_o_ip
    DocumentRoot /var/www/html/ojs

    <Directory /var/www/html/ojs>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

Activa el sitio y reinicia Apache:

```bash
sudo a2ensite ojs.conf
sudo a2enmod rewrite
sudo systemctl reload apache2
```

---

## Paso 7: Completar instalación desde el navegador

Abre en tu navegador:

```
http://IP_DEL_SERVIDOR/ojs
```

En el instalador proporciona:

* Directorio de archivos: `/var/www/ojs_files`
* Base de datos: `ojs`
* Usuario de base de datos: `ojsuser`
* Contraseña: la definida en el paso 2

Al finalizar, podrás acceder como administrador y empezar a configurar tu revista.
