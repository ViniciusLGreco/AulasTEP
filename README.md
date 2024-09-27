# AulasTEP
Repositório com todas as aulas de Tópicos Especiais em Programação.

# Aula 1 - dia 08/08/2024
Não teve aula

# Aula 2
Dia 15/08/2024

Criar conta no GPT
Passo a passo:

Acesse o site da OpenAI: Vá até a página principal da OpenAI: https://platform.openai.com/
Clique em "Sign Up" (Inscreva-se): Geralmente, este botão se encontra no canto superior direito da página.
Preencha as informações solicitadas:
E-mail: Insira um endereço de e-mail válido.
Senha: Crie uma senha forte e segura.
Outras informações: Podem ser solicitados outros dados, como nome completo e organização (se aplicável).
Verifique seu e-mail: A OpenAI enviará um e-mail de verificação para confirmar sua identidade. Clique no link de verificação dentro do e-mail.
Complete o perfil (opcional): Após a verificação, você pode personalizar seu perfil adicionando informações adicionais, como sua área de interesse e como planeja usar as ferramentas da OpenAI.
Comece a usar: Com a conta criada, você terá acesso aos diferentes produtos e serviços oferecidos pela OpenAI, como o ChatGPT, API da OpenAI e outros.
Criar conta no Groq
https://groq.com/

Trabalhando com ambientes Virtuais no Python
Ambientes virtuais são como "ilhas" isoladas dentro do seu sistema, onde você pode instalar e gerenciar pacotes Python de forma independente para cada projeto. Isso significa que cada projeto terá sua própria versão do Python e suas próprias bibliotecas, evitando conflitos entre diferentes versões e dependências.

Por que usar ambientes virtuais?

Isolamento de projetos: Cada projeto terá seu próprio conjunto de pacotes, evitando conflitos de versão.
Gerenciamento de dependências: Facilita o controle das versões exatas de cada pacote utilizado em um projeto.
Reprodutibilidade: Permite que outros desenvolvedores reproduzam o ambiente do seu projeto com facilidade.
Organização: Mantém seu ambiente Python organizado e livre de confusões.
a) Criando um ambiente virtual local com Python no terminal

python -m venv meu_ambiente # Ativar ambiente - Linux;WSL source meu_ambiente/bin/activate # Ativar ambiente - windows meu_ambiente\Scripts\activate # Instalando pacotes pip install <module name> # Dica. Nomear ambiente como .venv
b) Criando um ambiente virtual local com Python no VSCODE

Testes práticos:
Search Tools GPTs

.Chat com GPT
.Imagem com DALLE-3
.Texto para audio Groq
.Audio para texto
.Chat com Groq

