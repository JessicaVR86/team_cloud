# Proyecto: Página Web del Equipo Cloud de Adalab

Este es un proyecto de ejemplo para aprender a desplegar una página web estática en **AWS S3**. Contiene información sobre el equipo de especialistas en cloud de Adalab y sus servicios.

## Descripción

La página web es una **landing page básica** que presenta:

- Una introducción al equipo y sus servicios.
- Una sección con perfiles de los miembros del equipo.
- Información sobre sus competencias en AWS.
- Footer con créditos.

El objetivo principal de este proyecto es **practicar el despliegue de sitios web estáticos en la nube** utilizando AWS S3.

---

## Estructura del proyecto

/proyecto-cloud-adalab
│
├─ index.html # Página principal
├─ styles.css # Estilos CSS para la web
├─ Gina.png # Imagen del miembro del equipo Gina
├─ Irina.png # Imagen del miembro del equipo Irina
├─ Irene.png # Imagen del miembro del equipo Irene
├─ Jessica.png # Imagen del miembro del equipo Jessica
└─ README.md # Este archivo

---

## Tecnologías utilizadas

- **HTML5**: Estructura de la página.
- **CSS3**: Estilos y diseño de la página.
- **AWS S3**: Hosting de la página web estática.

---

## Cómo desplegar en AWS S3

1. **Crear un bucket en S3**  
   - Accede a tu consola de AWS S3 y crea un bucket nuevo.
   - Elige un nombre único global.
   - Desactiva el bloqueo de acceso público (para permitir que cualquiera pueda ver la página).

2. **Subir archivos al bucket**  
   - Sube `index.html`, `styles.css` y las imágenes del proyecto.
   - Mantén la estructura de carpetas para que los enlaces funcionen correctamente.

3. **Configurar el bucket para hosting estático**  
   - Ve a **Properties → Static website hosting**.
   - Marca **Enable**.
   - Define `index.html` como documento de inicio.
   - Copia la URL proporcionada para acceder a tu página web.

4. **Hacer públicos los archivos**  
   - Ve a **Permissions → Bucket Policy**.
   - Aplica una política que permita acceso público de lectura a todos los archivos del bucket. Ejemplo:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::NOMBRE_DE_TU_BUCKET/*"
    }
  ]
}
