# Projeto de Chatbot com Google Gemini
[![Python](https://img.shields.io/badge/Python-3.9-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Google Generative AI](https://img.shields.io/badge/google--generativeai-FFC107?style=for-the-badge&logo=google&logoColor=black)](https://pypi.org/project/google-generativeai/)
[![Python dotenv](https://img.shields.io/badge/Dotenv-gray?style=for-the-badge&logo=python&logoColor=yellow)](https://pypi.org/project/python-dotenv/)


Este é um projeto de chatbot em Python que utiliza a API do Google Gemini para interações de linguagem natural. O projeto é configurado para usar a biblioteca `google-generativeai` e gerenciar a chave de API de forma segura usando um arquivo `.env`.

## Tecnologias Utilizadas

* **Python 3.x**

* **google-generativeai**: Biblioteca oficial para interagir com a API do Google Gemini.

* **python-dotenv**: Para carregar variáveis de ambiente de um arquivo `.env`.

## Instalação e Configuração

Siga os passos abaixo para configurar e executar o projeto no seu ambiente.

### 1. Clone o repositório

```
git clone <url_do_seu_repositório>
cd <nome_do_seu_projeto>

```

### 2. Crie um Ambiente Virtual (Recomendado)

```
# No Linux/macOS
python3 -m venv env
source env/bin/activate

# No Windows
python -m venv env
.\env\Scripts\activate

```

### 3. Instale as Dependências

As dependências necessárias estão listadas no arquivo `requirements.txt`.

```
pip install -r requirements.txt

```

### 4. Configure a Chave de API

Você precisa de uma chave de API do Google Gemini.

1. Obtenha sua chave em [Google AI Studio](https://aistudio.google.com/app/apikey).

2. Crie um arquivo na raiz do seu projeto chamado `.env`.

3. Adicione a sua chave no arquivo `.env` no formato:

    ```
    GOOGLE_API_KEY="sua_chave_de_api_aqui"
    
    ```

    **Importante:** Adicione o arquivo `.env` ao seu `.gitignore` para garantir que a chave não seja enviada para o seu repositório.

### 5. Execução

Para rodar o script principal do chatbot, execute o seguinte comando:

```
python seu_script.py

```

*(substitua `seu_script.py` pelo nome do seu arquivo Python)*

### Exemplo de Código do Projeto

O código do seu script principal (`seu_script.py`) deve ser semelhante a este:

```
import os
import google.generativeai as genai
from dotenv import load_dotenv

# Carrega a chave de API
load_dotenv()
genai.configure(api_key=os.getenv("GOOGLE_API_KEY"))

# Inicializa o modelo
modelo = genai.GenerativeModel('gemini-2.5-flash-lite')

# Inicia a sessão de chat com a instrução do sistema
chat = modelo.start_chat(
    history=[],
    system_instruction="Você é um assistente pessoal e você sempre responde de forma sucinta"
)

# Envia a primeira mensagem no chat
response = chat.send_message("Olá, como posso te ajudar?")

# Imprime a resposta
print(response.text)