PDF de LLMs(https://github.com/ViniciusLGreco/AulasTEP/blob/main/LLMs.pdf)

# Aula 3

# Aula 4

# Aula 5

Aula 5 -Conceitos de RAG com Langchain e Langflow
Atividades com Agentes CREW AI

Agentes de IA com CrewAI e Llama3 usando a API Groq

Este exemplo demonstra como criar agentes de IA usando a biblioteca CrewAI, o modelo Llama3 e a API Groq em Python. O objetivo é fornecer uma estrutura básica para configurar e executar agentes de IA.

Requisitos
Antes de começar, certifique-se de ter os seguintes requisitos instalados:

Python 3.8 ou superior
Biblioteca CrewAI
Acesso à API Groq para o modelo Llama3
pip para gerenciar pacotes Python
Instalação
Clone o repositório:

git clone https://github.com/viniciusds2020/ai_crewai_starter_template.git
cd ai_crewai_starter_template
Crie um ambiente virtual (opcional, mas recomendado):

python -m venv venv
source venv/bin/activate  # No Windows, use `venv\Scripts\activate`
Instale as dependências:

pip install -r requirements.txt
Configuração
Obtenha uma chave de API da Groq para acessar o modelo Llama3. Registre-se no site da Groq e siga as instruções para gerar a chave de API.

Crie um arquivo .env na raiz do projeto e adicione sua chave de API:

GROQ_API_KEY=your_api_key_here
Teste sua configuração para verificar se está carregando corretamente o arquivo .env

import os
from dotenv import load_dotenv

# Carrega as variáveis de ambiente do arquivo .env
load_dotenv()

# Verifica se a chave foi carregada corretamente
groq_api_key = os.getenv('GROQ_API_KEY')
if groq_api_key is None:
    print("A chave da API não foi carregada corretamente.")
else:
    print("Chave da API carregada:", groq_api_key)
Uso
O arquivo principal main.py contém a lógica para inicializar e executar o agente de IA. Para iniciar o agente, execute:

python main.py
Estrutura do Projeto
.
├── README.md
├── requirements.txt
├── main.py
└── .env
README.md: Este arquivo de documentação.
requirements.txt: Arquivo de dependências do Python.
main.py: Script principal que inicializa e executa o agente de IA.
.env: Arquivo contendo a chave de API da Groq.
Fiz alguns pequenos ajustes abaixo para facilar o uso. Revise seu arquivo.

Arquivo agents.py

### Sistemas de multi-agentes de inteligencias artificiais

# Biblioteca
from crewai_tools import tool
from crewai import Agent, Task, Crew
from langchain_groq import ChatGroq
from langchain_community.tools import DuckDuckGoSearchRun

# Modelo LLM - Llama3 
llm = ChatGroq(temperature=0.7,
               groq_api_key='sua-chave-api-groq',
               model_name='llama-3.1-8b-instant') #novo modelo

#se for usar o GPT
#llm = ChatOpenAI(model_name="gpt-4o-mini", temperature=0.3)

# Ferramentas - Busca na internet com DuckDuckGo
@tool('DuckDuckGoSearchRun')
def search_tool(search_query: str):
  ''' Search the web for infotmation on a given topic'''
  return DuckDuckGoSearchRun().run(search_query)

# Topico do blog
topic = "Apple and AI in finance"

# Agentes
researcher = Agent(
    role = "Senior Researcher",
    goal = f"Explore trending technologies in {topic}.",
    backstory = "You are an innovative researher who follows the latest technology",
    verbose = True,
    tools = [search_tool],
    llm = llm,
)

writer = Agent(
    role = "Top Writer",
    goal = f"Create engaging content about {topic}. ",
    backstory = "You are an expert blogger who writes interesting articles.",
    verbose = True,
    tools = [search_tool],
    llm = llm,
)

# Tarefas
research_task = Task(
    description = f"Investigate the latest AI trends in {topic}.",
    expected_output = "A comprehensive 4 paragraphs long report on the latest AI trends.",
    tools = [search_tool],
    agent = researcher,
)

write_task = Task(
    description = f"Write an engaging article on {topic} that focuses on the latest trends.",
    expected_output = f"A comprehensive 4 paragraphs blog on {topic} in markdown format.",
    tools = [search_tool],
    agent = researcher,
    output_file = "my-blog.md"
)

# Orquestrador
crew = Crew(
    agents=[researcher, writer],
    tasks = [research_task, write_task]
)

result = crew.kickoff(
    inputs = {"topic": topic}
)
Vamos adaptar o projeto acima para pesquisar e redigir uma notícia com dados recentes sobre as queimadas em Mato Grosso.

Faça uma cópia do arquivo main.py para agente.py

Obs. Altere os prompts, de modo com que o resultado produzido seja em Porguês do Brasil, contudo, mantenha os roles definidos para os agentes ou verifique com mais cuidado a documentação em crewAI Agents - crewAI.

Renomei também o output_file = "news.md".

Ok. Quando finalizar suba tudo para seu Git OK!

Instalar o Langflow localmente
Cuidado

O Langflow  requer que  o Python versão 3.10 ou superior e  o pip  ou  pipx  estejam instalados no seu sistema.

Instale o Langflow com pip:

  1  python -m pip install langflow -U           

Instale o Langflow com pipx:

  1  pipx install langflow --python python3.10 --fetch-missing-python           

O Pipx pode buscar a versão Python faltante para você com  --fetch-missing-python, mas você também pode instalar a versão Python manualmente. Use  --force-reinstall para garantir que você tenha a versão mais recente do Langflow e suas dependências.

⛓️ Execute o Langflow
Para executar o Langflow, digite o seguinte comando.
  1  python -m langflow run           

Confirme se uma instância local do Langflow é iniciada visitando  o site http://127.0.0.1:7860 em um navegador baseado em Chromium.


Exemplos de Fluxos no LANGFLOW
TEP - Chat com Memória

TEP - CrewAI

TEP - PDF RAG

![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula5/Captura%20de%20tela%202024-09-12%20215701.jpg)

![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula5/datastax.jpg)

[Ver o arquivo git.txt](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula5/git.txt)

[Ver o arquivo Chat com Memória.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula5/Chat%20com%20memoria.json)

# Aula 6
Chatbots com base de conhecimento - Dify

![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/1.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/2.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/3.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/4.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/5.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/6.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/7.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/8.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/9.jpg)

[Ver o arquivo RAG documents.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/RAG%20documents.json)

[Ver o arquivo DataStax.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/Aula6/datastax%20aula%2006.json)

# Aula 7
**Docker**
Docker é uma plataforma open source que possibilita o empacotamento de uma aplicação dentro de um container. Uma aplicação consegue se adequar e rodar em qualquer máquina que tenha essa tecnologia instalada.

Porque usar WSL 2 + Docker para desenvolvimento
Configurar ambientes de desenvolvimento no Windows sempre foi burocrático e complexo, além do desempenho de algumas ferramentas não serem totalmente satisfatórias.

Com o nascimento do Docker este cenário melhorou bastante, pois podemos montar nosso ambiente de desenvolvimento baseado em Unix, de forma independente e rápida, e ainda unificada com outros sistemas operacionais.

Modos de usar Docker no Windows
Docker Desktop com WSL2
Roda em cima do Virtual Machine Platform que é um componente do Hyper-V e se integra com o WSL2 permitindo rodar o Docker dentro do ambiente do Linux.

Não é necessário adquirir licença PRO do Windows 10/11.

Tem um grande desempenho e consome menos recursos quando comparado ao Docker Toolbox ou Docker Desktop com Hyper-V.

Algumas Vantagens
Tem uma ferramenta visual para administrar o Docker.
Permite instalar extensões para usar ferramentas diretas no Docker.
Permite rodar um cluster Kubernetes localmente de forma fácil.
Simplifica a configuração do Docker tanto no Windows quanto no WSL 2.
Algumas Desvantagens
Uso de memória inicial sem rodar nenhum container Docker é de 1GB ou mais.
Pode ser necessário reiniciar o Docker Desktop para que ele funcione corretamente em algumas situações.
Tende a consumir mais recursos da máquina que o Docker Engine diretamente instalado no WSL 2.
Docker Engine (Docker Nativo) diretamente instalado no WSL2
O Docker Engine é o Docker nativo (como foi criado) que roda no ambiente Linux e completamente suportado para WSL 2. Sua instalação é idêntica a descrita para as próprias distribuições Linux disponibilizadas no site do Docker.

É a maneira pura de usar o Docker no Linux.

Algumas Vantagens
Consume menos memória para rodar o Docker Daemon (servidor do Docker) quando comparado ao Docker Desktop.

Traz a experiência mais pura de usar o Docker no Linux.

Algumas Desvantagens
Se necessitar executar o Docker em outra instância do WSL 2, é necessário instalar novamente o Docker nesta instância ou configurar o acesso ao socket do Docker desejado para compartilhar o Docker entre as instâncias.

**2 - Instalar o Docker com Docker Engine (Docker Nativo)**
A instalação do Docker no WSL 2 é idêntica a instalação do Docker em sua própria distribuição Linux, portanto se você tem o Ubuntu é igual ao Ubuntu, se é Fedora é igual ao Fedora. A documentação de instalação do Docker no Linux por distribuição está aqui, mas vamos ver como instalar no Ubuntu.

![[Pasted image 20240822100956.png]]

O que o WSL 2 pode usar de recursos da sua máquina
Podemos dizer que o WSL 2 tem acesso quase que total ao recursos de sua máquina. Ele tem acesso por padrão:

A 1TB de disco rígido. É criado um disco virtual de 1TB para armazenar os arquivos do Linux (este limite pode ser expandido, ver a área de dicas e truques).
A usar completamente os recursos de processamento.
A usar 50% da memória RAM disponível.
A usar 25% da memória disponível para SWAP (memória virtual).
Se você quiser personalizar estes limites, crie um arquivo chamado .wslconfig na raiz da sua pasta de usuário (C:\Users\<seu_usuario>) e defina estas configurações:

[wsl2]
memory=8GB
processors=4
Instalando Docker
https://docs.docker.com/engine/install/ubuntu/

Install using the apt repository
Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

Set up Docker's apt repository.

# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
Install the Docker packages.

Latest Specific version
To install the latest version, run:

$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
Verify that the Docker Engine installation is successful by running the hello-world image.

$ sudo docker run hello-world
Fazer Ate aqui

https://github.com/codeedu/wsl2-docker-quickstart
https://learn.microsoft.com/pt-br/windows/terminal/install

**Passo 3: Inicialize os recursos do Docker**
Agora que você tem uma aplicação, podemos iniciar o processo de containerização. Dentro do diretório 'docker-nodejs-sample', execute o comando 'docker init' em um terminal e siga as instruções:

Crie um Dockerfile
Crie um arquivo chamado Dockerfile na pasta principal do seu projeto. Este arquivo irá conter as instruções para construir a imagem Docker do seu projeto.

# Use uma imagem base oficial do Node.js
FROM node:14

# Defina o diretório de trabalho dentro do container
WORKDIR /usr/src/app

# Copie o arquivo package.json e package-lock.json (se existir)
COPY package*.json ./

# Instale as dependências do projeto
RUN npm install

# Copie o restante do código do projeto
COPY . .

# Exponha a porta que o aplicativo Node.js estará escutando
EXPOSE 3000

# Comando para rodar o aplicativo
CMD ["node", "src/index.js"]
Crie um arquivo .dockerignore
node_modules
npm-debug.log
Dockerfile
.dockerignore
Construa a Imagem Docker
No terminal, navegue até a pasta principal do seu projeto e execute o seguinte comando para construir a imagem Docker:

docker images
docker build -t meu-app-node .
Execute o Container:
Após a construção da imagem, você pode executar um container a partir dela com o seguinte comando:

docker images
docker run -p 3000:3000 meu-app
docker run -p 3000:3000 -d meu-app
docker ps
docker stop
docker rm CONTAINERID
docker rmi -f meu-app
Isso mapeará a porta 3000 do container para a porta 3000 do seu host, permitindo que você acesse o aplicativo Node.js em http://localhost:3000

Utilizando o Docker compose
Utilizar o Docker Compose é uma ótima maneira de gerenciar múltiplos containers Docker de forma orquestrada, especialmente útil para aplicativos que dependem de vários serviços, como bancos de dados, servidores de cache, etc. Aqui estão os passos para configurar e usar o Docker Compose com seu projeto Node.js:

Certifique-se de que o Docker Compose está instalado no seu sistema. Você pode verificar isso com o comando:

docker compose version
Crie um arquivo docker-compose.yml:

version: '3'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/usr/src/app
    environment:
      - NODE_ENV=production
Construa e Execute os Serviços:
No terminal, navegue até a pasta principal do seu projeto e execute o seguinte comando para construir e iniciar os serviços definidos no docker-compose.yml:

docker compose up --build
Verifique os Serviços:

docker compose ps
#parar serviço
docker compose down
Use docker-compose up -d quando quiser iniciar os serviços usando as imagens já construídas, sem reconstruir as imagens.

Use docker-compose up --build -d quando quiser garantir que as imagens sejam reconstruídas antes de iniciar os serviços, o que é útil após fazer alterações no código-fonte ou no Dockerfile.

Exemplo de um arquivo com dois serviços
version: '3'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/usr/src/app
    environment:
      - NODE_ENV=production

  db:
    image: mysql:8
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=mysecretpassword
      - MYSQL_DATABASE=mydatabase
      - MYSQL_USER=myuser
      - MYSQL_PASSWORD=mypassword
As variáveis de ambiente correspondem às necessidades do MySQL:

MYSQL_ROOT_PASSWORD: Define a senha do usuário root.

MYSQL_DATABASE: Define o nome do banco de dados que será criado.

MYSQL_USER: Define o nome de um usuário não-root que será criado.

MYSQL_PASSWORD: Define a senha para o usuário não-root.

Referência:
https://blog.rocketseat.com.br/containerizando-uma-aplicacao-node-js-com-docker-um-guia-passo-a-passo/

![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/1.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/2.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/3.jpg)
![Print da aula](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/4.jpg)

[Ver o arquivo RAG documents.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/RAG%20Documentos.json)

[Ver o arquivo CrewAI.json](https://github.com/ViniciusLGreco/AulasTEP/blob/main/aula7/TEP_-_CrewAI.json)
