# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# Fase 4 - Cap 1 - Visão Computacional na Clínica

## Autor: 
- <a href="https://www.linkedin.com/in/renanmendes26/">Renan de Oliveira Mendes - RM563145</a>


# Descrição
Nessa quarta fase desenvolvi ferramentas que automatizam a triagem e o diagnóstico médico por meio de Processamento de Linguagem Natural (NLP) e Machine Learning. Utilizamos duas técnicas em NLP, baseado em regras e estatístico.

Indo além, criamos uma interface moderna com React e Vite. Também desenvolvemos e treinamos um modelo de visão computacional para a análise de exames de eletrocardiograma.

## Links Videos:
### Parte 1 e Parte 2: 
### Ir Além: https://youtu.be/1NBNX88V1-0
### App: https://youtube.com/shorts/XTpQ_kAq_G8


# Parte 1
Implementamos um sistema de extração de informações para interpretar relatos clínicos.

Através de buscas por palavras-chave e expressões comuns (ex: "aperto no tórax", "fadiga"), o algoritmo sugere diagnósticos preliminares como Infarto ou Insuficiência Cardíaca, simulando o apoio à decisão médica.

#### Como funciona:


<img src="assets/Mapa_Ontologia.png" widht="150">

# Parte 2

Agora utilizando processamento de texto com TF-IDF (Term Frequency-Inverse Document Frequency) para converter relatos médicos em vetores numéricos. Seguindo uma abordagem mais tradicional, voltada a estatistica e probabilidade, treinamos um algoritmo de Machine Learning (Scikit-learn) para classificar os pacientes entre "Baixo Risco" e "Alto Risco", permitindo uma triagem rápida e eficiente baseada na gravidade dos sintomas.

#### Como funciona:

Criamos outro programa python "Gerar_Dataset.py" para gerar um novo arquivo csv "frases_risco.csv". Esse novo dataset é necessário pois descreve de forma mais textual e natural do que o dataset usado na parte 1.

<img src="assets/gerar_dataset.png" widht="150">


<img src="assets/teste_modelo_Logis_Regre.png" widht="150">

# Ir Além

Criamos do zero uma interface web completa responsiva para a gestão da clínica cardiológica.
Utilizamos: React + Vite + Styled Components/CSS Modules.

<img src="assets/Login.png" widht="150">

Dentre as Funcionalidades: 
- Gerenciamento de estado global com Context API.
- Autenticação simulada com persistência via LocalStorage.
- Consumo de dados via API fake para listagem de pacientes.
- Dashboards dinâmicos com métricas de agendamento e saúde.

Usando Context e diversos hooks e componentes, criamos 4 paginas

<img src="assets/pages.png" widht="150">
<img src="assets/AuthContext.png" widht="150">

De forma dinamica e simulada é possível realizar um login com autenticação, ver a lista de pacientes e marcar uma consulta.

<img src="assets/Portal.png" widht="150">
<img src="assets/agendamento.png" widht="150">


# Ir Além 2

 Assistente de Detecção de Pneumonia

Aplicação composta por:
- **backend/** — API Flask com modelo MobileNet (TensorFlow/Keras)
- **cardio-assistant/** — App mobile/web com Expo (React Native)

## Pré-requisitos

- Python 3.10+ (venv já incluído em `venv/`)
- Node.js 18+
- [Expo Go](https://expo.dev/go) no celular **ou** emulador Android/iOS

---

## 1. Iniciar o backend (API)

Abra um terminal na pasta do projeto:

```powershell
cd "c:\Users\Pichau\OneDrive\Área de Trabalho\Fase_4_Cap1\Ir_Alem2\backend"
```

Ative o ambiente virtual e inicie o servidor:

```powershell
..\venv\Scripts\Activate.ps1
python app.py
```

O servidor ficará disponível em `http://localhost:5000`.

Teste rápido no navegador ou PowerShell:

```powershell
Invoke-RestMethod http://localhost:5000/health
```

Deve retornar: `{"status":"ok","model":"mobilenet_pneumonia.keras"}`

---

## 2. Iniciar o app (Expo)

Abra **outro terminal**:

```powershell
cd "c:\Users\Pichau\OneDrive\Área de Trabalho\Fase_4_Cap1\Ir_Alem2\cardio-assistant"
npm install
npx expo start
```

Opções após o Expo iniciar:

| Plataforma | Como abrir |
|------------|------------|
| **Web** | Pressione `w` no terminal |
| **Android emulador** | Pressione `a` (requer Android Studio) |
| **Celular físico** | Escaneie o QR code com Expo Go |

---

## 3. Configurar URL do servidor

O app detecta automaticamente:

| Ambiente | URL padrão |
|----------|------------|
| Web / iOS simulador | `http://localhost:5000` |
| Emulador Android | `http://10.0.2.2:5000` |
| Celular físico | Precisa do IP da sua máquina na rede Wi-Fi |

Para **celular físico**, crie o arquivo `cardio-assistant/.env`:

```env
EXPO_PUBLIC_API_URL=http://192.168.x.x:5000
```

Substitua `192.168.x.x` pelo IP local do seu PC (veja com `ipconfig` no PowerShell).

Reinicie o Expo após alterar o `.env`.

---

## Fluxo de uso

1. Backend rodando (`python app.py`)
2. App aberto no Expo
3. Aba **Análise** → **Selecionar Imagem** → **Analisar**
4. Resultado: `Normal` ou `Pneumonia` + confiança (%)

---


## Estrutura

```
Ir_Alem2/
├── backend/
│   ├── app.py
│   ├── mobilenet_pneumonia.keras
│   └── requirements.txt
├── cardio-assistant/
│   ├── app/              # Rotas Expo Router
│   ├── screens/          # Tela principal de análise
│   └── constants/api.ts  # URL da API
└── venv/                 # Ambiente Python
```



# 📁 Estrutura de pastas

Dentre os arquivos e pastas presentes na raiz do projeto, definem-se:

- <b>assets</b>: Imagens relevantes para documentação desse repositório.

- <b>Ir_Alem</b>: Interface e todo código React + Vite.

- <b>Ir_Alem_2</b>: Notebook python com o modelo MLP para visão computacional.

- <b>Parte_1</b>: Arquivo txt, csv e código Python referentes ao classificador NPL baseado em regras e mapa ontologico criado.

- <b>Parte_2</b>: Arquivo csv e programa Python classificador NPL probabilistico, usando TF_IDF.
  



