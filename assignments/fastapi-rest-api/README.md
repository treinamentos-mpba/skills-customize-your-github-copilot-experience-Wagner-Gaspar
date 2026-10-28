# 📘 Assignment: Building REST APIs with FastAPI

## 🎯 Objective

Construa uma API REST com FastAPI para gerenciar tarefas, praticando rotas HTTP, parâmetros de caminho e consulta, validação de dados e operações CRUD.

## 📝 Tasks

### 🛠️ Configure a aplicação FastAPI

#### Descrição
Crie uma aplicação FastAPI que possa ser iniciada localmente e disponibilize uma rota simples para verificar se a API está funcionando.

#### Requisitos
O programa concluído deve:

- Instalar `fastapi` e `uvicorn` no ambiente Python.
- Definir a aplicação FastAPI em `main.py`.
- Expor `GET /health`, retornando o JSON `{"status": "ok"}`.
- Permitir iniciar o servidor com `uvicorn main:app --reload`.

### 🛠️ Consultar a lista de tarefas

#### Descrição
Armazene tarefas em uma lista em memória e crie rotas para consultar todas as tarefas ou uma tarefa específica.

#### Requisitos
O programa concluído deve:

- Representar cada tarefa com, no mínimo, `id`, `title` e `completed`.
- Expor `GET /tasks` para retornar a lista de tarefas e aceitar o parâmetro de consulta opcional `completed` para filtrar pelo estado.
- Expor `GET /tasks/{task_id}` para retornar uma tarefa pelo ID.
- Retornar o status HTTP `404` quando o ID não corresponder a uma tarefa.

### 🛠️ Criar tarefas com dados validados

#### Descrição
Use um modelo Pydantic como entrada de `POST /tasks` para validar os dados enviados e adicionar uma tarefa à lista. Por exemplo, o corpo da requisição pode ser `{"title": "Study FastAPI"}`.

#### Requisitos
O programa concluído deve:

- Exigir um título não vazio no modelo de entrada.
- Definir `completed` como `false` quando esse campo não for informado.
- Gerar um ID para a nova tarefa e adicioná-la à lista.
- Retornar a tarefa criada com o status HTTP `201`.

### 🛠️ Atualizar e excluir tarefas

#### Descrição
Complete as operações CRUD permitindo atualizar ou excluir uma tarefa existente pelo ID.

#### Requisitos
O programa concluído deve:

- Expor `PUT /tasks/{task_id}` para atualizar o título e o estado `completed` de uma tarefa usando um modelo Pydantic.
- Expor `DELETE /tasks/{task_id}` para remover uma tarefa e responder com o status HTTP `204`.
- Retornar o status HTTP `404` quando uma atualização ou exclusão receber um ID inexistente.
- Manter a lista atualizada após cada operação; os dados podem permanecer em memória e reiniciar com o servidor.
