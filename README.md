Read pasted-text.txtThought for 3sAqui está o texto formatado em Markdown padrão para o README do GitHub:

```markdown
# 📚 API Livraria

API simples feita com **Python + Django + Django REST Framework**.  
Serve pra gerenciar livros — cadastrar, listar, editar e excluir — tudo via API REST.

---

## 🚀 Tecnologias usadas

- 🐍 Python 3.12+
- ⚙️ Django 5.x
- 🌐 Django REST Framework
- 🧩 SQLite (por padrão, mas pode mudar pra PostgreSQL)
- ☁️ Deploy pensado pra Vercel

---

## 🧱 Estrutura do projeto

```

C:\Projetos\Livraria
│
├─ src/
│  ├─ core/              # Projeto Django principal
│  │  └─ settings/       # Base, dev e prod configs
│  └─ apps/
│     └─ livraria/       # Nosso app principal
│
├─ config/env/           # Arquivos de ambiente (.env)
├─ tests/                # Testes futuros :)
│
├─ requirements.txt      # Dependências do projeto
├─ vercel.json           # Configuração de deploy
└─ README.md             # Este arquivo

```plaintext

---

## ⚙️ Como rodar o projeto localmente

### 1️⃣ Clone o repositório

```bash
git clone https://github.com/devdanias/api_livraria.git
cd api_livraria
```

### 2️⃣ Crie o ambiente virtual

```shellscript
python -m venv .venv
.\.venv\Scripts\Activate.ps1   # no Windows
```

### 3️⃣ Instale as dependências

```shellscript
pip install -r requirements.txt
```

### 4️⃣ Configure o .env

Crie o arquivo `config/env/.env` (ou copie o `.env.example`) e deixe assim:

```ini
DEBUG=True
SECRET_KEY=changeme-local
ALLOWED_HOSTS=127.0.0.1,localhost
```

### 5️⃣ Rode as migrações

```shellscript
python src/manage.py makemigrations
python src/manage.py migrate
```

### 6️⃣ Crie um superusuário (opcional, pra acessar o /admin)

```shellscript
python src/manage.py createsuperuser
```

### 7️⃣ Suba o servidor

```shellscript
$env:DJANGO_SETTINGS_MODULE="core.settings.dev"
python src/manage.py runserver
```

Abra o navegador:👉 [http://127.0.0.1:8000/api/livros/](http://127.0.0.1:8000/api/livros/)

---

## Endpoints básicos

| Método | Rota | Descrição
|-----|-----|-----
| GET | `/api/livros/` | Lista todos os livros
| POST | `/api/livros/` | Cria um novo livro
| GET | `/api/livros/{id}/` | Detalha um livro específico
| PUT/PATCH | `/api/livros/{id}/` | Atualiza um livro
| DELETE | `/api/livros/{id}/` | Remove um livro


---

## Dicas úteis

**Se mudar algo nos models:**

```shellscript
python src/manage.py makemigrations
python src/manage.py migrate
```

**Rodar shell interativo:**

```shellscript
python src/manage.py shell
```

**Criar dados de teste direto:**

```python
from apps.livraria.models import Livro
Livro.objects.create(titulo="1984", autor="George Orwell", publicado_em="1949-06-08")
```

---

## ️ Deploy na Vercel

1. Faça login na Vercel
2. Importe o repositório `api_livraria`
3. Defina as variáveis de ambiente:

1. `DJANGO_SETTINGS_MODULE=core.settings.prod`
2. `SECRET_KEY=<sua chave>`
3. `ALLOWED_HOSTS=.vercel.app`



4. Deploy automático 🎉
