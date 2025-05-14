# Encriptar y desencriptar
Para el encriptado y desencriptado usamos herramientas como `openssl` y `sha256sum`

- openssl: Es un kit de herramientas que nos permite encriptar y desencriptar en sha256, sha512, aes-256, entre otros.
- sha256sum: Nos permite comparar un hash y validad la integridad de sus datos.

## Encriptado
```bash
# Enncriptado sin formati ASCII
openssl aes-256-cbc -in letter_to_grandma.txt -out letter.enc

# Enncriptado con formati ASCII (-a)
openssl aes-256-cbc -a -in letter_to_grandma.txt -out letter.enc
```

## Desencriptado
```bash
openssl aes-256-cbc -a -d -in letter.enc -out letter.txt
```

# Crackear zip's
Para encriptar zip es sencillo y recomendable para guardar información sensible, sin embargo, depende de la contraseña que se le ponga a estos archivos, si es una débil, se desencriptaría con `fcrackzip`

#### Zip
```bash
zip -e file.zip file.txt
```

#### Fcrackzip
```bash
fcrackzip -vul 1-8 file1.zip
```

![[Selección_001.png]]

# Whireshark
Nos permite ver el tráfico de nuestra red y dispositivos, asi como las peticiones internas

![[Selección_002.png]]
*Realizamos una conexión por TELNET para poder visualizar las credenciales mediante Whireshark*

`Right Click > Follow > UDP/TCP Stream`

TELNET no tiene un cifrado en comparación a SSH, por ende este sirve mejor para la conexión con dispositivos por la red.

# Generar clave privada y publica (OpenSSL)
Estas claven sirven para mayor seguridad a la hora de compartir o tratar con archivos ya que estas llaves son únicas y no se deben compartir

```bash
# Generar clave pública
openssl genpkey -algorithm RSA -out clave_privada.pem -pkeyopt rsa_keygen_bits:2048
```

![[Selección_003.png]]

```bash
# Generar clave privada
openssl rsa -text -in clave_privada.pem
```

![[Selección_004.png]]

```bash
# Extraer la clave pública  
openssl rsa -pubout -in clave_privada.pem -out clave_publica.pem
```

![[Selección_005.png]]

```bash
# Encriptar un archivo con nuestra clave pública
openssl pkeyutl -encrypt -inkey clave_publica.pem -pubin -in secreto -out secreto.enc
```

![[Selección_006.png]]

```bash
# Desencriptar un archivo con nuestra clave privada
openssl pkeyutl -decrypt -inkey clave_privada.pem -in secreto.enc -out descifrado
```

![[Selección_007.png]]