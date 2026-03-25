# Capítulo 1 — El Editor de Unity: Tu Entorno de Trabajo

---

## 1. Qué vas a construir

Al terminar este capítulo, tendrás la escena principal de Aphelion lista para trabajo: un plano de terreno en el centro del mundo, iluminado, con un GameObject vacío llamado "GameManager" que actúa como raíz lógica del juego.

No es mucho visualmente. Pero entenderás exactamente qué es cada cosa que ves en el editor y por qué está ahí. Eso es más valioso que tener algo bonito que no entiendes.

![PlayMode-Tint-Image](../Imgs/Volume1/Final-Cap1-Img.png)

---

## 2. El Por Qué

### Por qué el editor importa tanto

La mayoría de personas que aprenden Unity empiezan a copiar scripts de YouTube sin entender el entorno donde viven esos scripts. El resultado inevitable: cuando algo sale mal, no saben dónde mirar. Cuando quieren hacer algo diferente, no saben cómo navegarlo.

El editor de Unity no es una pantalla de presentación — es donde **vive tu juego mientras lo construyes**. Cada ventana es una lente diferente sobre la misma realidad. Entender qué ve cada ventana y cuándo usarla es la diferencia entre trabajar con Unity y pelear contra Unity.

### La arquitectura conceptual de Unity

Antes de tocar el editor, necesitas entender cómo Unity conceptualiza un juego. Todo en Unity existe en una de estas tres capas:

**1. El Proyecto** — Todo lo que existe en el disco duro. Scripts, texturas, modelos, sonidos, configuraciones. Esto es persistente. Existe aunque Unity esté cerrado.

**2. La Escena** — Una "instancia del mundo" que seleccionas del proyecto para ejecutar. Una escena es como una habitación: puedes tener muchas, pero solo una está activa a la vez (o varias si usas carga aditiva, que veremos en el Capítulo 12). Lo que está en la escena existe en memoria mientras el juego corre.

**3. El GameLoop** — El motor corriendo. Unity ejecuta tu juego llamando funciones específicas (Update, FixedUpdate, etc.) en cada frame. No tú. Unity. Tú solo defines qué ocurre cuando esas funciones son llamadas.

Esta distinción — Proyecto / Escena / GameLoop — es fundamental. Cuando algo "no aparece en el juego", generalmente es porque está en el Proyecto pero no fue añadido a la Escena. Cuando algo "desaparece al cerrar el juego", es porque existía en la Escena pero no fue guardado al Proyecto.

---

## 3. Las 5 ventanas del editor

### Scene View (Vista de Escena)

**Qué es:** La ventana principal donde colocas y manipulas objetos en tu mundo 3D. Es tu vista de arquitecto — ves el mundo desde un punto de vista flotante que tú controlas con el mouse y teclado, sin restricciones del juego.

**Para qué sirve:** Posicionar objetos, hacer ajustes visuales, diseñar niveles, ver colisionadores, ver luces, depurar visualmente.

**Atajos de navegación esenciales:**

- **Clic derecho + WASD:** Mover la cámara del editor en modo "vuelo libre" (la forma más rápida)
- **Alt + Clic izquierdo:** Orbitar alrededor del punto focal
- **Scroll del mouse:** Zoom in/out
- **F:** Enfocar en el objeto seleccionado (frame selected) — el más usado
- **Teclas Q/W/E/R/T:** Cambiar entre herramientas (mano/mover/rotar/escalar/rect)

**Error crítico que evitar:** Todo lo que muevas en la Scene View durante Play Mode se resetea al salir. No hagas ajustes de posición importantes en Play Mode. Más sobre esto en la sección "Errores comunes".

### Game View (Vista del Juego)

**Qué es:** Lo que verá el jugador cuando corra el juego. Renderiza desde la perspectiva de la cámara activa en la escena.

**Para qué sirve:** Verificar que el juego se ve como debe, probar el gameplay, verificar la UI en el tamaño correcto de pantalla.

**Detalle importante:** Puedes cambiar la resolución y el aspect ratio en el menú desplegable de la parte superior de esta ventana. Siempre prueba tu juego en la resolución que planeas soportar.

### Hierarchy (Jerarquía)

**Qué es:** La lista de todos los GameObjects que existen en la escena actualmente cargada.

**Para qué sirve:** Seleccionar objetos, ver relaciones padre-hijo entre objetos, reorganizar la estructura de la escena.

**Cómo leerla:** Los objetos con flecha tienen hijos. Los hijos están indentados. Un objeto hijo está "dentro" del espacio de transformación de su padre — su posición es relativa al padre, no al mundo. Esto importa enormemente y lo desarrollamos en el Capítulo 2.

### Project Window (Ventana de Proyecto)

**Qué es:** El explorador de archivos de tu proyecto. Muestra todo lo que está en la carpeta `Assets/` de tu proyecto en el disco.

