# Antigravity Token Efficient

Reduces output token usage in [Google Antigravity](https://antigravity.google) (Gemini & Claude) by ~80%. One-click installer. Drop-in, no code changes.

---

## 🇺🇸 English

### The Problem

By default, AI models in Antigravity:
- Open every response with "Sure!", "Great question!", "Absolutely!"
- End with "I hope this helps! Let me know if you need anything!"
- Use em-dashes, smart quotes, Unicode characters
- Restate your question before answering
- Add unsolicited suggestions beyond what you asked

All of this wastes tokens. None of it adds value.

### Benchmark Results

Same prompt: *"What does bot.py do?"*

| | Without Rules | With Rules |
|---|---|---|
| Words | ~400 | ~70 |
| Reduction | — | **~82%** |
| Numbered sections | 5 | 0 |
| Filler phrases | Yes | No |

**Same information. Zero signal loss. ~80% fewer output tokens.**

### Before (without rules)

```
Great question! 😊 I can see you're working with a really interesting project.
Let me take a look at that file for you. The bot.py file is the main engine
of your Clash of Clans automation bot. It handles the complete lifecycle...
[400+ words with 5 numbered sections, greetings, and filler]
...I hope this helps! Feel free to ask if you need anything else! 🚀
```

### After (with rules)

```
bot.py is the main automation script for Clash of Clans. Connects to
BlueStacks via ADB, captures screen with OpenCV for template matching,
trains troops, searches for villages meeting resource thresholds in
config.json, and launches attacks via ataque.py.
```

### Installation

#### Option 1: One-Click Installer (Recommended)

1. Download `install_rules_EN.bat`
2. Double-click it
3. Done. Rules are installed globally for all projects.

#### Option 2: Manual

Copy the contents of [`GEMINI.md`](GEMINI.md) to:

```
C:\Users\<YourUsername>\.gemini\GEMINI.md
```

Create the `.gemini` folder if it doesn't exist.

### How It Works

Antigravity reads `GEMINI.md` from `~/.gemini/` at the start of every conversation. The rules instruct the model to:

- Skip greetings, farewells, and filler
- Respond in 2-3 lines for simple questions
- Never restate the user's question
- Never give unsolicited suggestions
- Go straight to the result

Works with all models available in Antigravity (Gemini, Claude, etc.).

### When This Helps vs When It Doesn't

**Works best for:**
- Regular coding sessions with high output volume
- Repeated structured tasks where verbosity compounds

**Not worth it for:**
- Single short queries (the file adds input tokens every message)
- Exploratory work where detailed explanations are the point

### Override Rule

User instructions always win. If you explicitly ask for a detailed explanation, the model follows your instruction. The rules never fight you.

### Uninstall

Delete `C:\Users\<YourUsername>\.gemini\GEMINI.md` or clear its contents.

---

## 🇪🇸 Español

### El Problema

Por defecto, los modelos de IA en Antigravity:
- Abren cada respuesta con "¡Excelente pregunta!", "¡Claro!", "¡Por supuesto!"
- Terminan con "¡Espero que esto ayude! ¡No dudes en preguntar!"
- Usan guiones largos, comillas tipográficas, caracteres Unicode
- Repiten tu pregunta antes de responder
- Agregan sugerencias no solicitadas

Todo eso gasta tokens. Nada de eso agrega valor.

### Resultados del Benchmark

Mismo prompt: *"¿Qué hace bot.py?"*

| | Sin Reglas | Con Reglas |
|---|---|---|
| Palabras | ~400 | ~70 |
| Reducción | — | **~82%** |
| Secciones numeradas | 5 | 0 |
| Frases de relleno | Sí | No |

**Misma información. Cero pérdida de señal. ~80% menos tokens de salida.**

### Antes (sin reglas)

```
¡Excelente pregunta! 😊 Puedo ver que estás trabajando en un proyecto muy
interesante. Déjame revisar ese archivo por ti. El archivo bot.py es el motor
principal de tu bot de automatización...
[400+ palabras con 5 secciones numeradas, saludos y relleno]
...¡Espero que esto te haya sido de ayuda! ¡No dudes en preguntar! 🚀
```

### Después (con reglas)

```
bot.py es el script principal de automatización de Clash of Clans. Se conecta
a BlueStacks via ADB, captura la pantalla con OpenCV para template matching,
entrena tropas, busca aldeas que cumplan los umbrales de recursos en
config.json, y lanza ataques via ataque.py.
```

### Instalación

#### Opción 1: Instalador de un clic (Recomendado)

1. Descargá `install_rules_ES.bat`
2. Doble clic
3. Listo. Las reglas se instalan globalmente para todos los proyectos.

#### Opción 2: Manual

Copiá el contenido de [`GEMINI.md`](GEMINI.md) a:

```
C:\Users\<TuUsuario>\.gemini\GEMINI.md
```

Creá la carpeta `.gemini` si no existe.

### Cómo Funciona

Antigravity lee `GEMINI.md` desde `~/.gemini/` al inicio de cada conversación. Las reglas le indican al modelo:

- No usar saludos, despedidas ni relleno
- Responder en 2-3 líneas para preguntas simples
- Nunca repetir la pregunta del usuario
- Nunca dar sugerencias no solicitadas
- Ir directo al resultado

Funciona con todos los modelos disponibles en Antigravity (Gemini, Claude, etc.).

### Cuándo Sirve y Cuándo No

**Funciona mejor para:**
- Sesiones de código regulares con alto volumen de salida
- Tareas estructuradas repetitivas donde la verbosidad se acumula

**No vale la pena para:**
- Consultas cortas individuales (el archivo agrega tokens de entrada en cada mensaje)
- Trabajo exploratorio donde las explicaciones detalladas son el objetivo

### Regla de Anulación

Las instrucciones del usuario siempre ganan. Si pedís una explicación detallada, el modelo sigue tu instrucción. Las reglas nunca te pelean.

### Desinstalar

Borrá `C:\Users\<TuUsuario>\.gemini\GEMINI.md` o vaciá su contenido.

---

## Files / Archivos

| File / Archivo | Description / Descripción |
|---|---|
| `GEMINI.md` | Rules file (reference) / Archivo de reglas (referencia) |
| `install_rules_EN.bat` | One-click installer (English) / Instalador (inglés) |
| `install_rules_ES.bat` | One-click installer (Spanish) / Instalador (español) |

## Credits / Créditos

Inspired by / Inspirado en [claude-token-efficient](https://github.com/drona23/claude-token-efficient) by Drona Gangarapu. Adapted for Google Antigravity.

## License / Licencia

MIT - free to use, modify, and distribute.
