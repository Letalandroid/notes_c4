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