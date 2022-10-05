### Importar a biblioteca Pandas

```python
#importando a biblioteca pandas
import pandas as pd

df = pd.read_csv("/content/drive/MyDrive/Database/Gapminder.csv", error_bad_lines=False, sep=";")

# error_bad_lines # para ignorar as linhas com erro e pular
# sep # para ler o separador como ";" ao invés do padrão ","
```

### Visualizando as 5 primeiras linhas

```python
df.head()

```

### Renomeado as colunas

```python
df = df.rename(columns={"country":"País", "continent": "Continente", "year": "Ano", "lifeExp": "Expectativa de vida", "pop": "População", "gdpPercap": "PIB"})
df.head()
```

### Total de linhas e colunas

```python
df.shape

# (3312, 6)
```

### Retornar apenas os nomes das colunas

```python
df.columns

# df.columns
Index(['País', 'Continente', 'Ano', 'Expectativa de vida', 'População', 'PIB'], dtype='object')
```

### O tipo de dado em cada coluna

```python
df.dtypes

# País                    object
# Continente              object
# Ano                      int64
# Expectativa de vida    float64
# População                int64
# PIB                    float64
# dtype: object
```

### Retornar as últimas linhas

```python
df.tail()
```

### Retornar informações estatísticas do conjunto de dados

```python
df.describe()
```

### Filtro no conjunto de dados

```python
df["Continente"].unique()

# array(['Asia', 'Europe', 'Africa', 'Americas', nan, 'FSU', 'Oceania'],
#     dtype=object)

Oceania = df.loc[df['Continente'] == "Oceania"]
Oceania.head()
```

### Fazer agrupamento

```python
df.groupby("Continente")["País"].nunique()

"""
Continente
Africa      51
Americas    25
Asia        41
Europe      35
FSU          6
Oceania      3
Name: País, dtype: int64
"""

df.groupby("Ano")["Expectativa de vida"].mean()

...
```

Outros métodos

```python
df["PIB"].mean() # A média do PIB

df["PIB"].sum() # Soma do PIB
```
