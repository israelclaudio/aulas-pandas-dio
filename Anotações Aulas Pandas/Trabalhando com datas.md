### Transformando a coluna de data em tipo inteiro

```python
df["Data"] = df["Data"].view("int64")
```

### Transformando a coluna de data em data

```python
df["Data"] = pd.to_datetime(df["Data"])
```

### Agrupamento por ano

```python
df.groupby(df["Data"].dt.year)["Receita"].sum()

# Data
# 2018    118176.53
# 2019    228246.45
# Name: Receita, dtype: float64
```

### Criando uma nova coluna com o ano

```python
df["Ano_venda"] = df["Data"].dt.year
```

### Extraindo o mês e o dia

```python
df["Mes_venda"], df["Dia_venda"] = (df["Data"].dt.month, df["Data"].dt.day)
```

### Criando a coluna de trimestre

```python
df["Trimestre_venda"] = df["Data"].dt.quarter
```

### Filtrando as vendas de 2019 do mês de março

```python
vendas_marco_19 = df.loc[(df["Data"].dt.year == 2019) & (df["Data"].dt.month == 3)]
```
