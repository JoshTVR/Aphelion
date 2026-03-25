# APHELION — Unity Developer Series

## Volumen 1: Los Cimientos

**Bienvenido al inicio.**

Este volumen es el más importante de toda la serie. No porque sea el más difícil, sino porque establece la forma en que vas a pensar sobre Unity para siempre. Los errores de comprensión que se forman aquí son los que persisten durante años. Por eso no vamos a apresurarnos.

Cuando termines este volumen, tendrás:

- Un personaje moviéndose en un mundo 3D con físicas reales
- Una cámara en tercera persona que lo sigue suavemente
- Colisiones que impiden atravesar el suelo y las paredes
- Un menú principal que carga la escena del juego
- La capacidad de leer y escribir scripts de C# sin copiar y pegar

No tendrás un juego terminado. Tendrás los fundamentos que hacen posible construir cualquier juego.

---

## Cómo usar esta documentación

Cada capítulo sigue la misma estructura de 9 secciones:

| Sección                  | Propósito                                                |
| ------------------------ | -------------------------------------------------------- |
| **Qué vas a construir**  | El estado final — lo que verás en Unity cuando termines  |
| **El Por Qué**           | La teoría profunda antes de escribir una sola línea      |
| **Anatomía del código**  | Cada línea explicada antes de que la escribas            |
| **Ejercicio guiado**     | Los pasos exactos con cada menú y campo especificado     |
| **Qué acaba de pasar**   | La conexión entre lo que hiciste y la teoría             |
| **Errores comunes**      | Los 3-5 errores más frecuentes de este tema              |
| **Retos independientes** | Desafíos con sistema de 3 pistas para cuando te atasques |
| **Resumen**              | Lista completa de todo lo introducido                    |
| **Glosario**             | Definiciones ancladas al juego Aphelion                  |

### El sistema de 3 pistas

Los retos no tienen respuesta directa. Tienen pistas:

- **Pista 1 — Dirección:** Una pregunta que apunta hacia dónde mirar
- **Pista 2 — Enfoque:** El patrón o mecanismo a usar, sin código
- **Pista 3 — Esqueleto:** El código con los espacios clave vacíos

Intenta el reto primero. Si te atasques, lee solo la Pista 1. Si sigues atascado, lee la Pista 2. La Pista 3 es el último recurso. Este sistema existe porque resolver algo con un mínimo de ayuda construye más capacidad que resolverlo sin ayuda o con la respuesta completa.

---

## El proyecto: Aphelion

A lo largo de los 5 volúmenes construirás **Aphelion**: un RPG/Aventura 3D oscuro y atmosférico. El protagonista explora ruinas antiguas, enfrenta enemigos con IA, recoge objetos, tiene conversaciones con NPCs y descubre fragmentos de una narrativa.

Esto no es un juego de demostración. Es un juego real con un portafolio real al final.

Cada capítulo añade una pieza concreta a Aphelion. Cuando estudias el Capítulo 7 sobre física, lo haces porque necesitas que el protagonista de Aphelion no caiga por el suelo. La teoría siempre tiene un para qué.

---

## Capítulos de este volumen

- [Capítulo 1 — El Editor de Unity: Tu Entorno de Trabajo](Cap01_El_Editor.md)
- [Capítulo 2 — GameObjects, Componentes y la Jerarquía](Cap02_GameObjects_Componentes.md)
- [Capítulo 3 — Tu Primer Script: Qué es un MonoBehaviour y por qué existe](Cap03_Primer_Script.md)
- [Capítulo 4 — Variables, Tipos y el Inspector](Cap04_Variables_Tipos.md)
- [Capítulo 5 — Métodos: Organizar el Código para que Escale](Cap05_Metodos.md)
- [Capítulo 6 — Input: El Sistema de Movimiento del Jugador](Cap06_Input_Movimiento.md)
- [Capítulo 7 — Física 3D: Colisiones, Rigidbody y Raycast](Cap07_Fisica_3D.md)
- [Capítulo 8 — La Cámara: Follow Camera en Tercera Persona](Cap08_Camara.md)
- [Capítulo 9 — Condicionales y el Bucle del Juego](Cap09_Condicionales.md)
- [Capítulo 10 — Arrays, Listas y Loops](Cap10_Arrays_Listas.md)
- [Capítulo 11 — Debugging: Leer Errores y Encontrar Bugs](Cap11_Debugging.md)
- [Capítulo 12 — Escenas: Arquitectura del Juego](Cap12_Escenas.md)

---

## Antes de empezar: configuración del proyecto

Antes del Capítulo 1, haz esto una vez:

1. Abre Unity Hub
2. Abre el proyecto (o crea uno nuevo con URP 3D si lo prefieres)
3. En el menú superior: **Edit → Preferences → External Script Editor** — elige Visual Studio Code o Rider
4. En **Edit → Project Settings → Player** — asegúrate de que el nombre del producto sea "Aphelion"
5. Crea esta carpeta: **Assets → Scripts** (clic derecho en Assets → Create → Folder → nombra "Scripts")
6. Crea esta carpeta: **Assets → Scenes**

Listo. Empecemos.

---

_Versión 1.0 — Generado como parte de la Aphelion Unity Developer Series_
