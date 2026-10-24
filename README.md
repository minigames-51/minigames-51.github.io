# Los Gatitos 8-bit · Elecciones Escolares 2027

Juego estilo 8 bits (horizontal) hecho en un solo archivo `index.html`. Sin dependencias: HTML + Canvas + JavaScript.

## Cómo jugarlo
- **Local:** abre `index.html` en el navegador.
- **GitHub Pages:** sube el repo → *Settings → Pages → Deploy from branch (main / root)*.

## Controles
- Mover: WASD / flechas (en celular: joystick izquierdo)
- Armas: teclas 1-3 o Q (botón ARMA). El ataque es automático y recarga solo.
- Habilidad: ESPACIO (botón ESP) cuando la barra azul está llena (se carga al matar).
- Pausa: P

## Contenido
- 5 candidatos jugables con pasiva propia y 4 slots de equipo (3 armas de juguete con accesorios + 1 habilidad).
- 7 armas con munición, cadencia y recarga distintas; cajas de munición; blindaje de libros.
- 5 habilidades: torreta, invisibilidad, revobinar, invulnerabilidad y teletransporte.
- 4 ventajas de 3 niveles que se compran con monedas.
- Campaña (6 mapas con obstáculos), modo infinito (niveles 1–20) y modo zombis por oleadas.
- Ranking local (top 10) y progreso guardado en `localStorage`.
- Zombis por oleadas con descanso entre rondas, jefe cada 5 oleadas y enemigos que escalan en vida y daño.
- Dos joysticks (movimiento y apuntado/disparo) y tres modos de disparo, que se cambian en Ajustes o en la pantalla de preparación:
  - **Automático:** apunta solo al enemigo más cercano; si inclinas el joystick de disparo, dispara hacia donde apuntes.
  - **Semiautomático (x1.5 monedas):** apuntas con el joystick y dispara solo cuando hay un enemigo en la mira.
  - **Manual (x2 monedas):** apuntas con el joystick y disparas con el botón FUEGO.
- Controles táctiles editables (Ajustes → Editar controles).
- Menú de preparación para elegir clase/equipo antes de cada partida.

## Cómo agregar un accesorio
En `index.html`, agrega un objeto al arreglo `ACC`. Los multiplicadores válidos son `dm` (daño), `cd` (cadencia: menor = más rápido), `mag` (cargador), `rl` (recarga: menor = más rápida), `sp` (velocidad de bala) y `rg` (alcance). Ejemplo: `{nm:'Silenciador',dm:.9,cd:.9}`. Para un efecto nuevo agrega una bandera (como `las` o `rb`) en `ws()` y programa su efecto en `upd()`/`hit()`.

## Zombis (nuevo)
- **Zombis 15:** mapa normal, 15 rondas, puntos de partida (aleatorios por impacto) y estación de munición (200 un arma / 500 todas) que cambia de lugar.
- **Extremo 20:** mapa grande con 4 zonas; empiezas con pistola + melee de tu equipo. Hay armas en las paredes (siluetas blancas), puertas (1000 → 1250 → 1500), perks (Juggernog, Double Tap, Speed Cola, Stamin-Up) y Pack-a-Punch. Las ventajas de la tienda solo funcionan pagando 1000×(nivel×1.15) en la estación de ventajas.
- **Inf 60:** igual que Extremo, 60 rondas y cambio de mapa cada 12.
- Controles: **USAR** (toca = 1 arma / mantén = todas) o F / G, **PLACA** o R para reponer placas (máx. 15). Chalecos de 2/3/4 slots (Thiago: 5 slots y 1.25 placas por recogida).

## Armero
- Menú principal → **ARMERO** (o toca un arma en Equipo). Ves el arma en grande, navegas con ◄ ►, y al activar un accesorio el arma cambia visualmente (con un destello) y las barras de estadísticas muestran lo que ganas (verde) o pierdes (rojo).
- Los accesorios se guardan **por arma** (máx. 4 de 6) y se equipan en la posición 1, 2 o 3 de tu equipo.

## Progresión y desbloqueos (nuevo)
- **Nivel de jugador (1–20):** ganas XP con bajas, misiones y rondas de zombis (150 XP por nivel; completar la campaña ~1.5 veces llega al máximo). Desbloquea armas, habilidades, operadores, chalecos y modos.
- **Nivel de arma:** sube con las bajas hechas con ella y desbloquea sus accesorios (Armero → Equipo → ARMA 1/2/3).
- **Operadores secretos** (Michprice, Michoup, Michaz, Michuri, Michalex): se desbloquean con un código en Operadores → CÓDIGO.
- **Zombis:** configuración de modo, mapa (aleatorio = +120% monedas), 6 armas a la venta y zombis no-muertos (opcional). La tienda del mapa vende tus armas con tus accesorios.
- **Minimapa** movible y redimensionable (Ajustes → Editar controles) que muestra estaciones, perks y zombis. Toca los cuadritos de armas para cambiar de arma.

## Zombis: perks, Pack-a-Punch y armero
- **10 perks** (Juggernog, Double Tap, Speed Cola, Stamin-Up, Quick Revive, Deadshot, Vulture Aid, Electric Cherry, Placa Cola, Reposición). Cada mapa ofrece 4 distintos; los que tienes aparecen en una barra con su símbolo.
- **Pack-a-Punch de 10 niveles** (3000 → 12000 pts): cada nivel sube daño, cadencia y alcance, acelera la recarga y aumenta un 25% (acumulado) el cargador y la munición de reserva.
- **Armero en el mapa:** personaliza el arma que llevas (10 000 pts la primera vez; luego es gratis). La tienda vende armas personalizadas a 10 000 pts.
- **Habilidades con nivel (1–5):** suben al usarlas y mejoran sus efectos y la carga por baja. Nueva: **Maestro en trampas** (2 minas unidas por un cable eléctrico, 10 s activas; 3 minas que recargan en 40 s cada una).

## Pantalla completa y ajuste al dispositivo
- La pantalla del juego se adapta a la proporción del dispositivo (sin franjas negras) y respeta las muescas/cámara.
- Con un toque entra en **pantalla completa** (sin barra de búsqueda) y bloquea la orientación horizontal. Se activa/desactiva en Ajustes → Pantalla completa.
- Dentro de una partida aparece el botón **<** arriba a la izquierda para salir de la sala (con confirmación).
- Si lo publicas en GitHub Pages, también se puede **instalar como app** ("Añadir a pantalla de inicio"): `manifest.webmanifest` e `icon.svg` ya están incluidos. En iPhone/iPad esa es la forma de ocultar la barra del navegador.