**Para qué sirve:** Importar assets, crear scripts, organizar archivos, arrastrar cosas a la Escena o al Inspector.

**Estructura recomendada para Aphelion:**

```
Assets/
├── Scripts/        ← Todos tus scripts C#
├── Scenes/         ← Tus archivos de escena (.unity)
├── Materials/      ← Materiales creados por ti
├── Prefabs/        ← Prefabs del juego (Capítulo 2)
├── Audio/          ← Sonidos y música
├── UI/             ← Sprites e imágenes de interfaz
└── Documentation/  ← Esta documentación
```

### Inspector

**Qué es:** La ventana que muestra todas las propiedades del objeto seleccionado actualmente (ya sea un GameObject de la escena o un archivo del proyecto).

**Para qué sirve:** Ajustar valores de componentes, asignar referencias entre objetos, activar/desactivar componentes, ver y editar scripts en tiempo real.

**Concepto clave:** El Inspector es contextual. Cambia completamente dependiendo de qué tienes seleccionado. Selecciona un GameObject → ves sus componentes. Selecciona un script → ves el código fuente y sus metadatos. Selecciona una textura → ves sus opciones de importación.

---

## 4. El sistema de coordenadas 3D

Unity usa un sistema de coordenadas de mano izquierda:

- **X:** Derecha (+) / Izquierda (-)
- **Y:** Arriba (+) / Abajo (-)
- **Z:** Adelante (+) / Atrás (-)

Cuando posicionas un objeto en `(3, 0, 5)`, significa: 3 unidades a la derecha del origen, en el suelo, 5 unidades al frente.

Una **unidad de Unity** no tiene un tamaño físico obligatorio, pero la convención estándar es que **1 unidad = 1 metro**. Si sigues esta convención, la física, la IA de navegación y los colisionadores funcionarán con valores "naturales" sin ajustes complicados.

Para Aphelion: el protagonista medirá aproximadamente 1.8 unidades de alto. Un muro medirá 3 unidades. Una habitación tendrá unos 8×6 unidades. Estos números se sentirán "correctos" con los sistemas de física por defecto.

![PlayMode-Tint-Image](../Imgs/Volume1/PlayMode-Tint.png)

---

## 5. Play Mode vs Edit Mode

**Edit Mode:** Donde construyes el juego. Puedes modificar la escena, mover objetos, crear scripts, cambiar propiedades. Los cambios son permanentes.

**Play Mode:** Donde pruebas el juego. Unity compila, inicializa todos los sistemas y empieza a llamar a tu código. Puedes modificar valores en el Inspector para hacer ajustes rápidos — pero **todos esos cambios se pierden cuando sales del Play Mode**. La escena vuelve exactamente al estado que tenía antes de presionar Play.

Esto no es un bug. Es una función deliberada que te permite experimentar sin miedo a romper nada permanentemente. Pero si haces un cambio importante en Play Mode y no lo recuerdas, lo perderás. Desarrollarás el hábito de salir siempre del Play Mode antes de hacer cambios que quieras conservar.

**Indicador visual:** Cuando estás en Play Mode, la barra superior del editor se pone de un color diferente (gris oscuro por defecto, configurable en Preferences). Si no ves el cambio de color, ve a **Edit → Preferences → Colors** y activa el tint de Play Mode con un color visible.

---

## 6. Ejercicio guiado paso a paso

### Objetivo: Crear la escena base de Aphelion

**Paso 1: Crear la escena**

1. En la ventana **Project**, navega a `Assets/Scenes/`
2. Clic derecho → **Create → Scene**
3. Nombra la escena `Aphelion_MainLevel`
4. Doble clic en ella para abrirla

![alt text](../Imgs/Volume1/Aphelion-MainLevel-Img.png)
**Paso 2: Guardar la escena anterior**
Si Unity te pregunta si quieres guardar la escena anterior (`SampleScene`), haz clic en **Save**. Siempre guarda antes de cambiar de escena.
![alt text](../Imgs/Volume1/SampleScene-Save.png)

**Paso 3: Limpiar la jerarquía**
La nueva escena tiene solo una Main Camera y una Directional Light (en Unity 6, puede tener también un Global Volume). Por ahora dejamos estos objetos.

**Paso 4: Crear el terreno base**

1. En el menú superior: **GameObject → 3D Object → Plane**
2. Renombra el objeto: con el objeto seleccionado en la Hierarchy, presiona **F2** (o doble clic en el nombre) y escríbele `Terrain_Base`
3. En el Inspector, en el componente **Transform**, establece estos valores:
   - Position: `X: 0, Y: 0, Z: 0`
   - Rotation: `X: 0, Y: 0, Z: 0`
   - Scale: `X: 10, Y: 1, Z: 10`

