# Clóset Wada

App Android para registrar tu ropa con la cámara, recortar cada prenda, confirmar su color y armar outfits con las 348 combinaciones del *Dictionary of Color Combinations* de Sanzo Wada.

Todo funciona dentro del celular: las prendas y sus fotos se guardan en el dispositivo, sin cuentas ni servidores.

## Cómo obtener el APK (sin instalar nada)

1. Sube este proyecto a un repositorio de GitHub.
2. En el repositorio, entra a la pestaña **Actions** y abre **Compilar APK**. Se ejecuta solo con cada cambio en `main`; también puedes lanzarlo con **Run workflow**.
3. Cuando termine (unos 5 minutos), abre la ejecución y descarga **closet-wada-apk** en la sección *Artifacts*. Es un `.zip` con el archivo `app-debug.apk`.
4. Pasa el `.apk` al celular y ábrelo. Android pedirá permitir la instalación de apps de origen desconocido para esa app (por ejemplo, tu navegador o el administrador de archivos).

## Cómo compilarlo en tu computador

Necesitas Node.js 20, JDK 17 y Android Studio.

```bash
npm ci
npx cap sync android
npx cap open android   # abre Android Studio; luego Build > Build APK(s)
```

## Estructura

| Carpeta | Qué contiene |
| --- | --- |
| `www/` | La app completa (HTML, CSS y JavaScript en un solo archivo, con los datos de Wada incluidos) |
| `android/` | Proyecto Android generado por Capacitor |
| `.github/workflows/apk.yml` | Compilación automática del APK en GitHub Actions |

## Notas

- El APK de prueba (`debug`) sirve para instalarlo en tu celular y compartirlo con amigos. Para publicar en Google Play hay que generar una versión firmada (`release`).
- La detección de color usa CIELAB y Delta E 2000; el recorte (varita, lazo y pinceles) corre en el propio celular.
- Datos de color: [mattdesl/dictionary-of-colour-combinations](https://github.com/mattdesl/dictionary-of-colour-combinations).
