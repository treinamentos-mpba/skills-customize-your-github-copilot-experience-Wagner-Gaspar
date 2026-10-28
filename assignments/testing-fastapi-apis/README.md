# 📘 Assignment: Testing FastAPI APIs with pytest

## 🎯 Objective

Escreva testes automatizados para uma API FastAPI usando `pytest` e `TestClient`. Verifique respostas HTTP, operações CRUD e casos de erro sem iniciar um servidor ou depender de dados de testes anteriores.

## 📝 Tasks

### 🛠️ Configure os testes e verifique rotas de leitura

#### Descrição
Crie uma suíte de testes para a API da atividade Building REST APIs with FastAPI. Use o cliente de testes do FastAPI para chamar as rotas diretamente, sem iniciar o servidor com Uvicorn.

#### Requisitos
O programa concluído deve:

- Instalar `pytest` no ambiente de desenvolvimento.
- Criar `test_main.py` e importar a aplicação FastAPI definida em `main.py`.
- Criar uma fixture que disponibilize um `TestClient` para os testes.
- Testar `GET /health` e verificar o status `200` e o JSON `{"status": "ok"}`.
- Testar `GET /tasks` e verificar que a resposta tem status `200` e contém uma lista JSON.
- Permitir executar a suíte com `pytest -q`.

### 🛠️ Teste o fluxo CRUD com dados isolados

#### Descrição
Teste a criação, consulta, atualização e exclusão de uma tarefa. Prepare os dados de teste com fixtures para que cada teste funcione independentemente dos demais.

#### Requisitos
O programa concluído deve:

- Criar uma fixture que cadastre uma tarefa de teste por meio de `POST /tasks` e disponibilize sua resposta aos testes.
- Remover a tarefa criada ao final de cada teste, quando ela ainda existir.
- Verificar que `POST /tasks` retorna status `201` e os dados da tarefa criada, incluindo um ID.
- Usar o ID retornado para consultar a tarefa e verificar que `PUT /tasks/{task_id}` atualiza seus dados.
- Verificar que `DELETE /tasks/{task_id}` retorna status `204` e que uma consulta posterior retorna status `404`.

### 🛠️ Teste validações e respostas de erro

#### Descrição
Acrescente testes para entradas inválidas e IDs inexistentes. Use parametrização quando vários casos compartilharem as mesmas verificações.

#### Requisitos
O programa concluído deve:

- Verificar que criar ou atualizar uma tarefa com título vazio retorna status `422`.
- Verificar que consultar, atualizar ou excluir uma tarefa com ID inexistente retorna status `404`.
- Verificar que o filtro `completed` em `GET /tasks` retorna apenas tarefas com o estado solicitado.
- Usar `pytest.mark.parametrize` para cobrir mais de um caso de erro sem duplicar a mesma estrutura de teste.
- Executar todos os testes com `pytest -q` e confirmar que passam sem depender de um servidor em execução.
