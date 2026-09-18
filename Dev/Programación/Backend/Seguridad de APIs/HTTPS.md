**HTTPS (HyperText Transfer Protocol Secure)** es la versión segura de HTTP. Utiliza **TLS (Transport Layer Security)**, un protocolo que establece reglas para proteger la comunicación entre el cliente y el servidor.

Su objetivo es proteger la información que se transmite por la red.

---

## TLS

**TLS (Transport Layer Security)** es un **protocolo de comunicación** que protege los datos transmitidos entre un cliente y un servidor.

Proporciona principalmente:

- **Cifrado:** protege los datos para que terceros no puedan leerlos durante la transmisión.
    
- **Autenticación del servidor:** permite verificar que el servidor corresponde al dominio con el que se está estableciendo la conexión.
    
- **Integridad:** permite detectar si los datos fueron modificados durante la transmisión.
    

> **SSL** es el nombre de una tecnología anterior. Actualmente se utiliza TLS, aunque todavía es común hablar de "certificados SSL" como nombre genérico.

---

## Certificados digitales

Un **certificado digital** es un documento electrónico que vincula la identidad de un **dominio** con una **clave pública**.

Por ejemplo, un certificado puede indicar que una determinada clave pública corresponde a:

```text
api.ejemplo.com
```

El certificado permite que el cliente pueda verificar la identidad del servidor durante una conexión HTTPS.

### Autoridades certificadoras

Una **Autoridad Certificadora (CA)** es una entidad que emite certificados digitales en los que los navegadores pueden confiar.

**Let's Encrypt** es una Autoridad Certificadora que emite certificados TLS de forma gratuita.

Para obtener un certificado para un dominio, se debe demostrar que se tiene **control sobre ese dominio**.

> El certificado no acredita la propiedad legal del dominio ni garantiza que todos sus recursos sean seguros. Acredita que quien solicita el certificado pudo demostrar control sobre el dominio.

---

## HSTS

**HSTS (HTTP Strict Transport Security)** es una política de seguridad que indica al navegador que debe utilizar **HTTPS** para comunicarse con un sitio, evitando conexiones mediante HTTP.

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

- Utilizar certificados TLS válidos.
    
- Utilizar certificados emitidos por **Autoridades Certificadoras confiables**, como Let's Encrypt.
    
- Implementar **HSTS**.
    
- Redirigir las conexiones HTTP a HTTPS.
    
- Utilizar **TLS 1.2 o superior**.
    

> El código de implementación con `fs`, `readFileSync()` y `https.createServer()` se puede estudiar aparte cuando se hayan visto esos conceptos de Node.js.