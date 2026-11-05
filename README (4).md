# Sistema de votación (estilo Matrix)

Votación secreta con candidatos sin nombre (solo nombres en clave), enlaces a cada trabajo y dos modos: **alumno** y **admin**.

## Cómo publicarla

1. Subí `index.html`, `config.js`, `firestore.rules` y `README.md` a un repositorio de GitHub.
2. **Settings → Pages → Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. En Firebase, abrí **Base de datos → Reglas**, borrá todo, pegá el contenido de `firestore.rules` y tocá **Publicar**. Este archivo incluye también las reglas del sitio de proyectos, así que no rompe nada de lo anterior.
4. `config.js` ya trae los datos de Firebase. Cambiá `adminPin` por tu propia clave.

Sin Firebase configurado funciona en modo local de prueba (los datos quedan solo en tu navegador).

## Modo admin

Tocá **acceso admin** (abajo de todo) e ingresá la clave. Desde ahí:

- **Estado:** abrir o cerrar la votación, mostrar u ocultar los resultados a los alumnos, y editar título y subtítulo.
- **Candidatos:** agregar, borrar y editar el nombre en clave, el enlace al trabajo y una descripción corta.
- **Códigos de acceso:** generar códigos y copiar los que siguen disponibles. Los usados aparecen tachados.
- **Resultados en vivo:** barras y porcentajes que se actualizan solas.
- **Ver como alumno:** vista previa de lo que ven los alumnos, sin registrar votos.
- **Reiniciar votos:** borra los votos y libera todos los códigos.

## Modo alumno

El alumno entra al link, ingresa su código de acceso, mira los trabajos con **Ver trabajo**, elige y confirma. Cada código sirve para un solo voto y no se puede cambiar.

## Límites a tener en cuenta

- El secreto del voto es **de interfaz**: los alumnos no ven quién votó a quién ni los resultados antes de tiempo, pero esta clase de página no tiene servidor propio. Alguien con conocimientos técnicos podría leer la base de datos o saltearse la clave de admin. Es adecuada para una votación de aula, no para una elección con consecuencias serias. La solución real sería sumar inicio de sesión de administrador con Firebase Authentication.
- No pongas nombres reales en el nombre en clave de los candidatos.
