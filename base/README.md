# Base — Controle De Treinos

Esta é a aplicação-base da avaliação de reposição.

Ela já possui CRUD de treinos com SQLite. O arquivo `auth.py` também já foi iniciado com Blueprint, mas a autenticação com `session` ainda precisa ser implementada.

## Executar

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```

Acesse `http://127.0.0.1:5000`.

## Arquivos Principais

- `app.py`: rotas Flask.
- `auth.py`: módulo de autenticação já iniciado, ainda sem rotas cadastradas.
- `database.py`: funções de banco de dados.
- `templates/`: páginas HTML.

## Observação

Não substitua a aplicação por outro projeto. A tarefa é adaptar esta base para autenticação com `session`, completando o módulo `auth.py` e mantendo as rotas de treinos em `app.py`.


JUSTIFICATIVA

1-Por que as rotas de autenticação foram movidas para auth.py?
Foram movidas para usar o Blueprint do Flask. Isso serve para organizar o projeto e separar as rotas de login, registro e logout das rotas principais em app.py.

2-Como a aplicação identifica o usuário logado usando session?
Após validar as credenciais no login, o id do usuário é salvo na session. A aplicação lê essa chave da session para saber qual usuário está ativo.  

3-Como o código impede que um usuário acesse treinos de outro usuário?
Salvando o id do usuário no banco de dados na hora de criar o treino e filtrando a busca na consulta do SQL para mostrar apenas os treinos onde o usuario_id seja igual ao id da session.  