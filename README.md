🏈 LINFAAC - Torneo Estatal de Flag Football
Sitio web oficial del Torneo Estatal de Flag Football de la Liga LINFAAC.
📋 Especificaciones del Torneo
Table
Parámetro	Valor
Duración	3 días
Campos	12 simultáneos
Horario	7:00 AM - 4:00 PM
Duración partido	50 minutos
Descanso entre partidos	10 minutos
Slots por día	9 (7:00, 8:00, 9:00, 10:00, 11:00, 12:00, 13:00, 14:00, 15:00)
Categorías	6 (Varonil, Femenil, Mixto, Sub-17, Sub-15, Veteranos)
Equipos totales	26
Partidos fase regular	84
Playoffs	Semifinal + Final por categoría
🔄 Actualización en Tiempo Real
El sitio web se actualiza automáticamente cada 30 segundos. Los usuarios no necesitan recargar la página manualmente.
Cuando detecta cambios en data.json:
✅ Actualiza marcadores en vivo
✅ Actualiza estados de partido
✅ Recalcula tablas de posiciones
✅ Actualiza bracket de playoffs
Muestra indicador verde "Actualizando" en el header
📁 Estructura del proyecto
plain
Copy
linfaac-torneo/
├── index.html      # Página web (diseño, lógica y auto-refresh)
├── data.json       # Base de datos del torneo
└── README.md       # Este archivo
🏠 Sistema de Equipos Casa vs Visitante
Regla principal
Los equipos de casa (inscritos en la liga regular) NO se enfrentan entre sí.
Cada categoría tiene:
Equipos de casa ("casa": true): Inscritos en la liga regular LINFAAC
Equipos visitantes ("casa": false): Equipos invitados al torneo estatal
Toggle de filtro
En la sección Rosters, hay un switch para mostrar solo equipos de casa.
🏆 Sistema de Playoffs
Estructura por categoría
plain
Copy
Semifinal 1: 1° lugar vs 4° lugar
Semifinal 2: 2° lugar vs 3° lugar
       ↓
    Final: Ganador SF1 vs Ganador SF2
       ↓
   Campeón
Cómo configurar playoffs en data.json
Agrega la sección "playoffs" al JSON:
JSON
Copy
{
  "teams": [ ... ],
  "schedule": [ ... ],
  "playoffs": [
    {
      "category": "Varonil",
      "rounds": [
        {
          "round": "Semifinal",
          "matches": [
            {
              "id": "v_sf1",
              "name": "Semifinal 1",
              "team1": "v1",
              "team2": "v5",
              "score1": 21,
              "score2": 14,
              "status": "finished",
              "winner": "v1",
              "field": "Cancha 1",
              "time": "16:00"
            }
          ]
        },
        {
          "round": "Final",
          "matches": [
            {
              "id": "v_f1",
              "name": "Gran Final",
              "team1": "v1",
              "team2": "v6",
              "score1": null,
              "score2": null,
              "status": "upcoming",
              "winner": null,
              "field": "Cancha Principal",
              "time": "18:00"
            }
          ]
        }
      ]
    }
  ]
}
Table
Campo	Descripción
team1, team2	IDs de los equipos. Usa null si aún no se define
winner	ID del equipo ganador. null si no hay ganador aún
status	upcoming, live, finished
score1, score2	Marcador o null
Cuando un partido de semifinal tiene winner, la final se actualiza automáticamente mostrando al ganador.
🚀 Cómo publicar en GitHub Pages
Paso 1: Crear el repositorio
Ve a github.com e inicia sesión.
Haz clic en New repository.
Nombra el repositorio: linfaac-torneo.
Deja todo en público y haz clic en Create repository.
Paso 2: Subir los archivos
En tu nuevo repositorio, haz clic en uploading an existing file.
Arrastra los 3 archivos (index.html, data.json, README.md) o selecciónalos.
Escribe como mensaje de commit: Initial commit.
Haz clic en Commit changes.
Paso 3: Activar GitHub Pages
Ve a la pestaña Settings de tu repositorio.
En el menú lateral izquierdo, haz clic en Pages.
En Source, selecciona la rama main y la carpeta / (root).
Haz clic en Save.
Espera 1-2 minutos. Tu sitio estará disponible en:
plain
Copy
https://TU_USUARIO.github.io/linfaac-torneo/
✏️ Cómo actualizar datos durante el torneo
Desde la computadora:
Ve a tu repositorio en GitHub.
Haz clic en el archivo data.json.
Haz clic en el ícono del lápiz (✏️) arriba a la derecha para editar.
Modifica los datos que necesites.
Al final de la página, escribe un mensaje como: Actualiza resultados día 1.
Haz clic en Commit changes.
En 1-3 minutos, todos los usuarios verán los cambios automáticamente.
Desde el celular:
Abre el navegador e ingresa a tu repositorio.
Toca data.json → los tres puntos ... → Edit.
Realiza los cambios y guarda con Commit changes.
📋 Guía para editar data.json
Cambiar un resultado de partido (fase regular)
JSON
Copy
{
  "id": 1,
  "day": 1,
  "time": "09:00",
  "field": "Cancha 5",
  "category": "Varonil",
  "team1": "v1",
  "team2": "v5",
  "status": "finished",
  "score1": 21,
  "score2": 14
}
Table
Estado	Descripción
upcoming	Por jugar
live	En vivo (marcador actualizable)
finished	Finalizado
Estados de partido en la página
Table
Estado	Badge mostrado
upcoming	Programado
live	En Curso (pulsante)
finished	Finalizado
⚠️ Reglas importantes al editar
NO borres las comas al final de cada línea (excepto la última de cada bloque).
NO modifiques los id de los equipos si ya tienen partidos asignados.
Siempre usa comillas dobles " para el texto.
Los valores null no llevan comillas (escríbelos así: null).
Verifica la estructura: cada llave { debe cerrarse con }.
🎨 Personalizar colores de equipos
Los colores se escriben en formato hexadecimal. Ejemplos:
Table
Color	Código
Azul marino	#1e3a8a
Negro mate	#171717
Rojo oscuro	#991b1b
Naranja quemado	#c2410c
Morado real	#6b21a8
Verde bosque	#065f46
Café cobrizo	#92400e
Dorado	#c9a227
Busca más en htmlcolorcodes.com.
📱 Compartir el sitio
plain
Copy
https://TU_USUARIO.github.io/linfaac-torneo/
Los espectadores pueden abrirlo desde cualquier celular o computadora sin instalar nada.
¿Preguntas? El sitio es 100% estático, no requiere servidor ni base de datos. Solo GitHub Pages + este repositorio.
