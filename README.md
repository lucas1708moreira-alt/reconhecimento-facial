# Sistema de Reconhecimento Facial

Este projeto implementa um sistema completo de verificação facial utilizando Visão Computacional. O sistema é composto por três módulos principais que garantem a detecção, a identificação precisa e a prevenção de fraudes (liveness detection).

## 🚀 O que o projeto faz

1. **Detecção de Faces:** 
   O sistema localiza rostos humanos em imagens ou vídeos utilizando duas técnicas:
   - **Viola-Jones (Haar Cascade):** Algoritmo clássico e rápido, ideal para ser executado em tempo real.
   - **DNN SSD (Caffe):** Modelo baseado em Deep Learning utilizando redes neurais convolucionais, sendo mais robusto a variações de iluminação e ângulos.

2. **Identificação de Faces:**
   Após detectar o rosto, o sistema utiliza o algoritmo **LBPH (Local Binary Patterns Histograms)** para reconhecer a face capturada. O modelo compara a face detectada com as faces treinadas previamente para identificar se a pessoa na câmera é um usuário autorizado (ex: 'lucas') ou se é um 'desconhecido'.

3. **Liveness Detection (Detecção de Vivacidade):**
   Para evitar ataques de apresentação/fraudes (como usar uma foto impressa ou a tela de um celular em frente à câmera), o projeto aplica detecção de piscar de olhos. Ele utiliza a biblioteca **Dlib** (68 marcos faciais) para calcular a **Taxa de Aspecto do Olho (EAR - Eye Aspect Ratio)**. O sistema exige a detecção de movimentos naturais dos olhos antes de liberar a autorização.

## 📁 Estrutura de Diretórios e Dependências

O projeto foi construído inteiramente no Jupyter Notebook (`projeto_reconhecimento_facial.ipynb`) e foi pensado para ser executado no **Google Colab** utilizando arquivos hospedados no Google Drive.

Organização de arquivos e modelos pré-treinados necessários:
- `fotos/`: Contém as imagens dos rostos para treinar o identificador.
- `classificadores/`: Contém o arquivo Haar Cascade (`haarcascade_frontalface_default.xml`).
- `modelos/`:
  - `deploy.prototxt` e `res10_300x300_ssd_iter_140000.caffemodel` (para a detecção via DNN DNN Caffe).
  - `shape_predictor_68_face_landmarks.dat` (para capturar os pontos dos olhos no cálculo do EAR).

## 🛠 Bibliotecas Utilizadas

- **OpenCV (`opencv-contrib-python`):** Para carregar imagens, processamento de vídeo, detecção de rostos e o algoritmo de reconhecimento LBPH.
- **Dlib** e **SciPy:** Para a detecção de "Liveness" baseado na distância espacial dos marcos oculares.
- **NumPy, Matplotlib e Seaborn:** Manipulação de matrizes e visualização de dados/resultados.
- **Scikit-Learn:** Avaliação de métricas de classificação facial.
