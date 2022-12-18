# sel0337_11234721
**Repositório da prática 6 de micros 2:
**

Foi adicionado nesta pasta um zip contendo as duas versões do código desenvolvido para a prática 6, bem como a imagem e o vídeo capturado pela RaspBerry.

A primeira versão do código é "camera.py", cujo conteúdo é o código respondavel por tirar foto e capturar um vídeo do laboratório. A versão final é "pratica6_weather.py", que adiciona o código responsável por impotar os dados da base climática, o qual pode ser aprimorado para exibir os dados da estação meteorológica na imagem capturada pela câmera em aplicações futuras. Como a versão final consiste apenas na anexação de mais uma parcela de código, será comentada a lógica do "pratica6_weather.py" apenas.

Para a utilização da câmera, importou-se as bibliotecas "requests", "json", "pprint", "picamera" e "time".

As variáveis "stations" e "weather" são objetos que, a partir da API oracle, recebem respectivamente as coordenadas de todas as estações de meteorologia próximas e os dados da estação UFSC, de ID 966583.

Já o objeto "my_weather" aloca o comando "get(weather).json()\['items'\]", que consiste em procurar, em "weather", todos os ítems da categoria "items" do código JavaScript do objeto, e agrupá-los num arquivo de formato JavaScript Object Notation (.json). Este objeto é o que, de fato, contém os dados meteorológicos desejados.

O comando "pprint(my_weather)" imprime, no terminal python, o conjunto de informações armazenados em "my_weather".

O comando abaixo de "pprint(my_weather)", começa a manipular a câmera da Rasp, criando o objeto "camera".

Como as imagens obtidas pela câmera são apresentadas no monitor de ponta cabeça, é necessário rotacioná-la 180°. Esta rotação é definida pelo parâmetro "camera.rotation = 180".

A adição de texto à imagem se deu com os parâmetros "camera.annotate": "camera.annotate_text_size = 30" determina que o tamanho da fonte é 30, "camera.annotate_background = Color('blue')" indica que a cor de fundo do texto é azul, e "camera.annotate_text = "Luis Otavio: 11234721; Lucas Pires: 11819452" " determina o conteúdo do texto apresentado.

O comando "camera.start_preview()" começa a comunicação entre a câmera e a rasp, implementa todos os parâmetros atribuídos ao objeto "camera" e inicia a captura de tela.

A sequência de códigos:

"sleep(3)
camera.capture('/home/sel/sel0337_LuisO_Lucas/image.jpg')"

Determina um intervalo de 3 segundos antes de se tirar a foto pela câmera, e salva esta imagem no caminho de arquivo indicado como parâmetro da função ".capture"

Já a sequência de códigos:

"camera.start_recording('/home/sel/sel0337_LuisO_Lucas/video.h264')
sleep(5)
camera.stop_recording()"

Grava um vídeo de 5 segundos (tempo determinado pelo comando "sleep") que será salvo no caminho indicado no parâmetro de ".start_recording".

Por fim, "camera.stop_preview()" termina a transmissão da câmera.
