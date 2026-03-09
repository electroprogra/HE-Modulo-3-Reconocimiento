# Tarea 3 · Módulo 3: Reconocimiento Pasivo y Activo Básico
## Parte 1 – Reconocimiento Pasivo con Google Dorks
Se utilizaron los siguientes Google Dorks:<br/>

### Buscar listado de directorios
`site:*.gob.mx intitle:index.of`
>Se encontraron directorios de archivos.<br/>
>Riesgo de exposición de información sensible, se encontró un archivo con usuarios y correos.<br/>

### Buscar información de configuración
`site:*.gob.mx intitle:config OR intitle:server`
>Riesgo de exposición de información sensible, no se encontraron resultados para URL de archivos/páginas de configuración.<br/>

### Buscar panel de control
`site:*.gob.mx inurl:/admin OR inurl:/dashboard intitle:"Control panel" OR intitle:"Panel de control" -osint`
>Riesgo de acceso no autorizado, se encontraron varios resultados de páginas de login para paneles de control (Buscar vulnerabilidades en login, ej. inyección de código).<br/>

### Buscar páginas de autenticación
`site:*.gob.mx inurl:/login/ OR intitle:login`
`site:*.gob.mx inurl:remote/login/`
>Riesgo de acceso no autorizado, se encontraron varios resultados de páginas de login (Buscar vulnerabilidades en login, ej. inyección de código).<br/>

### Buscar información de autenticación
`site:*.gob.mx pass" OR "user" OR "password" OR "usuario" OR "clave" filetype:txt OR filetype:ini OR filetype:xml OR filetype:log OR filetype:sql OR filetype:conf OR filetype:properties OR filetype:json OR filetype:env OR filetype:bak`
>Riesgo de acceso no autorizado, se encontró un archivo de usuario con contraseñas.<br/>

### Buscar archivos de configuración de servidores WEB
`site:*.gob.mx inurl:httpd.conf OR inurl:apache2.conf OR inurl:conf.d OR inurl:nginx.conf OR inurl:web.config OR inurl:web.xml OR inurl:web-jetty.xml OR inurl:applicationContext.xml OR inurl:struts-config.xml OR inurl:applicationSecurity.xml OR inurl:manifest.mf`
>Riesgo de exposición de información sensible, se encontraron varios resultados de configuración de apliación web (Para indagar más información o vulnerabilidades)<br/>

### Buscar componentes del servidor WEB con vulnerabilidades identificadas
`site:*.gob.mx inurl:javax.faces.resource OR inurl:jsp OR inurl:jsf OR inurl:xhtml`
>Riesgos varios dependiendo de la vulnerabilidad, se probó vulnerabilidad de PATH TRAVERSAL en los primeros 2 resultados, encontrándose uno de ellos con la capacidad de explotarse la vulnerabilidad.<br/>
<br/>

> [!NOTE]
> Evidencias en [PARTE_1_GOOGLE_DORKS](/PARTE_1_GOOGLE_DORKS).

<br/><br/>



## Parte 2 – Investigación en GHDB
Se encontraron los siguientes Google Dorks (Google Hacking):<br/>

`intitle:"SSL Network Extender Login" -checkpoint.com [https://www.exploit-db.com/ghdb/8447](https://www.exploit-db.com/ghdb/8447)`
>**BUSCA:** Página de login a VPN.<br/>
>**EXPOSICIÓN:** De acceso no autorizado.<br/>
>**CATEGORÍA:** Vulnerable Servers<br/>

`intitle:"index of" env.cgi [https://www.exploit-db.com/ghdb/8404]](https://www.exploit-db.com/ghdb/8404)`
>**BUSCA:** Información de aplicaciones CGI.<br/>
>**EXPOSICIÓN:** De información sensible.<br/>
>**CATEGORÍA:** Files Containing Juicy Info<br/>

`intitle:"OpenVpn Status Monitor" [https://www.exploit-db.com/ghdb/8399]](https://www.exploit-db.com/ghdb/8399)`
>**BUSCA:** Información de servidores con OpenVPN.<br/>
>**EXPOSICIÓN:** De información sensible.<br/>
>**CATEGORÍA:** Vulnerable Servers<br/>
<br/><br/>


## Parte 3 – Maltego (Mapa Visual)
1. De la ENTITY PALETTE se utilizó el elemento DOMAIN.
2. Se utilizó de objetivo el dominio https://ferias.empleo.gob.mx.
3. Del dominio anterior se obtuvo el DNS (Transformer: To Domains DNS).
4. Del DNS se obtuvo la IP (Transformer: To IP Address DNS).
5. De la IP se obutvo la localicación (Transformer: To location City, Country).<br/>
![Mapa visual - Tarea 3 realizado en Maltego](/PARTE_3_MALTEGO/Screenshot%202026-03-09%20at%2010.53.00%E2%80%AFa.m..png)<br/>
![Mapa visual - Tarea 3 v2, realizado en Maltego utilizando herramienta MACHINES - FOOTPRINT L1](/PARTE_3_MALTEGO/Screenshot%202026-03-09%20at%2011.00.52%E2%80%AFa.m..png)<br/>

> [!NOTE]
> Evidencias en [PARTE_3_MALTEGO](/PARTE_3_MALTEGO).

<br/><br/>


## Parte 4 – Reflexión (1 hoja)
Responder:<br/>

* **Diferencia entre reconocimiento pasivo y activo.**
>El reconocimiento pasivo es la obtención de información mediante fuentes de datos públicas (Ej. buscador, redes sociales, comunicados, ...), el reconocimiento activo involucra interactuar con el objetivo para obtener la información.

* **¿Por qué el reconocimiento sin autorización puede ser ilegal?**
>Porque hay leyes que protegen la privacidad de la información.

* **¿Qué aprendiste sobre la exposición de información?**
>Hay mucha información sensible de forma pública cuando no debería ser completamente pública, dicha información puede apoyar o provocar brechas de seguridad.
<br/><br/>



## 📦 ¿Cómo lo entregan?
**Suben a GitHub un repositorio llamado:**
>Modulo-3-Reconocimiento

**Con:**
* PDF con evidencias<br/>
* Capturas<br/>
* Explicaciones<br/>
* ***[README.md](https://github.com/electroprogra/HE-Modulo-3-Reconocimiento/blob/main/README.md)** explicando lo que hicieron