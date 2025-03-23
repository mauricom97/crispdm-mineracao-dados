# Mineração de Dados com CRISP-DM

Este repositório contém um projeto de mineração de dados seguindo as três primeiras etapas do processo **CRISP-DM**:

1. **Entendimento do Negócio**
2. **Entendimento dos Dados**
3. **Preparação dos Dados**

O objetivo é explorar diferentes técnicas de mineração de dados, incluindo classificação, regressão, clusterização, associação e detecção de anomalias.

## Estrutura do Projeto

- `data/` - Conjunto de dados utilizados ou gerados no projeto.
- `notebooks/` - Códigos e análises em Jupyter Notebook.
- `src/` - Implementações principais em Python.
- `README.md` - Documentação do projeto.

## Instalação e Configuração

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/crispdm-mineracao-dados.git
   cd crispdm-mineracao-dados
   ```

2. Crie um ambiente virtual e instale as dependências:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate  # Windows
   pip install -r requirements.txt
   ```

## Exemplos de Código

### 1. Classificação com Random Forest
```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier

# Carregar dados
dados = load_iris()
X_train, X_test, y_train, y_test = train_test_split(dados.data, dados.target, test_size=0.2, random_state=42)

# Treinar modelo
modelo = RandomForestClassifier()
modelo.fit(X_train, y_train)

# Fazer previsão
print("Previsão:", modelo.predict(X_test[:5]))
```

### 2. Gerando Dados Falsos com Faker
```python
from faker import Faker
import pandas as pd
import random

fake = Faker()
dados = []
for _ in range(1000):
    usuario = {
        "id": fake.uuid4(),
        "idade": random.randint(18, 65),
        "tempo_no_site": round(random.uniform(0.5, 10.0), 2),
        "num_paginas_vistas": random.randint(1, 20),
        "comprou": random.choice([0, 1])
    }
    dados.append(usuario)

df = pd.DataFrame(dados)
df.to_csv("data/dados_ecommerce.csv", index=False)
print(df.head())
```

