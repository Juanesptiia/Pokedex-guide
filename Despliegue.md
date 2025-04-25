# ☁️ Implementación Profesional de la Aplicación Pokedex en la nube Azure Static Web Apps



## 1. 📌 Clonar el Proyecto Base

Accede al repositorio base del laboratorio Pokedex disponible en el siguiente enlace:  
[https://github.com/rcuello/ac4dem1a/tree/master/sistemas-distribuidos/poke-dex-lab](https://github.com/rcuello/ac4dem1a/tree/master/sistemas-distribuidos/poke-dex-lab)

Procede a realizar un **fork** del repositorio. Haz clic en el botón **Fork** ubicado en la parte superior derecha. Puedes nombrar tu copia como desees (por ejemplo, `pokedex-azure`) y luego confirmar la acción con **Create fork**.

---

## 2. 🛠️ Configuración del Entorno de Despliegue

Dirígete a tu repositorio forkeado:  
[https://github.com/Juanesptiia](https://github.com/Juanesptiia)

Ingresa a la siguiente ruta dentro de tu proyecto:

```
.github/workflows/
```

Localiza el archivo YAML correspondiente al flujo de trabajo de Azure Static Web Apps. El nombre puede variar, pero comúnmente será algo como:

```
azure-static-web-apps-*.yml
```

Haz clic en el ícono del lápiz ✏️ para editar.  
En la línea correspondiente a `app_location`, actualiza la ruta existente por la siguiente:

```yaml
app_location: "./sistemas-distribuidos/poke-dex-lab/source/pokedex-angular"
```

Guarda los cambios con **Commit changes**.

---

## 3. ✅ Verificación del Flujo de Trabajo

Haz clic en la pestaña **Actions** en la parte superior de tu repositorio.  
Allí podrás observar la ejecución automática del workflow de Azure. Espera a que el proceso se complete correctamente (estado: ✅ `Completed`).

---

## 4. 🌍 Acceso a la Aplicación en Azure

Una vez finalizado el proceso, accede al portal de Azure y navega a tu recurso **Static Web App**.  
Haz clic en **"Ir al recurso"** y copia el enlace de acceso público. 

---

## 5. 🔐 Configuración de Seguridad y Navegación

Para reforzar la seguridad de tu aplicación y definir rutas de fallback, crea el archivo de configuración correspondiente.

### Instrucciones:

1. Desde tu repositorio, dirígete a:  
   `sistemas-distribuidos/poke-dex-lab/source/pokedex-angular/`

2. Haz clic en **Add file** > **Create new file**  
3. Asigna el nombre:  
   `staticwebapp.config.json`

4. Pega el siguiente contenido:

```json
{
  "globalHeaders": {
    "Content-Security-Policy": "default-src 'self'; img-src 'self' https://raw.githubusercontent.com https://pokeapi.co https://assets.pokemon.com; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com; connect-src 'self' https://beta.pokeapi.co",
    "X-Frame-Options": "DENY",
    "Permissions-Policy": "geolocation=(), microphone=(), camera=()"
  },
  "navigationFallback": {
    "rewrite": "/index.html",
    "exclude": ["/images/", "/css/", "/js/*", "/favicon.ico"]
  }
}
```

5. Guarda los cambios y confirma con **Commit changes**.

Vuelve a **Actions** para verificar que la nueva configuración sea desplegada correctamente.

---

## 6. 🖼️ Corrección de Rutas para las Imágenes

Para asegurar la visualización adecuada de las imágenes de los Pokémon:

1. Dirígete a la carpeta:  
   `sistemas-distribuidos/poke-dex-lab/source/pokedex-angular/src/environments/`

2. Edita el archivo:  
   `environment.prod.ts`

3. Localiza la línea:

```ts
imagesPath: 'pokedex-angular/assets/images',
```

y reemplázala por:

```ts
imagesPath: '/assets/images',
```

4. Guarda y confirma los cambios.  
5. Una vez más, visita la pestaña **Actions** y asegúrate de que el proceso de despliegue se complete con éxito.

---

## 🎉 ¡Despliegue Exitoso!

Tu aplicación Pokedex ahora está disponible de forma pública y totalmente funcional desde Azure Static Web Apps.  
Verifica que las imágenes, rutas y navegación estén operando correctamente.

📌 **Acceso a tu Pokedex online:**  
🔗 [https://salmon-river-04e95b810.6.azurestaticapps.net](https://salmon-river-04e95b810.6.azurestaticapps.net)

---

¡Felicidades por completar esta implementación profesional en la nube! 🎓☁️
**🌐 Aplicación desplegada en producción:**  
[https://salmon-river-04e95b810.6.azurestaticapps.net](https://salmon-river-04e95b810.6.azurestaticapps.net)

**✍️ Autor:** Juan David Espitia  
**📂 Repositorio personal:** [https://github.com/Juanesptiia](https://github.com/Juanesptiia)  
**📚 Curso:** Sistemas Distribuidos  
**🎓 Programa:** Ingeniería de Sistemas, Noveno Semestre  
**📅 Fecha:** 20 de abril de 2025

---
