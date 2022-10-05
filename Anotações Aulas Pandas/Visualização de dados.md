### # Biblioteca Matplotlib (Integrado ao pandas)
# Gráfico de barras

```python
df["LojaID"].value_counts(ascending=False).plot.bar()

df["LojaID"].value_counts(ascending=False).plot.barh()

df["LojaID"].value_counts(ascending=True).plot.barh();
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8c21c252-0251-47f1-9ee0-dcd044dda1c9/Untitled.png)

### Gráfico de Pizza

```python
df.groupby(df["Data"].dt.year)["Receita"].sum().plot.pie()
```

Total de vendas por cidade

```python
df["Cidade"].value_counts()
```

### # Adicionando um título e alterando o nome dos eixos
Precisa importar o matplotlib.pyplot

```python
import matplotlib.pyplot as plt
df["Cidade"].value_counts().plot.bar(title="Total vendas por Cidade")
plt.xlabel("Cidade")
plt.ylabel("Total Vendas");
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4ac932ae-59c6-4373-8563-41be144ea6e6/Untitled.png)

### Alterar a cor

```python
df["Cidade"].value_counts().plot.bar(title="Total vendas por Cidade", color="red")
plt.xlabel("Cidade")
plt.ylabel("Total Vendas");
```

### Alterando o estilo

```python
df.groupby(df["Mes_venda"])["Qtde"].sum().plot(title="Total Produtos Vendidos x Mês")
plt.xlabel("Mês")
plt.ylabel("Total Produtos Vendidos")
plt.legend();
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48282a18-0d1f-4aa6-8fec-89fa0550dccf/Untitled.png)

### Selecionando apenas as vendas de 2019

```python
df_2019 = df[df["Ano_venda"] == 2019]

df_2019.groupby(df_2019["Mes_venda"])["Qtde"].sum()

# Mes_venda
# 1    1541
# 2     128
# 3     460
# 4      12
# Name: Qtde, dtype: int64
```

### Total produtos vendidos por mês

```python
df_2019.groupby(df_2019["Mes_venda"])["Qtde"].sum().plot(marker = "o")
plt.xlabel("Mês")
plt.ylabel("Total Produtos Vendidos")
plt.legend();
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f617986e-5f7e-44b7-90d7-0f86bcaa117a/Untitled.png)

### Histograma

```python
plt.hist(df["Qtde"], color="lightsalmon");
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a369cdb9-6e6e-4013-8223-a3fe7aa00534/Untitled.png)

### Gráfico de dispersão

```python
plt.scatter(x = df_2019["Dia_venda"], y = df_2019["Receita"]);
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4cf2744b-b230-498e-b3e3-e7dcdc6fc0d4/Untitled.png)

### Salvando em png

```python
df_2019.groupby(df_2019["Mes_venda"])["Qtde"].sum().plot(marker = "v")
plt.title("Quantidade de produtos vendidos x Mês")
plt.xlabel("Mês")
plt.ylabel("Total Produtos Vendidos")
plt.legend()
plt.savefig("grafico QTDE x MES.png")
```
