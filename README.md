# Desafio-4-lojas-Alura-Store


Com base na análise dos dados de vendas, faturamento e avaliações das quatro unidades da Alura Store, realizei um estudo comparativo para identificar qual delas apresenta o menor desempenho e eficiência geral.

Abaixo estão os gráficos que ilustram o desempenho de cada loja:

1. Faturamento Total por Loja
Este gráfico mostra o montante total arrecadado por cada unidade. Observa-se que a Loja 4 possui o menor faturamento total entre todas as lojas da rede.

2. Avaliação Média dos Clientes
A satisfação do cliente é um pilar fundamental. Embora as notas sejam próximas, a Loja 1 apresenta a menor média de satisfação, enquanto a Loja 3 lidera neste quesito. A Loja 4 mantém uma média intermediária.

3. Frete Médio por Loja
Analisamos o custo logístico. A Loja 4 possui o menor frete médio, o que sugere que ela pode estar vendendo produtos menores ou para regiões mais próximas, mas isso não foi suficiente para impulsionar seu faturamento total.

4. Distribuição de Categorias (Loja com menor faturamento)
Para a loja recomendada para venda, analisamos quais categorias compõem suas vendas para entender o perfil do seu inventário.














import pandas as pd
import matplotlib.pyplot as plt

files = ['loja_1.csv', 'loja_2.csv', 'loja_3.csv', 'loja_4.csv']
dfs = {}

for i, f in enumerate(files, 1):
    dfs[f'Loja {i}'] = pd.read_csv(f)

# Combine metrics
metrics = []
for name, df in dfs.items():
    total_revenue = df['Preço'].sum()
    avg_rating = df['Avaliação da compra'].mean()
    avg_frete = df['Frete'].mean()
    total_sales = len(df)
    metrics.append({
        'Loja': name,
        'Faturamento': total_revenue,
        'Avaliação Média': avg_rating,
        'Frete Médio': avg_frete,
        'Total de Vendas': total_sales
    })

df_metrics = pd.DataFrame(metrics)
print(df_metrics)

# Visualization 1: Total Revenue per Store
plt.figure(figsize=(10, 6))
plt.bar(df_metrics['Loja'], df_metrics['Faturamento'], color=['skyblue', 'lightgreen', 'salmon', 'orchid'])
plt.title('Faturamento Total por Loja')
plt.ylabel('Faturamento (R$)')
plt.xlabel('Loja')
plt.savefig('faturamento_por_loja.png')

# Visualization 2: Average Rating per Store
plt.figure(figsize=(10, 6))
plt.plot(df_metrics['Loja'], df_metrics['Avaliação Média'], marker='o', linestyle='-', color='orange')
plt.title('Avaliação Média por Loja')
plt.ylabel('Nota Média')
plt.xlabel('Loja')
plt.ylim(0, 5)
plt.grid(True, linestyle='--', alpha=0.7)
plt.savefig('avaliacao_media_por_loja.png')

# Visualization 3: Shipping Cost Comparison
plt.figure(figsize=(10, 6))
plt.bar(df_metrics['Loja'], df_metrics['Frete Médio'], color='lightgrey', edgecolor='black')
plt.title('Frete Médio por Loja')
plt.ylabel('Frete Médio (R$)')
plt.xlabel('Loja')
plt.savefig('frete_medio_por_loja.png')

# Find the categories of the store with lowest revenue
# Assuming revenue is a main driver for João.
worst_store_name = df_metrics.loc[df_metrics['Faturamento'].idxmin(), 'Loja']
worst_df = dfs[worst_store_name]
cat_counts = worst_df['Categoria do Produto'].value_counts()

plt.figure(figsize=(8, 8))
plt.pie(cat_counts, labels=cat_counts.index, autopct='%1.1f%%', startangle=140)
plt.title(f'Distribuição de Categorias - {worst_store_name}')
plt.savefig('categorias_pior_loja.png')


Saída de código
     Loja  Faturamento  Avaliação Média  Frete Médio  Total de Vendas
