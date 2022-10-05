### Leitura dos arquivos

```python
df1 = pd.read_excel("Aracaju.xlsx",)
df2 = pd.read_excel("Fortaleza.xlsx")
df3 = pd.read_excel("Natal.xlsx")
df4 = pd.read_excel("Recife.xlsx")
df5 = pd.read_excel("Salvador.xlsx")
```

### Juntando todos os arquivos

```python
df = pd.concat([df1, df2, df3, df4, df5])
```

### Alterando o tipo de dado da coluna LojaID

```python
df["LojaID"] = df["LojaID"].astype("object")
```

## ****Tratando valores faltantes****

### Consultando linhas com valores faltantes

```python
df.isnull().sum()
```

### Substituindo valores nulos pela média

```python
df["Vendas"].fillna(df["Vendas"].mean(), inplace=True)
```

### Substituir valores nulos por zero

```python
df["Vendas"].fillna(0, inplace=True)
```

### Apagando as linhas com valores nulos

```python
df.dropna(inplace=True)
```

### Apagando linhas com valores nulos com base em apenas 1 coluna

```python
df.dropna(subset=["Vendas"], inplace=True)
```

### Remover linhas que estejam com valores faltantes em todas as colunas

```python
df.dropna(how="all", inplace=True)
```

## ****Criando novas colunas****

### Criando a coluna de receita

```python
df["Receita"] = df["Vendas"].mul(df["Qtde"])
```

### nlargest e nsmallest

```python
df.nlargest(3, "Receita")
df.nsmallest(3, "Receita")
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2be0158e-9622-4468-bd8b-84a9839a0dc6/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e154a70d-ea85-4c51-b153-959f00157b7a/Untitled.png)

### Agrupamento por idade

```python
df.groupby("Cidade")["Receita"].sum()

"""
Cidade
Aracaju       48748.25
Fortaleza     37913.97
Natal        167227.52
Recife        51936.51
Salvador      40596.73
Name: Receita, dtype: float64
"""
```

### Ordenando o conjunto de dados

```python
df.sort_values("Receita", ascending=False).head(10)
```
