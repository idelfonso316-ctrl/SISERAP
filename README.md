# SISERAP · Sistema de Seguimiento de Resultados de Aprendizaje Pendientes

Aplicación web del **Politécnico Nuestra Señora del Perpetuo Socorro** (Base Área de San Isidro, Santo Domingo Este) para registrar estudiantes con Resultados de Aprendizaje (RA) pendientes, sus evidencias y su seguimiento pedagógico, y para generar los formularios e informes imprimibles.

## Estado actual (Fase 1: modo local)

- Funciona sin servidor: los datos se guardan **solo en el navegador de cada dispositivo** (IndexedDB) y **no se sincronizan** entre equipos.
- Incluye: panel, estudiantes, RA con historial, evidencias, seguimiento (con sugerencias rápidas), formulario e informe imprimibles (carta, vertical), informes con CSV, respaldo/restauración, datos DEMO, modo oscuro/claro, reinicio desde cero.
- Incluye `manifest.webmanifest` y `sw.js` para poder instalarla como PWA cuando se sirve por HTTPS.
- **Pendiente (Fase 2):** inicio de sesión y roles, base de datos central (por ejemplo Supabase), adjuntos, instalador de Windows (Electron o Tauri) y APK (Capacitor). Nada de esto está implementado todavía.

## Estructura

```
index.html              Aplicación completa (HTML, CSS y JavaScript)
manifest.webmanifest    Datos de instalación PWA
sw.js                   Service Worker (disponibilidad sin conexión)
icons/                  Iconos 192 y 512 px
.github/workflows/      Publicación automática en GitHub Pages
```

## Probar en su equipo

```bash
python3 -m http.server 8080
# abrir http://localhost:8080
```

El Service Worker solo se activa en `localhost` o HTTPS, no abriendo el archivo con doble clic.

## Subir a GitHub y publicar

1. Cree un repositorio vacío en github.com (por ejemplo `siserap`).
2. En la carpeta del proyecto:
   ```bash
   git init -b main
   git add .
   git commit -m "SISERAP fase 1: modo local"
   git remote add origin https://github.com/USUARIO/siserap.git
   git push -u origin main
   ```
3. En GitHub: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
4. El flujo `pages.yml` publica la app en `https://USUARIO.github.io/siserap/`. El progreso se ve en la pestaña **Actions**.

GitHub Pages desde un repositorio privado requiere un plan de pago de GitHub; con el plan gratuito el repositorio debe ser público. El repositorio solo contiene el código: **los datos de los estudiantes nunca están en él**, viven en cada navegador.

## Privacidad

- No suba respaldos (`siserap-respaldo*.json`) ni informes con datos reales; el `.gitignore` ya los excluye.
- Haga respaldos periódicos desde *Respaldo e instalación*, porque borrar los datos del navegador elimina la información.
- La herramienta no es un expediente clínico: no registre diagnósticos ni información psicológica.

## Licencia

Por definir por la institución.
