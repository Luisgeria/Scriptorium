# Escritores de Mapa · El Laboratorio Creativo

Aplicación web de escritura creativa para alumnos de 8 a 16 años.  
Diseñada para actividades de calentamiento en clase (15-20 minutos).

---

## Archivos

| Archivo | Función |
|---|---|
| `index.html` | App del alumno |
| `docente.html` | Panel del docente (contraseña: `112233`) |

---

## App del alumno (`index.html`)

Tres pasos guiados:

1. **Género & chispa** — 6 géneros con 7 frases de arranque cada uno
2. **Tu mapa** — Protagonista, problema y desenlace en 2 minutos
3. **A escribir** — Editor limpio con temporizador de 15 min y contador de palabras

Al terminar, el texto se guarda automáticamente en Firebase con nombre, género, chispa, mapa y estadísticas.

---

## Panel del docente (`docente.html`)

Acceso con contraseña `112233`.

### Funcionalidades

**Estadísticas en tiempo real**
- Total de textos guardados
- Escritos hoy
- Palabras de media
- Textos con feedback

**Género del día**
- Fija un género para toda la clase → los alumnos solo ven ese género disponible
- Libera la elección en cualquier momento
- Se sincroniza con Firebase: al recargar la app del alumno ya ve el género fijado

**Lectura de textos**
- Lista ordenada por fecha (más recientes primero)
- Filtros por género, por feedback y búsqueda por nombre o contenido
- Cada texto desplegable muestra: chispa elegida, mini-mapa (protagonista / problema / desenlace) y texto completo

**Feedback por alumno**
- Campo de observaciones por texto
- Se guarda en Firebase y queda visible en futuras sesiones
- Indicador visual en la tarjeta del alumno

---

## Configuración Firebase

Antes de subir a GitHub, sustituye el objeto `firebaseConfig` en **ambos archivos** con los datos reales de tu proyecto `app-reserva-de-portatiles`:

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "app-reserva-de-portatiles.firebaseapp.com",
  databaseURL: "https://app-reserva-de-portatiles-default-rtdb.europe-west1.firebasedatabase.app",
  projectId: "app-reserva-de-portatiles",
  storageBucket: "app-reserva-de-portatiles.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

### Reglas de Realtime Database recomendadas

```json
{
  "rules": {
    "escritores": {
      "textos": {
        ".read": true,
        ".write": true
      },
      "settings": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

### Estructura de datos generada

```
escritores/
  settings/
    generoFijado: true/false
    generoId: "terror" | "aventura" | ...
    updatedAt: "2026-05-29T..."
  textos/
    -Nxxx.../
      nombre: "Lucía García"
      genero: "Terror"
      generoId: "terror"
      emoji: "👻"
      chispa: "El espejo no devolvía mi reflejo."
      protagonista: "Una niña que no puede dormir"
      problema: "Oye pasos en el tejado"
      final: "Era un pájaro perdido"
      texto: "Esa noche, cuando..."
      palabras: 87
      minutos: 12
      fecha: "2026-05-29T10:34:00Z"
      timestamp: 1748514840000
      feedback: "Muy buen uso de la elipsis al final."
      feedbackAt: "2026-05-29T11:00:00Z"
```

---

## Despliegue en GitHub Pages

1. Crear repositorio `escritores-de-mapa`
2. Subir `index.html`, `docente.html` y `README.md`
3. **Settings → Pages → Source: main / (root) → Save**

URLs resultantes:
- Alumno: `https://luisgeria.github.io/escritores-de-mapa/`
- Docente: `https://luisgeria.github.io/escritores-de-mapa/docente.html`

---

## Créditos

Desarrollado en el marco del proyecto **IAprendizaje** — Licencia por Estudios 2024/2025, Junta de Castilla y León.  
Tipografías: Cinzel y EB Garamond (Google Fonts). Licencia MIT.
