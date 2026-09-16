# PostgreSQL com Docker Compose

Projeto para instalação e configuração de um banco de dados PostgreSQL utilizando Docker Compose, com scripts Python para geração e carga de dados nas tabelas.

Este guia foi construído com base numa máquina virtual **Ubuntu**, por isso os passos incluem desde a instalação das dependências primárias (Docker, Python, venv) até a carga dos dados.

## 📋 Pré-requisitos

- Máquina Ubuntu (física ou virtual)
- Acesso à internet
- Permissões de `sudo`

## 🚀 Passo a passo

### 1. Clonar o repositório

```bash
git clone https://github.com/edamis/postgresql
cd postgresql
```

### 2. Instalar o Docker

```bash
sudo apt update
sudo apt install -y docker.io docker-compose
sudo systemctl enable docker
sudo systemctl start docker
```

Verifique se a instalação funcionou:

```bash
docker --version
docker-compose --version
```

### 3. Subir o container com Docker Compose

```bash
docker-compose up -d
```

Esse comando sobe o container do PostgreSQL de acordo com as configurações definidas no arquivo `docker-compose.yml` (porta, usuário, senha e nome do banco).

Para verificar se o container está rodando:

```bash
docker ps
```

### 4. Testar a conexão com o banco

💡 Use as credenciais definidas no `docker-compose.yml` para testar o acesso:


### 5. Habilitar o ambiente virtual Python (venv)

```bash
sudo apt install -y python3-venv
cd scripts
python3 -m venv venv
source venv/bin/activate
```

Instale as dependências do projeto (se houver um `requirements.txt`):

```bash
pip install -r requirements.txt
```
Instale as dependências do pacote python pandas

```bash
pip install pandas
```

### 6. Gerar e inserir os dados

Com o ambiente virtual ativado, execute os scripts para popular as tabelas do banco:

```bash
python scripts/generate_data.py
python scripts/insert_data.py
```

### 7. Desativar o ambiente virtual (opcional)

Ao terminar, você pode sair do ambiente virtual com:

```bash
deactivate
```

## 🗂 Estrutura esperada do projeto

```
postgresql/
├── docker-compose.yml
├── scripts/
│   ├── generate_data.py
│   ├── insert_data.py
│   └── requirements.txt
└── README.md
```

## 🛠 Tecnologias utilizadas

- Docker / Docker Compose
- PostgreSQL
- Python 3


