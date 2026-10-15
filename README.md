# 🪙 Taller 6: Sistema de Recolección de Monedas y Contador UI con ChatGPT

Proyecto de Unity 6 (2D) donde el personaje recolecta monedas por el nivel y un contador en pantalla se actualiza en tiempo real. Los scripts `Coin.cs` y `CoinUI.cs` se generaron aplicando **Prompt Engineering con ChatGPT**.

## 🎯 Objetivo

Aplicar Prompt Engineering con ChatGPT para generar un sistema completo de recolección de ítems y actualización de interfaz UI, sin escribir el código C# desde cero.

## 🎬 Video de demostración

El video **`VIDEOTALLER6.mp4`** se encuentra en la **raíz de este repositorio** para su revisión.

[▶️ Ver video de demostración](VIDEOTALLER6.mp4)

Muestra al personaje recolectando monedas mientras el contador en pantalla pasa de `Monedas: 0` a 1, 2, 3 en tiempo real.

## ✅ Cumplimiento de requisitos

| Requisito | Dónde se cumple |
|-----------|-----------------|
| Sprite de moneda en la escena | Hoja de animación de la moneda en `Assets/Sprites` |
| Collider con **Is Trigger** marcado | `CircleCollider2D` en el Prefab de la moneda |
| Moneda convertida en Prefab, mínimo 5 en el nivel | `Assets/Prefabs` |
| Texto UI "Monedas: 0" en la esquina superior derecha | Objeto `TextoMonedas` dentro del Canvas |
| Script `Coin.cs` (detecta, suma y destruye la moneda) | `Assets/Script/Coin.cs` |
| Script `CoinUI.cs` (actualiza el texto) | `Assets/Script/CoinUI.cs` |
| Prompt a ChatGPT | Sección de abajo |
| Video de demostración | `VIDEOTALLER6.mp4` (raíz del repo) |

## 🧩 Cómo funciona

### Moneda (`Coin.cs`)
- Está en el Prefab de la moneda, que tiene un `CircleCollider2D` con **Is Trigger** activado.
- Usa `OnTriggerEnter2D`: si el objeto que entra tiene el tag `Player`, suma 1 al contador estático `monedasRecogidas` y se elimina con `Destroy(gameObject)`.
- El contador es `static`, así todas las monedas comparten el mismo número.

### Interfaz (`CoinUI.cs`)
- Está en el objeto de texto `TextoMonedas` del Canvas.
- Lee el contador de `Coin` y actualiza el texto con el formato `Monedas: X`.
- Reinicia el contador a 0 al iniciar el nivel.

### Conexión en el Inspector
1. El personaje tiene el tag `Player`, un `Rigidbody2D` y un collider sin Is Trigger.
2. `Coin.cs` está en el Prefab de la moneda.
3. `CoinUI.cs` está en `TextoMonedas`, con ese mismo objeto arrastrado al campo **Texto Monedas**.

## 🤖 Prompt usado en ChatGPT

```
Estoy haciendo un juego 2D en Unity 6 con C#. Necesito un sistema de monedas.

1. Un script llamado Coin.cs para el Prefab de la moneda. La moneda tiene un
   Circle Collider 2D con Is Trigger activado. Cuando el personaje (tag "Jugador")
   la toque, debe aumentar un contador estático de monedas y destruir la moneda
   con Destroy(gameObject).

2. Un script llamado CoinUI.cs que actualice un texto TextMeshPro en la esquina
   superior derecha con el formato "Monedas: X", leyendo el contador de Coin.cs.
   El contador debe reiniciarse a 0 al empezar el nivel.

Requisitos:
- Usa nombres de variables en español.
- Código sencillo con comentarios cortos, para alguien que está aprendiendo.
- Explícame paso a paso qué debo arrastrar en el Inspector para conectarlo todo.
```

**Resultado:** ChatGPT generó los scripts `Coin.cs` y `CoinUI.cs`, junto con las instrucciones para conectarlos en el Inspector. Se copiaron a Unity y se ajustaron para que funcionaran con el proyecto.

## 🧱 Prefab

- La moneda se guardó como Prefab en `Assets/Prefabs`.
- Se colocaron varias copias distribuidas por el nivel. Si se modifica el Prefab, todas las copias se actualizan.

## 📁 Estructura del repositorio

```
Assets/
├── Prefabs/        → Moneda
├── Script/         → Coin.cs, CoinUI.cs, y scripts del personaje
├── Scenes/         → Nivel_1
├── Animations/
└── Sprites/
VIDEOTALLER6.mp4    → video de demostración
```

## ▶️ Cómo probarlo

1. Clonar el repositorio y abrirlo con **Unity 6**.
2. Abrir la escena `Nivel_1` en `Assets/Scenes`.
3. Dar **Play** y recoger las monedas con el personaje.
4. Ver cómo el contador de la esquina superior derecha sube con cada moneda.

## 🛠️ Tecnologías

- Unity 6 (2D, Universal Render Pipeline)
- C#
- TextMeshPro
- ChatGPT (generación de código con prompts)

## 👤 Autor

**Edwin Cusin** — Estudiante / Coder: **edwindev**
