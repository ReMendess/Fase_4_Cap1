# Assistente de Detecção de Pneumonia

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

## Solução de problemas

**Erro 400 / imagem não enviada (web)**
- Corrigido: na web o upload usa `Blob` em vez do formato `{ uri }` do React Native.

**Celular físico não conecta**
- O app usa automaticamente o mesmo IP do Expo (`192.168.x.x:5000`).
- Confirme que o backend está rodando e que PC e celular estão na mesma Wi-Fi.
- Se necessário, crie `cardio-assistant/.env` com `EXPO_PUBLIC_API_URL=http://SEU_IP:5000` e reinicie o Expo (`Ctrl+C` e `npx expo start` de novo).

**Permissão de galeria negada**
- Nas configurações do celular, permita acesso à galeria para o Expo Go

**Modelo não carrega**
- Verifique se `backend/mobilenet_pneumonia.keras` existe
- Execute `pip install -r requirements.txt` dentro do venv

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
