# Parte 3

A continuación se va a mostrar el análisis de algunos certificados de diferentes páginas web. Este análisis va a estar basado en los resultados del servicio SSL Labs.

## Gmail

Una vez introducida la URL de la web de Gmail en SSL Labs, puede verse que el resultado del certificado es B.

![gmail](/img/sslgmail.png)

Si accedemos a los detalles, puede verse un resumen del análisis, en el que básicamente explica que el certificado es seguro pero ha sido calificado con la B ya que es compatible con TLS 1.0 y 1.1, que son versiones más antiguas lo que puede desencadenar en más vulnerabilidades.

![gmail2](/img/sslgmail2.png)

## GifMaker

Al acceder a la web, podemos ver un error en el certificado referente a la fecha.

![gifmaker](/img/gifmaker.png)

Una vez terminado el análisis de SSL Labs, puede verse que el resultado es T, lo que significa que no es seguro. Esto se debe a que realmente el certificado ya ha expirado. Si el certificado siguiera vigente, la puntuación sería B.

![gifmaker2](/img/gifmaker2.png)

## api.s1.tetrapak

Al acceder a la web puede observarse un error en el certificado referente a la autoridad.

![api](/img/api.png)

Al analizar los resultados de SSL Labs, puede verse que el resultado obtenido es T, lo que significa que este certificado no es seguro. La razón es porque no es confiable. Esto puede deberse a una mala configuración, a que el certificado no es válido o que la autoridad de certificación es desconocida. Además de esto, la mayoría de navegadores no confían en el certificado de esta página.

![api2](/img/api2.png)

## pinning-test.badssl

Al acceder a la web puede observarse un error en el certificado referente a las claves.

![api2](/img/badssl.png)

Al analizar el certificado con SSL Labs, el resultado ha sido B. Aparentemente, el error más destacable es que es compatible con TLS 1.0 y 1.1, lo que puede desencadenar en que los atacantes descubran vulnerabilidades de estas versiones más antiguas.

![api2](/img/badssl2.png)
