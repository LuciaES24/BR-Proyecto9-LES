# Parte 2

## Configuración servidor y certificado

Realizar los siguientes pasos:

1. Actualizar los paquetes del sistema:
```
    sudo apt update
```
2. Instalar apache2 y openssl:
```
    sudo apt install apache2 openssl
```
Al acceder al servidor para ver la página de prueba se haría con HTTP y se vería lo siguiente:

![apache](/img/apache1.png)


3. Habilitar el módulo ssl:
```
    sudo a2enmod ssl
```
4. Reiniciar apache2:
```
    sudo systemctl restart apache2
```
5. Generar el certificado autofirmado:
```
    sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048
    -keyout /etc/ssl/private/apache-selfsigned.key
    -out /etc/ssl/certs/apache-selfsigned.crt
```

Al ejecutar este comando se deben configurar los datos del certificado, siendo lo más importante el "Common Name", donde debe ponerse el nombre de dominio del servidor o la IP.

6. Modificar el archivo de configuración de apache2:
```
sudo nano /etc/apache2/sites-available/default-ssl.conf
```
La configuración debe quedar parecida a la siguiente:

![cofiguración](/img/apache2.png)

7. Habilitar SSL y reiniciar apache2:
```
sudo a2ensite default-ssl  
sudo systemctl reload apache2
```
8. Configurar el firewall:
```
sudo ufw allow 'Apache Full'
```

Una vez terminada la configuración del certificado, al acceder por HTTPS aparecería lo siguiente:

![https](/img/apache3.png)

Si se accede a los datos del certificado, aparecerá algo parecido a la siguiente imagen:

![certificado](/img/apache4.png)

## Sitio web verificado

Para ver un certificado válido, he accedido a Gmail. Una vez ahí, al comprobar el certificado pone que la web es segura y el certificado es válido, puediendo ver la información del mismo:

![gmail](/img/apache5.png)

## Diferencias

En cuanto a las diferencias entre ambos certificados, además de datos básicos como el nombre común, el periodo de validez y los hashes, si se accede a la pestaña de "Detalles" pueden verse otras diferencias clave.
1. En el apartado de **"Verificado"**, en el que he configurado para el servidor apache2, el número de serie y el emisor son distintos del certificado que utiliza Gmail.
2. En el apartado de **"Tema"**, puede verse que es distinto entre ambos.
3. En el apartado de **"Extensiones"**, mi verificado solo utiliza 3 extensiones y el de Gmail utiliza 10.
4. El **"Valor de Firma de certificados"** también es distinto en ambos certificados.

