# Checkpoint-4-ML-Modelo-Diabetes-RL

## Visão Geral

Neste repositório contém o Modelo de Machine Learning criado durante o Checkpoint 4 da matéria Disruptive Architectures IoT, IOB e Generative IA. 

Nesse repositório se encontra especificamente o modelo de Regressão Logistica criado com o Dataset sobre incidencia de Diabetes no povo Pima.

Segue um passo a passo para a execução local deste modelo.

---

## Pré-requisitos

Antes de iniciar, verifique se você possui:

- Python instalado
- Docker Desktop instalado e em execução
- um editor de código, como VS Code
- Postman instalado

---

## Etapa 1 - Clonar o repositório

- Aqui neste repositório no git hub, clique no botão verde escrito "<> Code"
- Copie o link no pop-up que irá aparecer em seguida
- Abra o terminal do seu Sistema Operacional
- Digite o seguinte código:
```bash
git clone [Cole aqui o link do repositório]
```

Isso irá realizar o download do repositório no seu computador.

---

## Etapa 2 - Executar a aplicação localmente

Abra a pasta do projeto no seu editor de código.

No terminal, dentro da pasta do projeto, execute o seguinte código:

```bash
pip install -r requirements.txt
```

Depois execute:

```bash
python inference.py
```

Se tudo estiver correto, aparecerá algo semelhante a:

```text
Running on http://0.0.0.0:8000
```

---

## Etapa 3 — Testar a API no Postman

### Criar a requisição

1. Abra o **Postman**
2. Clique em **New**
3. Clique em **HTTP Request**

### Configurar a requisição

**Método**

```text
POST
```

**URL**

```text
http://localhost:8000/predict
```

### Configurar o Body

1. Clique na aba **Body**
2. Selecione **raw**
3. No seletor à direita escolha **JSON**

Exemplo de corpo de requisição:

```json
[
  {
    "Pregnancies": 6,
    "Glucose": 148,
    "BloodPressure": 72,
    "SkinThickness": 35,
    "Insulin": 0,
    "BMI": 33,
    "DiabetesPedigreeFunction": 0,
    "Age": 50
  }
]
```

Clique em **Send**.

Resposta esperada:

```json
{
  "predicao": [1]
}
```

> [!TIP]
> Se a API estiver rodando, mas o Postman não retornar a predição, confira primeiro se o método está como **POST** e se o body está como **raw + JSON**.

---

## Etapa 4 — Construir a imagem Docker (opcional)

No terminal:

```bash
docker build -t modelocolunadt .
```

Esse comando cria uma imagem Docker contendo toda a aplicação.

---

## Etapa 5 — Executar o container

```bash
docker run -p 8000:8000 modelo
```

Isso inicia o container e disponibiliza a aplicação na porta 8000.

---

## Etapa 6 — Testar novamente no Postman

Com o container rodando, volte ao Postman e repita o processo realizado na **Etapa 3**

---
