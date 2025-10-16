Markdown# 📚 API Livraria

API simples feita com **Python + Django + Django REST Framework**.
Serve para gerenciar livros — cadastrar, listar, editar e excluir — tudo via API REST.

---

## 🚀 Tecnologias Usadas

* 🐍 Python 3.12+
* ⚙️ Django 5.x
* 🌐 Django REST Framework
* 🧩 SQLite (por padrão, mas pode mudar para PostgreSQL)
* ☁️ Deploy pensado para Vercel

---

## 🧱 Estrutura do Projeto

C:\Projetos\Livraria│├─ src/│ ├─ core/             # Projeto Django principal│ │ └─ settings/       # Base, dev e prod configs│ └─ apps/│ └─ livraria/         # Nosso app principal│├─ config/env/         # Arquivos de ambiente (.env)├─ tests/              # Testes futuros :)│├─ requirements.txt    # Dependências do projeto├─ vercel.json         # Configuração de deploy└─ README.md           # Este arquivo
---

## ⚙️ Como Rodar o Projeto Localmente

### 1️⃣ Clone o repositório

```bash
git clone [https://github.com/devdanias/api_livraria.git](https://github.com/devdanias/api_livraria.git)
cd api_livraria
2️⃣ Crie o ambiente virtualBashpython -m venv .venv
.\.venv\Scripts\Activate.ps1   # no Windows (PowerShell)
source .venv/bin/activate      # no Linux/macOS
3️⃣ Instale as dependênciasBashpip install -r requirements.txt
4️⃣ Configure o .envCrie o arquivo config/env/.env (ou copie o .env.example) e deixe assim:Ini, TOMLDEBUG=True
SECRET_KEY=changeme-local
ALLOWED_HOSTS=127.0.0.1,localhost
5️⃣ Rode as migraçõesBashpython src/manage.py makemigrations
python src/manage.py migrate
6️⃣ Crie um superusuário (opcional, para acessar o /admin)Bashpython src/manage.py createsuperuser
7️⃣ Suba o servidorBash# Configurando a variável de ambiente no Windows (Cmd)
set DJANGO_SETTINGS_MODULE=core.settings.dev

# Configurando a variável de ambiente no Windows (PowerShell)
$env:DJANGO_SETTINGS_MODULE="core.settings.dev"

# Configurando a variável de ambiente no Linux/macOS
export DJANGO_SETTINGS_MODULE=core.settings.dev

# Rodando o servidor
python src/manage.py runserver
Abra o navegador:👉 http://127.0.0.1:8000/api/livros/🧩 Endpoints BásicosMétodoRotaDescriçãoGET/api/livros/Lista todos os livrosPOST/api/livros/Cria um novo livroGET/api/livros/{id}/Detalha um livro específicoPUT/PATCH/api/livros/{id}/Atualiza um livroDELETE/api/livros/{id}/Remove um livro🧠 Dicas ÚteisSe mudar algo nos models:Bashpython src/manage.py makemigrations
python src/manage.py migrate
Rodar shell interativo:Bashpython src/manage.py shell
Criar dados de teste direto:Pythonfrom apps.livraria.models import Livro
Livro.objects.create(titulo="1984", autor="George Orwell", publicado_em="1949-06-08")
☁️ Deploy na VercelFaça login na VercelImporte o repositório api_livrariaDefina as variáveis de ambiente:VariávelValorDJANGO_SETTINGS_MODULEcore.settings.prodSECRET_KEY<sua chave segura>ALLOWED_HOSTS.vercel.app