El plano ahora mide 100×100 unidades (Unity crea planos de 10×10 unidades por defecto, la escala 10 lo lleva a 100×100).

![alt text](../Imgs/Volume1/Plane-Img.png)

**Paso 5: Crear la jerarquía organizada**

1. En la Hierarchy, clic derecho → **Create Empty**
2. Renómbralo `World`
3. Arrastra `Terrain_Base` dentro de `World` (suéltalo encima del nombre "World")
4. Crea otro objeto vacío: clic derecho en un espacio vacío de la Hierarchy → **Create Empty**, nombre `Systems`
5. Crea otro: nombre `Characters`
6. Crea otro: nombre `UI`

Tu jerarquía debe verse así:

```
Main Camera
Directional Light
World
  └── Terrain_Base
Systems
Characters
UI
```

![alt text](../Imgs/Volume1/Organized-Hierarchy.png)

**Paso 6: Crear el GameManager**

1. Clic derecho en `Systems` → **Create Empty**
2. Nombre: `GameManager`
3. Verifica en el Inspector que su Transform está en `(0, 0, 0)` — los GameObjects vacíos usados como contenedores lógicos siempre deben estar en el origen

![alt text](../Imgs/Volume1/GameManager-Img.png)

**Paso 7: Ajustar la luz**

1. Selecciona `Directional Light` en la Hierarchy
2. En el Inspector, busca el componente **Light**
3. Cambia **Color** a un blanco ligeramente azulado (R:210, G:220, B:255) — da un ambiente nocturno/místico apropiado para Aphelion
4. **Intensity:** `0.8`
5. **Shadow Type:** `Soft Shadows`

![alt text](../Imgs/Volume1/Directional-Light-Conf.png)

**Paso 8: Posicionar la cámara**

1. Selecciona `Main Camera`
2. Transform → Position: `X: 0, Y: 5, Z: -10`
3. Transform → Rotation: `X: 20, Y: 0, Z: 0`

![alt text](../Imgs/Volume1/Main-Camera-Conf.png)

**Paso 9: Guardar**

- **Ctrl+S** para guardar la escena

**Paso 10: Entrar y salir del Play Mode**

1. Presiona el botón **Play** (triángulo) en la barra superior
2. Observa el cambio de color de la interfaz

![alt text](../Imgs/Volume1/Play-Mode-Test-1.png)

3. En la Scene View, intenta hacer clic y arrastrar un objeto (por ejemplo, la Main Camera)

![alt text](../Imgs/Volume1/Play-Mode-Test-2.png)

4. Sal del Play Mode (presiona Play de nuevo o Ctrl+P)
5. Verifica que el objeto que moviste volvió a su posición original

![alt text](../Imgs/Volume1/Play-Mode-Test-3.png)

---

## 7. Qué acaba de pasar

Acabas de hacer varias cosas importantes sin que parezcan importantes todavía:

1. **Organizaste la jerarquía** — La estructura `World / Systems / Characters / UI` no es capricho. Es la arquitectura que usaremos en todos los capítulos. Cada nuevo sistema va en el lugar correcto desde el inicio.

2. **Estableciste el origen** — Colocar `Terrain_Base` en `(0,0,0)` significa que "el centro del mundo es el centro del terreno". Todos los sistemas de posición relativos funcionarán predeciblemente desde aquí.

3. **Experimentaste con Play Mode** — El objeto que moviste dentro del Play Mode volvió a su lugar. Eso no es magia. Unity toma un snapshot del estado de la escena antes de hacer Play, y lo restaura al salir. El Play Mode es un entorno de prueba seguro.

4. **Estableciste el tono visual** — La luz azulada suave no es solo estética. En Aphelion, la oscuridad y el ambiente son parte del diseño. Empezar con una luz apropiada desde el inicio evita el hábito de "lo arreglo después".

---

## 8. Errores comunes

| Error                                       | Causa                                                                                                 | Solución                                                                                                     |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| "Moví un objeto y desapareció"              | Estabas en Play Mode sin darte cuenta                                                                 | Siempre verifica el color de la barra superior. Sal del Play Mode con Ctrl+P antes de hacer cambios          |
| "No encuentro el objeto que acabo de crear" | Se creó pero la cámara del editor no lo apunta, o está oculto en la jerarquía                         | Selecciónalo en la Hierarchy y presiona **F** para enfocar la Scene View en él                               |
| "El plano es gigante / muy pequeño"         | La escala en Unity es multiplicativa. Un Plane de 10×10 con Scale 10 mide 100×100                     | Siempre verifica el Scale en el Transform. Una escala de `(1,1,1)` significa "tamaño original sin modificar" |
| "Guardé pero los cambios se perdieron"      | Guardaste dentro del Play Mode — esos cambios se revierten siempre                                    | Guarda solo en Edit Mode                                                                                     |
| "El Inspector está vacío"                   | No tienes nada seleccionado, o tienes seleccionado un archivo del Project (no un objeto de la escena) | Haz clic en un objeto de la Hierarchy para seleccionarlo                                                     |

