# Assistente pessoal usando o ChatGPT

## Objetivo:
   Este projeto propõe a elaboração de um assistente pessoal utilizando o ChatGPT, processamento de voz e áudio, e Stable Diffusion, permitindo ao usuário interagir com o modelo de linguagem natural (ChatGpt) de maneira mais intuitiva e divertida. Esta integração aumenta a eficiência e conveniência do uso da tecnologia, tornando-a mais acessível e ampliando suas aplicações em vários setores da sociedade.
  
## Ferramentas:
### Pré Processamento de Áudio: 
   A captura de áudio para a utilização no projeto deve ser realizada através de um dispositivo de gravação, como microfone, o qual obtém o sinal analógico do áudio. Esse sinal será tratado corretamente a fim de evitar a perda de informações importantes.
  
### Speech to text (STT):
   STT é uma tecnologia de processamento de fala que permite a conversão da fala em texto. Ele é usado dentro do projeto para capturar a voz do indivíduo e convertê-la em texto para compreensão do ChatGPT. O funcionamento dessa ferramenta pode ser dividida em etapas: aquisição do áudio, processamento de fala e reconhecimento de fala.
  
### Text to speech (TTS):
   O TTS é o processo inverso do STT, sendo o processo pelo qual um texto é convertido em fala artificial, usado dentro do projeto para transmitir o texto gerado pelo ChatGPT, em forma de voz. Esse processo envolve diversas etapas, como: a análise do texto, em que é analisado o texto de entradas - palavras, frases e símbolos -; a geração de fonemas, etapa em que as palavras do texto são convertidas em fonemas - unidade básica de som utilizada para formar palavras -; modelagem da fala, o qual envolve a seleção de parâmetros como velocidade, entonação e inflexão; e por fim a síntese da voz, técnica para combinar os fonemas em um áudio, incorporando as informações sobre a modelagem da fala

### ChatGpt:
   O ChatGPT é um modelo avançado de processamento de linguagem natural (NLP) que foi desenvolvido pela OpenAI, uma organização de pesquisa de inteligência artificial sem fins lucrativos, fundada em 2015. A ferramenta é um sistema de chatbot que permite fazer perguntas e, muitas vezes, receber respostas rápidas e úteis.
   
   O ChatGPT é baseado em uma arquitetura de transformers, que é uma abordagem inovadora para o processamento de linguagem natural. A arquitetura de transformers foi desenvolvida para superar algumas limitações dos modelos anteriores, como a dificuldade em processar informações em sequência. O seu diferencial está na capacidade de atender a relações de dependência entre elementos em uma sequência, como palavras em uma frase. Essa arquitetura é baseada em redes neurais, onde as informações de entrada são codificadas em uma representação densa de vetor, que é passada por várias camadas para realizar tarefas como classificação de texto, geração de texto e tradução. Além disso, o modelo transformers é altamente escalável e pode ser facilmente treinado com grandes quantidades de dados, o que o torna uma opção atraente para aplicações em processamento de linguagem natural.
  
### Stable diffusion: 
   O modelo de Aprendizagem Profunda (Deep Learning) de texto para imagem, conhecido como Stable Diffusion, é uma tecnologia de ponta lançada em 2022. Ele permite a geração de imagens detalhadas a partir de descrições em texto, além de ser aplicável a outras tarefas. Com o código disponível publicamente e sua compatibilidade com a maioria das máquinas comuns, a tecnologia tem atingido uma ampla base de usuários.
   
   O Stable Diffusion possui a habilidade única de gerar novas imagens completamente a partir do zero, bastando uma descrição textual dos elementos desejados na imagem. Imagens existentes também podem ser editadas para incluir ou excluir elementos. 
   
   Portanto, devido às grandes capacidades do Stable Diffusion e do ChatGPT, o projeto engloba ambas as tecnologias. Enquanto o ChatGPT é capaz de descrever cenários complexos com extrema precisão, o Stable Diffusion consegue transformar essas descrições em imagens realistas e impactantes. O projeto, então, permite que o usuário descreva o que deseja na imagem, logo, o ChatGPT o transforma em uma descrição detalhada e o Stable Diffusion gera a imagem final e a retorna para o usuário.

### Grad.io:
   O avanço do aprendizado de máquina possibilitou o desenvolvimento de novas Inteligências Artificiais (IA) e modelos de Processamento de Linguagem Natural (NLP), o que resultou em uma ampla utilização desses modelos por grande parte da população, como é o exemplo do ChatGPT e algumas IAs que geram imagens. Contudo, mesmo que o conhecimento desses chatbots sejam muito amplos, não é o suficiente para que o usuário consiga interagir com esse chatbot, por isso é muito importante uma interface simples, de fácil interação e intuitiva.
   
   Com isso, para criar uma interface atraente e cativante para o chatbot, foi utilizado o Grad.io, que é um pacote do Python open-source que auxilia a fazer interfaces para o usuário. O Grad.io consegue disponibilizar para o modelo uma página web, dessa forma, facilitando a utilização de outras pessoas que possam estar interessadas no chatbot.
  
