# OWASP Top 10

El proyecto OWASP Top 10 es una lista de los diez riesgos más críticos para la seguridad de aplicaciones web. Este documento describe cada uno de estos riesgos y sus posibles soluciones.

## Tabla de Contenido

1. [Pérdida de control de acceso](#1-pérdida-de-control-de-acceso)
2. [Fallas criptográficas](#2-fallas-criptográficas)
3. [Inyección](#3-inyección)
4. [Diseño inseguro](#4-diseño-inseguro)
5. [Configuración de seguridad incorrecta](#5-configuración-de-seguridad-incorrecta)
6. [Componentes vulnerables y desactualizados](#6-componentes-vulnerables-y-desactualizados)
7. [Fallas de identificación y autenticación](#7-fallas-de-identificación-y-autenticación)
8. [Falta de visibilidad y monitoreo](#8-falta-de-visibilidad-y-monitoreo)
9. [Gestión inadecuada de la sesión](#9-gestión-inadecuada-de-la-sesión)
10. [Protección insuficiente contra ataques](#10-protección-insuficiente-contra-ataques)

---

## 1. Pérdida de control de acceso

### ⚠️ **Problema**

Los atacantes pueden explotar vulnerabilidades en el control de acceso, como manipular solicitudes para obtener permisos no autorizados (por ejemplo, modificar su rol de "usuario" a "administrador").

### ✅ **Solución**

- Implementar **políticas de control de acceso estricto** en todas las partes de la aplicación.
- Validar roles y permisos en el servidor, no confiar únicamente en el cliente.
- Usar **control de acceso basado en roles (RBAC)** o **control de acceso basado en atributos (ABAC)** para gestionar los permisos de manera robusta.

---

## 2. Fallas criptográficas

### ⚠️ **Problema**

Las contraseñas y otros datos sensibles pueden ser expuestos si no se cifran adecuadamente, o si se usan algoritmos de cifrado obsoletos o débiles.

### ✅ **Solución**

- **Cifrado adecuado** de datos sensibles utilizando algoritmos como **bcrypt**, **argon2** o **PBKDF2** para el almacenamiento seguro de contraseñas.
- **TLS (Transport Layer Security)** debe ser utilizado para cifrar las comunicaciones entre cliente y servidor.
- Asegúrate de que las claves privadas y los datos cifrados se gestionen de manera segura y se actualicen regularmente.

---

## 3. Inyección

### ⚠️ **Problema**

Las inyecciones de código (como SQL, NoSQL, XSS, o comandos del sistema) son vulnerabilidades comunes que permiten a un atacante ejecutar comandos maliciosos en la aplicación. Ejemplo ‘or true --'

### ✅ **Solución**

- **Filtrar y validar** las entradas del usuario para evitar que códigos maliciosos sean procesados por la aplicación.
- Utilizar **consultas parametrizadas** o **ORMs** para proteger contra inyecciones SQL.
- Implementar medidas de **escape** en todas las salidas, especialmente en el contexto de HTML, para prevenir **Cross-Site Scripting (XSS)**.

---

## 4. Diseño inseguro

### ⚠️ **Problema**

Los fallos en el diseño de la arquitectura de seguridad pueden exponer la aplicación a ataques, como la falta de validación de las entradas o control incorrecto del acceso. Revisión de DTOs

### ✅ **Solución**

- **Validar y sanitizar** todas las entradas del usuario en el servidor, especialmente en formularios de autenticación, pagos y comentarios.
- Utilizar **control de acceso granular** para asegurar que los usuarios solo puedan acceder a los recursos a los que están autorizados.
- Considerar la seguridad desde la fase de diseño, implementando prácticas como **principio de menor privilegio**.

---

## 5. Configuración de seguridad incorrecta

### ⚠️ **Problema**

Las configuraciones inseguras, como contraseñas predeterminadas, servicios innecesarios activos o puertos expuestos, dejan la aplicación vulnerable a ataques.

### ✅ **Solución**

- Realizar una **revisión periódica de configuraciones** en servidores, bases de datos y otros servicios.
- **Eliminar servicios innecesarios** y cerrar puertos no utilizados.
- Cambiar todas las **contraseñas predeterminadas** y asegurarse de que todas las configuraciones de seguridad sean adecuadas.

---

## 6. Componentes vulnerables y desactualizados

### ⚠️ **Problema**

Las aplicaciones web a menudo dependen de bibliotecas o componentes de terceros que pueden tener vulnerabilidades conocidas si no se actualizan.

### ✅ **Solución**

- Realizar **auditorías regulares** de las dependencias del proyecto utilizando herramientas como `npm audit` o `Snyk`.
- **Mantener las dependencias actualizadas** y eliminar las que ya no son necesarias.
- Realizar pruebas de seguridad continuas, especialmente cuando se añaden nuevas dependencias.

---

## 7. Fallas de identificación y autenticación

### ⚠️ **Problema**

La falta de una correcta implementación de autenticación puede permitir a los atacantes acceder a las cuentas de usuario o a la administración del sistema. Esto incluye contraseñas débiles o tokens de sesión no gestionados correctamente.

### ✅ **Solución**

- Requerir **contraseñas fuertes** y usar **autenticación multifactor (MFA)** para las cuentas de alto privilegio.
- Asegurarse de que las contraseñas sean **almacenadas de forma segura** (usando hashing con **sal**).
- Implementar la **expiración de sesiones** y revocar el acceso si es necesario.

---

## 8. Falta de visibilidad y monitoreo

### ⚠️ **Problema**

Sin un monitoreo adecuado, es difícil detectar brechas de seguridad o actividades sospechosas en tiempo real, lo que puede llevar a un mayor daño en caso de ataque.

### ✅ **Solución**

- Implementar **monitoreo en tiempo real** para detectar comportamientos anómalos.
- Configurar **auditorías de seguridad** regulares, manteniendo registros de eventos y alertas configuradas para comportamientos sospechosos.
- Asegurarse de que se realicen análisis regulares de vulnerabilidades.

---

## 9. Gestión inadecuada de la sesión

### ⚠️ **Problema**

Una gestión deficiente de las sesiones, como tokens sin caducidad o sesiones compartidas, puede permitir que un atacante secuestre la sesión de un usuario.

### ✅ **Solución**

- Usar **tokens seguros** (como JWT) para gestionar sesiones y asegurar que los tokens tengan una **fecha de expiración** razonable.
- Revocar tokens de sesión después de un evento de cierre de sesión o cambio de contraseña.
- Implementar mecanismos de **protección contra el secuestro de sesión**, como el **cambio de identificadores de sesión** tras un inicio de sesión exitoso.

---

## 10. Protección insuficiente contra ataques

### ⚠️ **Problema**

Sin una protección adecuada, las aplicaciones pueden ser vulnerables a ataques comunes como **Cross-Site Request Forgery (CSRF)** o **Cross-Site Scripting (XSS)**.

### ✅ **Solución**

- Implementar **tokens CSRF** en formularios de envío de datos para proteger contra este tipo de ataques.
- Configurar una **política de seguridad de contenido (CSP)** que limite las fuentes permitidas para los scripts.
- Validar y sanitizar todas las entradas del usuario para evitar que se inyecten scripts maliciosos.
