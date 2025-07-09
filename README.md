# Geração de Voz (Text-to-Speech) com Kokoro em Português

Este projeto demonstra como utilizar a biblioteca Python `Kokoro` para converter texto em fala (Text-to-Speech - TTS). O foco é a síntese de fala em português, com a possibilidade de aplicar diferentes estilos de voz, incluindo uma voz de "Papai Noel" (pm_santa). O resultado é um arquivo de áudio WAV que pode ser reproduzido.

## Visão Geral

A síntese de fala é uma área da inteligência artificial que permite a criação de áudio a partir de texto. A biblioteca Kokoro simplifica esse processo, oferecendo um pipeline fácil de usar para transformar texto escrito em voz falada. Este projeto é ideal para:
* Criar locução para vídeos ou apresentações.
* Desenvolver assistentes de voz.
* Aplicativos de acessibilidade.
* Qualquer aplicação que necessite de saída de áudio a partir de texto.

O script executa os seguintes passos:
1.  Define o código do idioma para português.
2.  Inicializa o pipeline Kokoro.
3.  Define o texto a ser sintetizado e a voz (`pm_santa`).
4.  Gera o áudio em chunks e os concatena.
5.  Salva o áudio completo em um arquivo WAV.

## Estrutura do Projeto

* `KokoroSimpleTest.ipynb`: O notebook Jupyter que contém todo o código para a síntese de fala.
* `audio_completo.wav`: O arquivo de áudio WAV de saída gerado pelo script.

## Tecnologias Utilizadas

* **Python 3**
* **`kokoro`**: A biblioteca principal para Text-to-Speech.
* **`soundfile`**: Para escrever o áudio em formato WAV.
* **`numpy`**: Para manipulação de arrays de áudio.
* **Jupyter Notebook**: Para execução e demonstração interativa do código.


## Exemplo de Uso

Você pode modificar a variável `text` no notebook para que o assistente sintetize qualquer frase que você quiser.
Também é possível experimentar outras vozes se você baixar modelos adicionais compatíveis com o Kokoro.

```python
# Exemplo de modificação do texto
novo_texto = "Olá, eu sou um assistente virtual e estou aqui para ajudar você."
generator = pipeline(novo_texto, voice='pm_santa') # Mantendo a voz de Papai Noel

audio_chunks = []
for gs, ps, audio in generator:
    audio_chunks.append(audio)

audio_completo = np.concatenate(audio_chunks)
sf.write('meu_novo_audio.wav', audio_completo, 24000)
