**HTTPS (HyperText Transfer Protocol Secure)** es la versión segura de HTTP. Utiliza **TLS (Transport Layer Security)** para proteger la comunicación entre el cliente y el servidor.

Su objetivo es proteger la información que se transmite por la red.

---

## TLS

**TLS (Transport Layer Security)** es un **protocolo de comunicación** que establece reglas para proteger los datos transmitidos entre un cliente y un servidor.

Proporciona principalmente:

- **Cifrado:** protege los datos para que terceros no puedan leerlos durante la transmisión.
- **Autenticación del servidor:** permite verificar que el servidor corresponde al dominio con el que se está estableciendo la conexión.
- **Integridad:** permite detectar si los datos fueron modificados durante la transmisión.

> **SSL** es una tecnología anterior. Actualmente se utiliza TLS, aunque todavía es común hablar de "SSL/TLS".

---

## Certificados digitales

Un **certificado digital** es un documento electrónico que vincula la identidad de un **dominio** con una **clave pública**.

Por ejemplo:

```text
api.ejemplo.com
       ↓
certificado digital
       ↓
clave pública
```

El certificado permite que el cliente pueda verificar que el servidor corresponde al dominio con el que está estableciendo la conexión HTTPS.

---

### Autoridades certificadoras

Una **Autoridad Certificadora (CA)** es una entidad que emite certificados digitales en los que los navegadores pueden confiar.
**Let's Encrypt** es una Autoridad Certificadora que emite certificados TLS de forma gratuita.
Para obtener un certificado, quien lo solicita debe demostrar que tiene **control sobre el dominio**.

---

## Implementación

Para utilizar HTTPS, el servidor necesita principalmente:

1. Un **certificado digital** para el dominio.
2. Una **clave privada** asociada a ese certificado.
3. Configurar el servidor para utilizar TLS.

**Conceptualmente**:

```text
Certificado + Clave privada
             ↓
       Servidor HTTPS
             ↓
       Puerto 443
             ↓
         Cliente
```


> [!ACLARACIÓN]
> Certificado y clave privada son cosas distintas, pero están relacionadas.
> 
> ```
> CERTIFICADO
> → contiene información del dominio + clave pública
> 
> CLAVE PRIVADA
> → pertenece al servidor y debe mantenerse secreta
> ```
> 
> Ambas se utilizan juntas durante TLS.
> 
> ##### Entonces, ¿por qué aparecen las dos en el ejemplo?
> 
> Porque TLS utiliza un par de claves:
> 
> ```
> Clave pública  → puede compartirse
> Clave privada  → debe mantenerse secreta
> ```
> 
> El certificado contiene la **clave pública** y la identidad del dominio.
> 
> La **clave privada** queda guardada en el servidor.
> 
> No es:
> 
> > certificado + contraseña para acceder al certificado
> 
> Es:
> 
> > **certificado que identifica al dominio + clave privada que posee el servidor**
> 
> 


Por ejemplo, en Node.js se puede crear un servidor HTTPS indicando el certificado y la clave privada:

```js
const https = require('https');
const fs = require('fs'); 

const options = {
  key: fs.readFileSync('private-key.pem'),      // Lee la clave privada
  cert: fs.readFileSync('certificate.pem')      // Lee el certificado
};

https.createServer(options, app).listen(443, () => {
  console.log('Servidor HTTPS ejecutándose en el puerto 443');
});
```

- `https` → permite crear un servidor HTTPS.
- `fs` → permite trabajar con archivos.

- `options` → reúne la clave y el certificado.
- `key` → contiene la **clave privada** del servidor.
- `cert` → contiene el **certificado digital** del dominio.
- `readFileSync()` → lee el archivo.

- `https.createServer()` → crea el servidor HTTPS usando esa configuración.
- `app` → aplicación que atenderá las solicitudes.
- `listen(443)` → hace que el servidor escuche en el **puerto 443**, estándar de HTTPS.

- `=>` → función flecha que se ejecuta cuando el servidor empieza a escuchar.

> La lectura de los archivos que contienen el certificado y la clave privada (`fs.readFileSync`) corresponde a conceptos de manejo de archivos de Node.js y puede estudiarse por separado.

---

## HSTS

**HSTS (HTTP Strict Transport Security)** es una política de seguridad que indica al navegador que debe utilizar HTTPS para comunicarse con un sitio.

Esto ayuda a evitar conexiones mediante HTTP.

```text
HTTP  → no utilizar
HTTPS → utilizar
```

---

## Versiones de TLS

TLS tiene diferentes versiones. Las versiones antiguas fueron quedando obsoletas por problemas de seguridad.

Por eso se recomienda utilizar **TLS 1.2 o superior**, como TLS 1.3.

---

## Buenas prácticas

- Utilizar **certificados TLS válidos** y vigentes.
- Utilizar certificados emitidos por **Autoridades Certificadoras confiables**, como Let's Encrypt.
- Utilizar **TLS 1.2 o superior**.
- Implementar **HSTS** para reforzar el uso de HTTPS.
- **Redirigir HTTP a HTTPS** para evitar que los clientes continúen utilizando conexiones no seguras.
- Mantener los certificados **actualizados y renovados** antes de su vencimiento.

---


