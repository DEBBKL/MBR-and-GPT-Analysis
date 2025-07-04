# Walkthrough TryHackMe: mbrandgptanalysis

Este repositorio documenta paso a paso el proceso para completar la room **mbrandgptanalysis** en TryHackMe. Esta room se centra en el análisis forense de un bootkit detectado en un servidor Windows crítico, y nos guía en la identificación de modificaciones maliciosas en el bootloader UEFI `bootmgr.efi`.

---

## Introducción

En este escenario, un bootkit ha comprometido el arranque seguro del sistema modificando el archivo `bootmgr.efi`. Nuestra misión es analizar este archivo para detectar la manipulación, identificar cadenas ocultas y entender cómo este tipo de amenazas afecta a la seguridad del arranque del sistema.

---

## Objetivos de aprendizaje

- Comprender las diferencias entre sistemas de arranque BIOS/MBR y UEFI/GPT.
- Aprender a usar editores hexadecimales para analizar archivos binarios.
- Detectar y extraer cadenas ocultas en archivos como `bootmgr.efi`.
- Entender el funcionamiento y riesgos de los bootkits.
- Reforzar conocimientos sobre Secure Boot y protección de la integridad del arranque.

---

## Requisitos previos

Para realizar este análisis es recomendable contar con:

- Cuenta activa en TryHackMe y acceso a la room [mbrandgptanalysis](https://tryhackme.com/room/mbrandgptanalysis).
- Conocimientos básicos sobre sistemas Windows y su proceso de arranque.
- Familiaridad con editores hexadecimales como HxD.
- Acceso a un equipo Windows para realizar el análisis local.
- Herramientas para decodificación base64 (pueden ser online o locales).

---

## Herramientas utilizadas

- **HxD Hex Editor:** Editor hexadecimal gratuito para visualizar y analizar archivos binarios.
- **TryHackMe:** Plataforma para práctica segura de ciberseguridad.
- **Herramientas online para decodificación Base64:** como [base64decode.org](https://www.base64decode.org/).

---

## Paso a paso del walkthrough

### 1. Descarga y preparación del archivo

- Desde la room en TryHackMe, descarga el archivo `bootmgr.efi`.
- Guárdalo en una carpeta accesible, por ejemplo: `C:\Analysis\bootmgr.efi`.
- Guarda una copia original sin modificaciones para futuras comparaciones.

### 2. Análisis inicial con HxD

- Abre HxD y carga el archivo `bootmgr.efi`.
- Observa las primeras 512 bytes y examina el contenido en hexadecimal y ASCII.
- Busca áreas de espacio aparentemente vacío (por ejemplo, muchos bytes 00) que puedan contener datos ocultos.

### 3. Identificación de cadenas codificadas

- Al revisar el archivo, puedes encontrar fragmentos que no parecen parte del código estándar.
- Por ejemplo, un fragmento hexadecimal así:
  ```
  53 47 56 73 62 47 38 73 49 45 56 47 53 53 42 43 62 32 39 30 61 32 6C 30 49 51 3D 3D
  ```

- Convierte este bloque hexadecimal a texto ASCII para ver la cadena codificada.

### 4. Decodificación de la cadena oculta

- La cadena ASCII resultante puede estar codificada en base64.
- Usa una herramienta online como [base64decode.org](https://www.base64decode.org/) para pegar la cadena y decodificarla.
- El resultado puede revelar instrucciones o datos maliciosos incrustados por el bootkit.

### 5. Interpretación del resultado

- Analiza cuidadosamente la información decodificada.
- Esto puede ser código malicioso, comandos, URLs o datos que ayuden a comprender el ataque.
- Documenta cualquier hallazgo relevante que confirme la manipulación del bootloader.

### 6. Reflexión y mitigación

- Comprender la importancia de proteger el proceso de arranque, ya que es crítico para la seguridad del sistema.
- Destacar el papel de tecnologías como Secure Boot para prevenir modificaciones no autorizadas.
- Proponer medidas de detección temprana y respuesta a amenazas como bootkits.

---

## Recursos adicionales

- [Documentación oficial UEFI](https://uefi.org/)
- [Microsoft Secure Boot](https://learn.microsoft.com/en-us/windows/security/information-protection/secure-the-boot-process-with-secure-boot)
- [TryHackMe Forensics Rooms](https://tryhackme.com/room/forensics)
- Herramientas hexadecimales como HxD o Hex Workshop

---

## Conclusión

Esta room nos ha permitido adentrarnos en un escenario realista de compromiso avanzado en sistemas Windows mediante bootkits. La habilidad para analizar archivos binarios, detectar datos ocultos y entender las vulnerabilidades del proceso de arranque es esencial para profesionales en ciberseguridad interesados en defensa avanzada y análisis forense.

---

## Contacto

Para dudas o contribuciones, por favor abre un issue en este repositorio.

*Autor: Déborah Loisel*  
*Fecha: 2025-07-04*

---

*¡Gracias por seguir este walkthrough!*

