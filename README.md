# 🎙️ Presets EasyEffects para Microfone BM-800 (Sem Phantom Power)

Este repositório contém perfis de áudio configurados para o **EasyEffects** (PipeWire), criados especificamente para domar as características do microfone condensador **BM-800** quando utilizado **diretamente no PC, sem uma fonte de alimentação Phantom Power (48V) ou interface de áudio**.

Como o BM-800 é um microfone que requer energia extra para operar com força total, ligá-lo direto na placa-mãe faz com que ele perca boa parte da sua capacidade natural de captação e ganho. Isso resulta em um áudio muito agudo, com som "metálico" e com bastante ruído estático de fundo (*hiss*). 

O objetivo destes presets é compensar digitalmente essa deficiência de hardware: entregando um som limpo, com peso de "locução de rádio", e isolando ruídos de teclado mecânico e mouse sem picotar a voz.

## 🐧 Compatibilidade Linux e Dependências

Esta configuração é compatível com **qualquer distribuição Linux** que utilize o servidor de áudio **PipeWire**.

**Atenção:** O EasyEffects é apenas o "hospedeiro" dos efeitos. Na grande maioria das distros, **os filtros não vêm pré-baixados**. Para que o perfil funcione e os plugins (Equalizador, Expander, Deesser, Limiter) apareçam na sua tela, você deve instalar os pacotes de plugins LV2 no seu sistema.

Exemplo de instalação no Arch Linux / EndeavourOS:
```bash
sudo pacman -S easyeffects lsp-plugins calf rnnoise
```

*(Usuários de Ubuntu, Fedora, Mint ou Pop!_OS devem procurar pelos pacotes equivalentes, como `lsp-plugins` e `calf-plugins`, em seus respectivos gerenciadores de pacotes).*

## 📁 Arquivos Disponíveis

No diretório principal, você encontrará variações do preset para diferentes necessidades:

* **`BM-800.json`** : O perfil base.
* **`BM-800 (Natural + Equalize + Deeser).json`** : Foco em encorpar a voz (ganho em 126-194Hz), remover o brilho metálico (corte gradual de 6kHz até 18kHz) e suavizar os "S" da fala. Usa um Expander suave para mutar o teclado quando não há fala.
* **`BM-800 (Natural + Equalize + Deeser + RNoiser).json`** : *(Recomendado)*  Versão com o plugin Noise Reduction ativado para ambientes com ruído constante e pesado (como ventiladores de teto ou ar-condicionado).
* **`BM-800 (Natural + Equalize) [SEM SUPRESSOR].json`** : Foco apenas no peso da voz e remoção do som de lata, ideal para quem grava em ambientes muito silenciosos ou com tratamento acústico.
* **`BM-800 (Natural + Sem supressor).json`** : Configuração mais leve, sem atuação extrema contra ruídos.

> De toda forma, você tem a liberdade de desativa no próprio EasyEffects, caso deseje. 

## ⚙️ A Cadeia de Filtros (Pipeline)

A mágica acontece (principalmente no preset recomendado) através da seguinte ordem de plugins:

1. **High-pass Filter (100Hz):** Corta o "pum" dos graves extremos e estalos de vento que a placa-mãe não consegue filtrar.
2. **Expander:** Atua como um silenciador inteligente. Configurado com Threshold em -36dB a -40dB e Ratio alto (5.0) para matar o barulho do teclado mecânico enquanto você não fala.
3. **Equalizer (32 Bandas):** Traz o corpo da voz (Médios-Graves) e aplica reduções pesadas nas altas frequências para matar o *hiss* natural gerado pela falta do Phantom Power.
4. **Deesser:** Segura os chiados em palavras com "S" ou "X" de forma natural (Threshold -18dB / Laxity 15ms).
5. **Loudness Limiter:** O escudo final. Trava picos sonoros (como palmas ou gritos) para não estourar os ouvidos de quem escuta.

## 🚀 Como Instalar no Linux

1. Certifique-se de ter o EasyEffects e os `lsp-plugins` instalados.
2. Baixe os arquivos `.json` deste repositório.
3. Abra o EasyEffects.
4. Vá até a aba **PipeWire** -> **Predefinições** (Presets).
5. Clique no botão de **Importar** e selecione os arquivos `.json`.
6. Selecione o preset desejado na lista e clique em **Carregar** (Load).

## 🪟 Alternativa para Usuários de Windows

O EasyEffects é um software construído exclusivamente para a arquitetura de áudio do Linux. Se você está utilizando **Windows** e sofre com o mesmo problema no BM-800 sem Phantom Power, a melhor ferramenta gratuita para aplicar filtros e encorpar a voz é o  **VoiceMeeter Banana** .

O VoiceMeeter atua como uma mesa de som virtual, onde você pode equalizar os graves, adicionar gates para ruído de teclado e melhorar consideravelmente o som do BM-800.

Para realizar essa configuração do zero e ainda separar o áudio do seu PC (Discord, Spotify, Jogos), recomendamos seguir este tutorial:
▶️ [COMO CONFIGURAR VOICEMEETER BANANA E SEPARAR FAIXAS DE ÁUDIO](https://www.youtube.com/watch?v=0EjDL3BgPk4&t=209s) (A partir de [03:29]).

## 🎮 Dicas de Uso (CS2, Discord, etc)

Para que o áudio filtrado funcione corretamente em jogos e aplicativos de comunicação no Linux:

* **No Sistema:** O EasyEffects cria um microfone virtual. Certifique-se de que o **"EasyEffects Source"** está selecionado como o dispositivo de entrada padrão nas configurações de áudio do sistema.
* **Discord:** Vá em *Voz e Vídeo* e desative **todas** as opções de processamento nativas (Supressão de Ruído, Cancelamento de Eco, Controle Automático de Ganho). O Discord "briga" com o EasyEffects se você não desligar isso.
* **Counter-Strike / Source Engine:** Os jogos da Valve costumam forçar alterações no volume do microfone, bagunçando seus filtros. Adicione as seguintes linhas no seu arquivo `autoexec.cfg` para impedir isso:
  **Snippet de código**

  ```
  voice_mixer_boost_low_mic "0"
  voice_mixer_volume "1.0" 
  ```

> Pull requests e sugestões de melhoria são bem-vindos!