## Metodologia: 
   Foi optado pela utilização do modelo Whisper para a implementação do Speech-to-Text, devido à sua transcrição satisfatória sem a necessidade de um pré-processamento muito complexo, à disponibilidade do modelo para o idioma português (já que o modelo é multilinguístico) e à sua capacidade de realizar transcrições precisas sem a necessidade de treinamento adicional, o que economiza tempo.
   
   O processo de pré-processamento começa com a amostragem do sinal analógico, seguida pelo recorte do áudio em segmentos de 30 segundos. Esses segmentos de áudio são então convertidos em imagens de log-mel-espectrograma, que representam a energia de frequência do sinal de áudio em uma escala logarítmica. O modelo Whisper é configurado para transcrever apenas em português, é o tamanho do modelo adotado foi o “base”, pois pareceu o mais adequado. O resultado do STT é então passa por uma análise de palavras-chave, que substitui palavras que possam prejudicar a geração de prompts de qualidade no ChatGPT. Somente após esse processo, o resultado é utilizado como entrada no chatbot inteligente. O prompt resultante é utilizado como entrada no TTS, utilizando o GTTS devido à sua facilidade de implementação e disponibilidade em português. O TTS, então, gera uma saída de áudio contendo a resposta do chatbot.
    
   Por fim, para a geração de imagens, a mesma entrada utilizada para gerar o prompt no ChatGPT é analisada em busca de palavras-chave que indicam se o usuário deseja gerar uma imagem ou se basta a resposta gerada pelo chatbot. Dependendo da análise, o prompt resultante é utilizado como entrada no modelo Stable Diffusion, a fim de gerar uma imagem mais detalhada, que gera uma imagem correspondente, ou é retornada uma imagem padrão quando a geração de imagem não é necessária.
   
   Para a integração com a interface, utilizamos os métodos do Grad.io. Para esses métodos precisamos passar o input e ele retorna um output na saída diretamente para o usuário. Além disso, temos que passar como parâmetro a função que a interface deve utilizar, que no nosso caso foi toda a comunicação entre os algoritmos, citado anteriormente. Para os inputs foram utilizados o audio do usuário, que é feito a partir da gravação com o microfone, e assim, após passar pela função ele nos retorna 4 outputs, o primeiro sendo o STT, mostrando a conversão do áudio do usuário para texto, a segunda sendo a resposta do ChatGPT, após a pergunta ou comando do usuário passar pela API, o terceiro, caso o usuário requisite a geração de uma imagem, será a descrição do ChatGPT para o Stable Diffusion, caso ele não requisite uma imagem, aparecerá uma imagem pré-definida, e por último o TTS, com a transcrição da resposta do ChatGPT de texto para áudio. Com essa interface também é possível gerar um link que permite o compartilhamento para outros usuários.
  
## Referências:

“ChatGPT hit 1 million users in 5 days: Here’s how long it took others to reach that milestone”, IndianExpress. Disponível em<https://indianexpress.com/article/technology/chatgpt-hit-1-million-users-5-days-vs-netflix-facebook-instagram-spotify-mark-8394119/>. Acesso em: 09 de fev. de 2023.

"O que é conversão de fala em texto?". Amazon Web Services, 2023. Disponível em: <https://aws.amazon.com/pt/what-is/speech-to-text/#:~:text=Speech%20to%20text%20is%20a,recognition%20or%20computer%20speech%20recognition.>. Acesso em: 09 de fev. de 2023

PORTASIO, Luiza. "Você sabe o que é TTS?". Medium, 2021. Disponível em: <https://medium.com/dialograma/voc%C3%AA-sabe-o-que-%C3%A9-tts-dfa2e3835c6b.>.  Acesso em: 09 de fev. de 2023

ALAMMAR, Jay. "The Illustrated Stable Diffusion". jalammar.github.io. Acesso em: 09 de fev. de 2023.

SMESTAD, Tuva Lunde, and Frode Volden. "Chatbot personalities matters: improving the user experience of chatbot interfaces." Internet Science: INSCI 2018 International Workshops, St. Petersburg, Russia, October 24–26, 2018, Revised Selected Papers 5. Springer International Publishing, 2019.

GRAD.IO. Quickstart. Disponível em: <.https://gradio.app/qNextuickstart/>. Acesso em: 09 de fev. de 2023

OPENAI. Whisper. GitHub, 2018. Disponível em: <https://github.com/openai/whisper>. Acesso em: 14 de fev. de 2023

GTTS. Documentação do módulo GTTS. Read the Docs, 2023. Disponível em: <https://gtts.readthedocs.io/en/latest/module.html#languages-gtts-lang>. Acesso em: 14 de fev. de 2023

## Autores:
   ALEXANDRE COSTA FERRO FILHO, aluno do bacharelado em IA na Universidade Federal de Goiás (UFG).
    Contato: alexandre_ferro@discente.ufg.br

   DECIVAN DAMASCENO ARAUJO FILHO, aluno do bacharelado em IA na Universidade Federal de Goiás (UFG).
    Contato: decivan.damasceno@discente.ufg.br

   EVELLYN NICOLE MACHADO ROSA, aluna do bacharelado em IA na Universidade Federal de Goiás (UFG).
    Contato: nicole@discente.ufg.br

   GUILHERME HENRIQUE DOS REIS, aluno do bacharelado em IA na Universidade Federal de Goiás (UFG).
    Contato: guilherme_reis@discente.ufg.br

   MARCELO HENRIQUE LOPES FERREIRA, aluno do bacharelado em IA na Universidade Federal de Goiás (UFG).
    Contato: marcelomarcelo2@discente.ufg.br
    
   MURILO DE OLIVEIRA GUIMARAES, aluno do bacharelado em IA na Universidade Federal de Goiás (UFG).
    Contato: muriloguimaraes@discente.ufg.br