---

## 9. Retos independientes

### Reto 1 — Crear una segunda plataforma elevada

Crea un plano adicional dentro de `World`, nombrado `Platform_Elevated`, posicionado a `(0, 5, 20)` y con escala `(2, 1, 2)`. Debe parecer una plataforma pequeña flotando sobre el terreno base.

**Pista 1:** ¿Qué valores de Transform necesita un objeto para estar "encima" de otro? ¿Qué eje controla la altura?

> El eje y controla la altura

**Pista 2:** La altura se controla con el eje Y. Una Position de `Y: 5` coloca el objeto 5 unidades por encima del suelo. La escala `(2, 1, 2)` lo hará el doble de ancho/largo que un plano estándar.

**Pista 3:**

```
Transform:
  Position: X:0  Y:5  Z:20
  Rotation: X:0  Y:0  Z:0
  Scale:    X:2  Y:1  Z:2
```

![alt text](../Imgs/Volume1/Challenge-1.png)

---

### Reto 2 — Explorar la ventana de Preferences

En **Edit → Preferences**, cambia el color de tint del Play Mode a algo claramente visible (rojo, morado, etc.) para que nunca accidentalmente edites en Play Mode sin darte cuenta.

**Pista 1:** Busca la sección "Colors" dentro de Preferences. ¿Qué opción mencionamos en el capítulo tiene relación con el modo de juego?

**Pista 2:** La opción se llama "Playmode tint". Es un color con alpha (transparencia) — ponle alpha alto para que sea visible.

**Pista 3:** Edit → Preferences → Colors → "Playmode tint" → Elige un color (por ej. rojo con Alpha 128).

![PlayMode-Tint-Image](../Imgs/Volume1/PlayMode-Tint.png)

---

### Reto 3 — Nombrar correctamente los objetos de la escena

Sin mirar el ejercicio guiado, crea desde cero una jerarquía de escena con: `World`, `Systems`, `Characters`, `UI`, y dentro de `Systems` un `GameManager`. Hazlo de memoria.

Este reto no tiene pistas — es puro ejercicio de memoria. Si no lo recuerdas, relee la sección del ejercicio guiado hasta que puedas hacerlo sin referencia. La estructura de la jerarquía es tan fundamental que debe ser automática.

---

## 10. Resumen del capítulo

**Ventanas del editor:**

- `Scene View` — Trabajar visualmente en el mundo
- `Game View` — Ver el juego desde los ojos del jugador
- `Hierarchy` — Lista de GameObjects en la escena activa
- `Project Window` — Explorador de archivos del proyecto
- `Inspector` — Propiedades del objeto seleccionado

**Conceptos:**

- Proyecto vs Escena vs GameLoop
- Sistema de coordenadas 3D (X derecha, Y arriba, Z adelante)
- Play Mode (temporal) vs Edit Mode (permanente)
- Convención de escala: 1 unidad = 1 metro
- F para enfocar un objeto seleccionado en la Scene View

**Atajos:**

- `Ctrl+S` — Guardar escena
- `Ctrl+P` — Entrar/salir del Play Mode
- `F` — Enfocar objeto seleccionado
- `Q/W/E/R/T` — Herramientas del editor
- `F2` — Renombrar objeto en la Hierarchy

---

## 11. Glosario

**GameObject:** La unidad básica de todo en Unity. No es un objeto con forma ni con comportamiento por sí mismo — es un contenedor al que se le adjuntan Componentes. Un GameManager sin Componentes es perfectamente válido como objeto de organización.

**Componente:** Una pieza de funcionalidad que se adjunta a un GameObject. Transform, Light, Camera — todos son Componentes. Un GameObject sin Componentes (aparte del Transform que tienen todos) es un objeto vacío, útil para organización.

**Transform:** El único Componente que todos los GameObjects tienen siempre, sin excepción. Almacena posición, rotación y escala del objeto. Si eliminas todos los demás Componentes, el Transform permanece.

**Escena:** Un archivo `.unity` que contiene la instantánea de un estado del mundo del juego: qué GameObjects existen, dónde están, qué Componentes tienen y con qué valores.

**Play Mode:** El estado en que Unity corre el juego activamente. Los cambios hechos aquí son temporales y se revierten al salir. En Aphelion, usaremos el Play Mode constantemente para probar que los sistemas funcionan correctamente.

**Edit Mode:** El estado normal del editor donde construyes el juego. Los cambios son permanentes (se guardan con Ctrl+S).

**Origin / Origen:** El punto `(0, 0, 0)` en el espacio 3D. El centro matemático del mundo. Colocar el terreno principal en el origen es una convención que facilita todos los cálculos de posición posteriores.
