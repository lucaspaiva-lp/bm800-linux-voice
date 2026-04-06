[![EN](https://img.shields.io/badge/lang-EN-blue?style=for-the-badge&logo=google-translate)](https://github.com/lucaspaiva-lp/lucaspaiva-lp)
[![PT-BR](https://img.shields.io/badge/lang-PT--BR-green?style=for-the-badge&logo=google-translate)](https://github.com/lucaspaiva-lp/bm800-linux-voice)

# 🎙️ BM-800 Linux Audio Voice Pro: Presets para EasyEffects

Este repositório contém perfis de áudio configurados para o **EasyEffects** (PipeWire), criados especificamente para domar as características do microfone condensador **BM-800** quando utilizado **diretamente no PC, sem uma fonte de alimentação Phantom Power (48V) ou interface de áudio**.

Como o BM-800 é um microfone que requer energia extra para operar com força total, ligá-lo direto na placa-mãe faz com que ele perca boa parte da sua capacidade natural de captação e ganho. Isso resulta em um áudio muito agudo, com som "metálico" e com bastante ruído estático de fundo (*hiss*).

O objetivo destes presets é compensar digitalmente essa deficiência de hardware: entregando um som limpo, com peso de "locução de rádio", e isolando ruídos de teclado mecânico e mouse sem picotar a voz.

---

## 📁 Arquivos e Estrutura do Repositório

* **Pasta `/presets`**: Contém os arquivos de configuração em formato **`.json`**.
* **Pasta `/images`**: Contém capturas de tela (screenshots) de cada plugin configurado. Use essas imagens como guia visual para conferir se os parâmetros foram carregados corretamente ou para configurar manualmente se preferir.

---

### Presets Disponíveis:

* **`BM-800 (Natural + Equalize + Deeser + RNoiser).json`** : 🏆 **(Recomendado)** Versão completa com Noise Reduction (RNNoise) para ambientes com ruído constante (ventiladores, ar-condicionado).
* **`BM-800 (Natural + Equalize + Deeser).json`** : Foco em encorpar a voz (ganho em 126-194Hz), remover o brilho metálico e suavizar os "S" da fala.
* **`BM-800.json`** : O perfil base de equalização.
* **`BM-800 (Natural + Equalize) [SEM SUPRESSOR].json`** : Para ambientes com tratamento acústico.
* **`BM-800 (Natural + Sem supressor).json`** : Configuração mais leve.

> *Nota: Você tem total liberdade para desativar filtros individuais diretamente na interface do EasyEffects conforme sua necessidade.*

*(Usuários de Ubuntu, Fedora ou Mint devem buscar por `lsp-plugins`, `calf-plugins` e `librnnoise` em seus gerenciadores).*

---

## 🚀 Como Instalar e Configurar

1. Baixe os arquivos `.json` da pasta `/presets`.
2. Abra o EasyEffects -> Aba **PipeWire** -> **Predefinições** (Presets).
3. Clique em **Importar** e selecione os arquivos baixados.
4. Selecione o preset e clique em **Carregar** (Load).
5. **Dica Visual:** Consulte a pasta `/images` deste repositório para comparar os gráficos e garantir que os efeitos estão ativos.

---

## 🎮 Dicas de Uso (CS2, Discord, etc)

* **No Sistema:** Certifique-se de que o **"EasyEffects Source"** está selecionado como seu microfone padrão no KDE/Gnome.
* **Discord:** Desative **todas** as opções de "Redução de Ruído" e "Cancelamento de Eco" do Discord para evitar conflito com o EasyEffects.
* **Counter-Strike / Source Engine:** Adicione ao seu `autoexec.cfg` para evitar que o jogo altere seu volume:
  **Snippet de código**

  ```
  voice_mixer_boost_low_mic "0"
  voice_mixer_volume "1.0" 
  ```

---

## 🪟 Alternativa para Windows (VoiceMeeter)

Para usuários de Windows, o EasyEffects não está disponível. Recomendamos o uso do **VoiceMeeter Banana** com este guia:
▶️ [Tutorial VoiceMeeter - Configuração e Separação de Áudio](https://www.youtube.com/watch?v=0EjDL3BgPk4&t=209s)

---

## 💬 Dúvidas, Sugestões ou Ajuda?

Se você tiver dificuldade na instalação, encontrar um bug ou quiser compartilhar uma melhoria na equalização, nossa aba de **Discussions** está aberta!

👉 [Acesse aqui o Fórum da Comunidade](https://github.com/lucaspaiva-lp/bm800-linux-voice/discussions)

> Pull requests são muito bem-vindos! Vamos melhorar o áudio da comunidade Linux juntos. 💪