0  Loja 1   1534509.12         3.976685    34.691805             2359
1  Loja 2   1488459.06         4.037304    33.621941             2359
2  Loja 3   1464025.03         4.048326    33.074464             2359
3  Loja 4   1384497.58         3.995759    31.278997             2358


<img width="800" height="800" alt="Code_Generated_Image" src="https://github.com/user-attachments/assets/c5d81a8f-1f96-4b81-9fba-3fbd44646d27" />



<img width="1000" height="600" alt="Code_Generated_Image_Graf2" src="https://github.com/user-attachments/assets/e09f2916-29ba-4235-bc78-a44c45868161" />



<img width="1000" height="600" alt="Code_Generated_Imahe_graf3" src="https://github.com/user-attachments/assets/95806f72-cba1-436f-be1c-854b9d47dcac" />



<img width="1000" height="600" alt="Code_Generated_Image_graf4" src="https://github.com/user-attachments/assets/9c2cc32b-a906-4dd4-b169-58baf01def64" />







Com base na análise dos dados de vendas, faturamento e avaliações das quatro unidades da Alura Store, realizei um estudo comparativo para identificar qual delas apresenta o menor desempenho e eficiência geral.

Abaixo estão os gráficos que ilustram o desempenho de cada loja:

1. Faturamento Total por Loja
Este gráfico mostra o montante total arrecadado por cada unidade. Observa-se que a Loja 4 possui o menor faturamento total entre todas as lojas da rede.

2. Avaliação Média dos Clientes
A satisfação do cliente é um pilar fundamental. Embora as notas sejam próximas, a Loja 1 apresenta a menor média de satisfação, enquanto a Loja 3 lidera neste quesito. A Loja 4 mantém uma média intermediária.

3. Frete Médio por Loja
Analisamos o custo logístico. A Loja 4 possui o menor frete médio, o que sugere que ela pode estar vendendo produtos menores ou para regiões mais próximas, mas isso não foi suficiente para impulsionar seu faturamento total.

4. Distribuição de Categorias (Loja com menor faturamento)
Para a loja recomendada para venda, analisamos quais categorias compõem suas vendas para entender o perfil do seu inventário.

Loja,Faturamento Total,Avaliação Média,Frete Médio,Total de Vendas
Loja 1,"R$ 1.534.509,12",3.97,"R$ 34,69",2359
Loja 2,"R$ 1.488.459,06",4.03,"R$ 33,62",2359
Loja 3,"R$ 1.464.025,03",4.04,"R$ 33,07",2359
Loja 4,"**R$ 1.384.497,58**",3.99,"R$ 31,27",2358

Resumo das Métricas
Loja        Faturamento Total            Avaliação Média         Frete Médio    Total de Vendas
Loja 1R$    1.534.509,12                 3.97R$                  34,69          2359
Loja 2R$    1.488.459,06                 4.03R$                  33,62          2359
Loja 3R$    1.464.025,03                 4.04R$                  33,07          2359
Loja 4R$    1.384.497,58                 3.99R$                  31,27          2358


Recomendação Final para o Senhor João
Após analisar detalhadamente os indicadores, a recomendação é que o Senhor João venda a Loja 4.

Motivos da decisão:

Menor Faturamento: A Loja 4 apresentou o menor faturamento total (R$ 1.384.497,58), ficando aproximadamente R$ 150.000,00 abaixo da Loja 1, mesmo tendo praticamente o mesmo volume de vendas (apenas 1 venda a menos).

Menor Ticket Médio: Com um número de vendas quase idêntico às outras, o fato de o faturamento ser significativamente menor indica que a Loja 4 possui um "ticket médio" (valor médio por venda) inferior. Isso significa que ela precisa de mais esforço operacional para gerar menos receita em comparação com as outras unidades.

Eficiência Financeira: Embora tenha o menor custo de frete médio, essa vantagem logística não se traduz em maior rentabilidade ou volume financeiro, tornando-a a unidade menos eficiente em termos de retorno sobre a operação.

Vender a Loja 4 permitirá ao Senhor João liberar capital de uma unidade que gera o menor retorno financeiro por transação, garantindo recursos saudáveis para investir em seu novo empreendimento.
