
# Passo a Passo

### 1. Captura dos dados em video

Um script Python faz download dos videos de várias câmeras da NitTrans e os armazena localmente, adicionando um timestamp ao nome do arquivo. O loop de captura é infinito, sendo feita uma nova tentativa a cada 10 minutos.

### 2. Pré-processamento

Um script para a extração de frames percorre o diretório local. Para cada video, ele executa o mesmo utilizando OpenCV e extrai até quatro frames, um a cada trinta quadros, e os reserva em outro diretório renomeando-os utilizando o UUID + timestamp. Em seguida, os frames são classificados, sendo calculado seu brilho médio e sua categoria *(chuva_com_alagamento, chuva_forte, chuva_leve, sem_chuva ou indefinido)*. Em seguida, o frame é copiado para a pasta referente a sua classificação. Finalmente, os frames estão prontos para serem separados e utilizados no algoritmo de Machine Learning, sendo divididos em três grupos:

- 70% em treinamento;
- 15% em validação;
- 15% em testes.

### 3. Aprendizado de Máquina

O script de Machine Learning utiliza os frames contidos nos diretórios de treinamento e validação para treinar um modelo de Rede Neural Convolucional (CNN) e, através da criação de geradores de imagem, carrega os dados de treinamento e validação, define a arquitetura da CNN, compila o modelo e o treina, persistindo o modelo criado na pasta modelo_cnn.h5. 

### 4. Monitoramento automatizado

O script de teste carrega o modelo Keras e percorre todo o conjunto de teste (localizado no diretório das imagens geradas na pasta teste), realiza comparações entre a classe prevista com a verdadeira e registra os resultados, calculando uma média de precisão com base nesses dados.