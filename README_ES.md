# Antigravity Token Efficient

Instalador de un clic. Reduce la verbosidad en [Google Antigravity](https://antigravity.google) (asistente de IA para código en VS Code). Sin cambios de código.

**[Read in English](README.md)**

---

## El Problema

Por defecto, los modelos de IA en Antigravity:
- Abren cada respuesta con "¡Excelente pregunta!", "¡Claro!", "¡Por supuesto!"
- Terminan con "¡Espero que esto ayude! ¡No dudes en preguntar!"
- Usan guiones largos, comillas tipográficas, caracteres Unicode
- Repiten tu pregunta antes de responder
- Agregan sugerencias no solicitadas
- Sobre-diseñan código con abstracciones que nunca pediste

Todo eso gasta tokens. Nada de eso agrega valor.

## Resultados del Benchmark

Mismo prompt: *"¿Qué hace bot.py?"*

| | Sin Reglas | Con Reglas |
|---|---|---|
| Palabras | ~400 | ~70 |
| Reducción | — | **~82%** |
| Secciones numeradas | 5 | 0 |
| Frases de relleno | Sí | No |
| Sugerencias no pedidas | Sí | No |

**Misma información. Cero pérdida de señal. ~80% menos tokens de salida.**

### Antes (sin reglas)

```
¡Excelente pregunta! 😊 Puedo ver que estás trabajando en un proyecto muy
interesante. Déjame revisar ese archivo por ti. El archivo bot.py es el motor
principal de tu bot de automatización de Clash of Clans. Maneja el ciclo
completo... [400+ palabras con 5 secciones numeradas, saludos y relleno]
...¡Espero que esto te haya sido de ayuda! ¡No dudes en preguntar! 🚀
```

### Después (con reglas)

```
bot.py es el script principal de automatización de Clash of Clans. Se conecta
a BlueStacks via ADB, captura la pantalla con OpenCV para template matching,
entrena tropas, busca aldeas que cumplan los umbrales de recursos en
config.json, y lanza ataques via ataque.py.
```

## Instalación

### Opción 1: Instalador de un clic (Recomendado)

1. Descargá `install_rules_ES.bat`
2. Doble clic
3. Listo. Las reglas se instalan globalmente para todos los proyectos.

### Opción 2: Manual

Copiá el contenido de [`GEMINI.md`](GEMINI.md) a:

```
C:\Users\<TuUsuario>\.gemini\GEMINI.md
```

Creá la carpeta `.gemini` si no existe.

## Cómo Funciona

Antigravity lee `GEMINI.md` desde `~/.gemini/` al inicio de cada conversación. Las reglas en este archivo le indican al modelo:

- No usar saludos, despedidas ni relleno
- Responder en 2-3 líneas para preguntas simples
- Nunca repetir la pregunta del usuario
- Nunca dar sugerencias no solicitadas
- Ir directo al resultado

Las reglas son agnósticas del modelo y funcionan con todos los disponibles en Antigravity (Gemini, Claude, etc.).

## Archivos

| Archivo | Descripción |
|---|---|
| `GEMINI.md` | El archivo de reglas (copia de referencia) |
| `install_rules_EN.bat` | Instalador de un clic (reglas en inglés) |
| `install_rules_ES.bat` | Instalador de un clic (reglas en español) |

## Cuándo Sirve y Cuándo No

**Funciona mejor para:**
- Sesiones de código regulares con alto volumen de salida
- Tareas estructuradas repetitivas donde la verbosidad se acumula
- Equipos que necesitan salida consistente y parseable

**No vale la pena para:**
- Consultas cortas individuales (el archivo agrega tokens de entrada en cada mensaje)
- Trabajo exploratorio donde las explicaciones detalladas son el objetivo

## Regla de Anulación

Las instrucciones del usuario siempre ganan. Si pedís explícitamente una explicación detallada, el modelo sigue tu instrucción. Las reglas nunca te pelean.

## Desinstalar

Borrá `C:\Users\<TuUsuario>\.gemini\GEMINI.md` o vaciá su contenido.

## Créditos

Inspirado en [claude-token-efficient](https://github.com/drona23/claude-token-efficient) por Drona Gangarapu. Adaptado para Google Antigravity.

## Licencia

MIT - libre para usar, modificar y distribuir.
