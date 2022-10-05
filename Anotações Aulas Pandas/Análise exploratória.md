### Upload do arquivo / Abrindo caixinha de upload / Arquivo temporário

```python
from google.colab import files
arq = files.upload()
```

### Extraindo apenas os dias

```python
df["Tempo_envio"] = (df["Data Envio"] - df["Data Venda"]).dt.days
```

### Média do tempo de envio por Marca

```python
df.groupby("Marca")["Tempo_envio"].mean()
```

## **Missing Values**

### Verificando se temos dados faltantes

```python
df.isnull().sum()
```

### **E, se a gente quiser saber o Lucro por Ano e Por Marca?**

### Vamos Agrupar por ano e marca (Agrupamento por duas condições)

```python
df.groupby([df["Data Venda"].dt.year, "Marca"])["lucro"].sum()

# Data Venda  Marca          
# 2008        Adventure Works             306,641.16
#             Contoso                      56,416.00
#             Fabrikam                  1,557,020.55
# 2009        Adventure Works             405,395.08
#             Contoso                     138,258.95
#             Fabrikam                  1,034,091.35
# Name: lucro, dtype: float64
```

### Mudando os números de formato científico para float

```python
pd.options.display.float_format = '{:20,.2f}'.format
```

### Resetando o index

```python
lucro_ano = df.groupby([df["Data Venda"].dt.year, "Marca"])["lucro"].sum().reset_index()
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/421bfbc1-3d1b-4da4-a4c1-0a8db3c54913/Untitled.png)

### Qual o total de produtos vendidos?

```python
df.groupby("Produto")["Quantidade"].sum().sort_values(ascending=False)
```

### Salvando csv

```python
df.to_csv("df_vendas_novo.csv", index=False)
```

### Salvando em excel

```python
df.to_excel("df_vendas_novo.xlsx", index=False)
```
