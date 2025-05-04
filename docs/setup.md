# **Setup da Aplicação** ⚙️

## **Pré-Requisitos** 🛠️

Antes de iniciar a aplicação, verifique se os seguintes componentes estão instalados em seu ambiente:

- **Docker** (v28.1.1, build 4eba377) 🐳
- **Python** 🐍
- **Node.js** (v22.14.0) 🌐
- **npm** (v10.9.2) 📦

### **Sistema Operacional Recomendado** 🖥️

Embora a aplicação seja **dockerizada**, é altamente recomendada a execução em um sistema operacional **Linux**. Isso ocorre porque alguns módulos específicos, que requerem o uso de GPU (para tarefas de IA), são executados localmente, a fim de evitar a complexidade de configurar o acesso à GPU dentro do Docker.

---

## **Para subir os containers Docker** 🚢

### **API** 🔌

#### **Configuração do Ambiente** ⚙️

Crie um arquivo chamado `.env` na raiz do projeto com as seguintes variáveis de ambiente:

```env
API_PORT=3001
ALLOWED_ORIGINS=http://localhost:5173,http://localhost:3000,http://localhost:3001

# Configuração do Banco de Dados
MONGO_INITDB_ROOT_USERNAME=root
MONGO_INITDB_ROOT_PASSWORD=example
MONGO_URL=mongodb://${MONGO_INITDB_ROOT_USERNAME}:${MONGO_INITDB_ROOT_PASSWORD}@FURIAX-db:27017

# JWT
JWT_REGISTER_SECRET=REGISTER_SECRET
JWT_AUTH_SECRET=AUTH_SECRET

# API do Twitter
TWITTER_PYTHON_API_URL=https://localhost:8000

# API da Steam
STEAM_API_KEY=<sua_chave_da_steam>

# Credenciais do Administrador
ADMIN_EMAIL=admin@admin.com
ADMIN_PASSWORD=admin
JWT_AUTH_ADMIN_SECRET=ADMIN_SECRET

# Informações de Login no Twitter
USERNAME=<usuario_do_twitter>
EMAIL=<email_do_twitter>
PASSWORD=<senha_do_twitter>
```

---

#### **Execução dos Módulos de Validação de Documentos** 📜

1. Acesse o diretório de validação de documentos:

```bash
cd document-validation
```

2. Crie um ambiente virtual Python:

```bash
python3 -m venv venv
```

3. Ative o ambiente virtual:

```bash
source venv/bin/activate
```

4. Instale as dependências do projeto:

```bash
pip install -r requirements.txt
```

5. Inicie a API de validação com o seguinte comando:

```bash
uvicorn main:app --host 0.0.0.0 --port 8002
```

---

## **Frontend** 🌍

#### **Instalação das Dependências** 📥

Crie um arquivo `.env` com as variáveis de ambiente:

```env
VITE_API_URL="http://localhost:3001/api"
VITE_DOCUMENT_VALIDATION_URL="http://localhost:8002"
```

Execute o seguinte comando na raiz do projeto frontend para instalar todas as dependências necessárias:

```bash
npm install
```

#### **Inicialização da Aplicação** 🚀

Após a instalação, inicie o ambiente de desenvolvimento com o comando:

```bash
npm run dev
```

> 💡 Certifique-se de que as variáveis de ambiente estejam corretamente configuradas e que a API esteja em execução antes de iniciar o frontend.

---

## **Ollama** 🧠

#### **Instalação** 🖥️

Para instalar o Ollama em seu sistema, execute o seguinte comando no terminal:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

#### **Download do Modelo** 📥

Após a instalação, faça o download do modelo necessário para análise executando:

```bash
ollama run gemma3:4b
```

#### **Expondo a Porta com Ngrok** 🌐

Para permitir acesso externo ao serviço, exponha a porta utilizada pelo Ollama com o **Ngrok**:

```bash
ngrok http 11434 --host-header="localhost:11434"
```

Em seguida, atualize a variável de ambiente correspondente com o link gerado pelo Ngrok, garantindo que a aplicação possa se comunicar corretamente com o serviço.