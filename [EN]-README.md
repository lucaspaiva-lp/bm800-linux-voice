[![PT-BR](https://img.shields.io/badge/lang-PT--BR-green?style=for-the-badge&logo=google-translate)](https://github.com/lucaspaiva-lp/bm800-linux-voice)
[![EN](https://img.shields.io/badge/lang-EN-blue?style=for-the-badge&logo=google-translate)](https://github.com/lucaspaiva-lp/bm800-linux-voice/blob/main/%5BEN%5D-README.md)


# 🎙️ BM-800 Linux Audio Voice Pro: Presets for EasyEffects

This repository contains audio profiles configured for **EasyEffects** (PipeWire), specifically created to tame the characteristics of the **BM-800** condenser microphone when used **directly on a PC, without a 48V Phantom Power supply or audio interface**.

Since the BM-800 requires extra power to operate at full capacity, plugging it directly into the motherboard causes it to lose most of its natural capture and gain. This results in high-pitched, "metallic" audio with significant background static noise (*hiss*).

The goal of these presets is to digitally compensate for this hardware deficiency: delivering a clean sound with "radio voice" presence, and isolating mechanical keyboard and mouse noises without clipping the voice.

---

## 📁 Files and Repository Structure

* **`/presets` folder**: Contains the configuration files in **`.json`** format.
* **`/images` folder**: Contains screenshots of each configured plugin. Use these images as a visual guide to check if parameters were loaded correctly or to configure them manually if you prefer.

---

### Available Presets:

* **`BM-800 (Natural + Equalize + Deeser + RNoiser).json`** : 🏆 **(Recommended)** Full version with Noise Reduction (RNNoise) for environments with heavy constant noise (fans, air conditioning).
* **`BM-800 (Natural + Equalize + Deeser).json`** : Focuses on adding body to the voice (gain at 126-194Hz), removing the metallic shimmer, and smoothing out "S" sounds (Deesser).
* **`BM-800.json`** : The base equalization profile.
* **`BM-800 (Natural + Equalize) [NO SUPPRESSOR].json`** : Focuses only on voice body and removing the "tin can" sound, ideal for quiet or acoustically treated environments.
* **`BM-800 (Natural + No suppressor).json`** : Lightweight configuration without aggressive noise suppression.

> *Note: You are free to disable individual filters directly within the EasyEffects interface as needed.*

---

## 🐧 Linux Compatibility and Dependencies

This setup is compatible with **any Linux distribution** using the **PipeWire** audio server.

**Warning:** EasyEffects is just the "host" for the effects. In most distros, **the filters are not pre-installed**. For the profile to work and the plugins (Equalizer, Expander, Deesser, Limiter) to appear, you must install the LV2 plugin packages.

Example installation on Arch Linux / EndeavourOS:

```bash
sudo pacman -S easyeffects lsp-plugins calf rnnoise
```

*(Ubuntu, Fedora, Mint, or Pop!_OS users should look for equivalent packages like `lsp-plugins` and `calf-plugins` in their respective package managers).*

---

## 🚀 How to Install and Configure

1. Download the `.json` files from the `/presets` folder.
2. Open EasyEffects -> **PipeWire** tab ->  **Presets** .
3. Click the **Import** button and select the downloaded `.json` files.
4. Select the desired preset from the list and click  **Load** .
5. **Visual Tip:** Check the `/images` folder in this repository to compare graphs and ensure the effects are active.

---

## 🎮 Usage Tips (CS2, Discord, etc.)

* **System-wide:** EasyEffects creates a virtual microphone. Ensure that **"EasyEffects Source"** is selected as the default input device in your system audio settings (KDE/Gnome).
* **Discord:** Go to *Voice & Video* and disable **all** native processing options (Noise Suppression, Echo Cancellation, Automatic Gain Control). Discord will "fight" with EasyEffects if these are not turned off.
* **Counter-Strike / Source Engine:** Valve games often force microphone volume changes, which can mess up your filters. Add the following lines to your `autoexec.cfg` to prevent this:
  **Snippet de código**

  ```
  voice_mixer_boost_low_mic "0"
  voice_mixer_volume "1.0" 
  ```

---

## 🪟 Alternative for Windows Users (VoiceMeeter)

EasyEffects is software built exclusively for the Linux audio architecture. If you are using **Windows** and suffer from the same BM-800 issues without Phantom Power, the best free tool to apply filters and enhance your voice is  **VoiceMeeter Banana** .

To set this up from scratch and even separate your PC audio (Discord, Spotify, Games), we recommend following this tutorial:
▶️ [HOW TO CONFIGURE VOICEMEETER BANANA AND SEPARATE AUDIO TRACKS](https://www.youtube.com/watch?v=0EjDL3BgPk4&t=209s).

---

## 💬 Doubts, Suggestions or Help?

If you have trouble installing, find a bug, or want to share an equalization improvement, our **Discussions** tab is open!

👉 [Access the Community Forum here](https://github.com/lucaspaiva-lp/bm800-linux-voice/discussions)

> Pull requests and improvement suggestions are welcome! Let's improve the Linux community's audio together. 💪
