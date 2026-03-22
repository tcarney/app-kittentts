# KittenTTS

A local text-to-speech app for Home Assistant using [KittenTTS](https://github.com/KittenML/KittenTTS) (StyleTTS2-based, ONNX). Lightweight models (15M–80M parameters) run on CPU without a GPU.

## Installation

1. In Home Assistant, go to **Settings > Add-ons > Add-on Store**
2. Click the three-dot menu (top right) and select **Repositories**
3. Add: `https://github.com/tcarney/app-kittentts`
4. The **KittenTTS** app will appear in the store

## Configuration

Install the app and optionally change settings in the **Configuration** tab:

| Option | Description | Default |
|---|---|---|
| `model` | HuggingFace model ID | `KittenML/kitten-tts-mini-0.8` |
| `voice` | Default voice name | `Jasper` |
| `debug` | Enable debug logging | `false` |

The model downloads from HuggingFace on first start and is cached for subsequent starts.

### Available Models

| Model | Params | Size | HuggingFace ID |
|---|---|---|---|
| kitten-tts-mini | 80M | ~80MB | `KittenML/kitten-tts-mini-0.8` |
| kitten-tts-micro | 40M | ~41MB | `KittenML/kitten-tts-micro-0.8` |
| kitten-tts-nano | 15M | ~56MB | `KittenML/kitten-tts-nano-0.8-fp32` |
| kitten-tts-nano-int8 | 15M | ~25MB | `KittenML/kitten-tts-nano-0.8-int8` |

### Available Voices

Bella, Jasper, Luna, Bruno, Rosie, Hugo, Kiki, Leo

## Connect to Voice Assistant

The app advertises itself via Zeroconf (mDNS), so Home Assistant should auto-discover it. If not:

1. Go to **Settings > Devices & Services > Add Integration**
2. Select **Wyoming Protocol**
3. Enter `localhost` and port `10200`

KittenTTS will appear as a TTS provider in your Voice Assistant pipeline.
