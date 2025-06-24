# Challenge Alura Store - (Oracle Next Education - ONE):

Repositório diz respeito ao primeiro desafio (Challenge) especializado em Data Science do Programa Oracle Next Education 2025 - G8. No seguinte desafio, é proposto ao estudante avaliar os dados de 4 lojas de um comerciante local, e com base em tais informações, apresentar qual seria a loja mais adequata a ser vendida pelo próprio.

## 🚩 **Objetivos Gerais:**

Com base nos dados disponibilizados pela Alura, foram propostas as
seguintes análises:

- I. Faturamento total das lojas
- II. Categorias mais e menos vendidas de produtos
- III. Média de avaliação dos clientes com relação a cada loja
- IV. Produtos mais e menos vendidos
- V. Custo médio do frete por compra realizada

Feitas as análises, foram pedidos gráficos para auxílio das mesmas. 

## 💾 **Informações sobre Instalação:**

> Caso o projeto seja rodado localmente e não em um arquivo.ipynb, serão necessários os seguintes softwares:

-  Python 3.8+
- Ambiente Python como *Jupyter Notebook* ou IDEs como *Visual Studio Code*.
-  Biblioteca *matplotlib*
-  Biblioteca *numpy*
- Módulo *collections*

> Caso a intensão for rodar o arquivo via **Google Colab**, basta fazer upload do arquivo **AluraStoreBr.ipynb** no Google Drive e então executá-lo.

## 🗂️ **Arquivos presentes no repositório:**

Único arquivo necessário para rodar projeto em nuvem ou localmente é o arquivo **AluraStoreBr.ipynb**, pois o próprio puxa dados de um outro repositório da própria Alura.

A estrutura abaixo mostra todos os arquivos contidos no diretório, **arquivos.csv praticamente não foram usados**.

- 📂 base-de-dados-challenge-1
    - loja_1.csv
    - loja_2.csv
    - loja_3.csv
    - loja_4.csv
- 📂 images
    - 1_faturamento_lojas.png
    - 2_vendas_por_categoria_A.png
    - 2_vendas_por_categoria_B.png
    - 3_media_avaliacao_lojas.png
    - 4_prods_mais_menos_vendidos.png
    - 5_media_frete_por_loja.png

- AluraStoreBr.ipynb

## 📋 **Análises Geradas (*presentes no relatório final*):**

> <p>NOTA IMPORTANTE:</p> Relatório também disponível no arquivo AluraSotreBr.ipynb.

### **0. Introdução:**

Após feitas as análises acima, com base nos dados e gráficos construídos, foi-se montado um relatório justificando a decisão de venda sobre uma das quatro lojas, acima analisadas. O conteúdo a seguir, diz respeito a decisão de venda final.

### **1. Análise Faturamento lojas:**
![grafico_ex1](https://raw.githubusercontent.com/Megalonnix/ChallengeAluraStore/refs/heads/master/images/1_faturamento_lojas.png)

Baseando-se no gráfico acima, observa-se que:
- A Loja 1 lidera em vendas brutas.
- A Loja 4 possui o menor faturamento de todas.

---
### **2. Análise de Vendas por Categoria:**
![grafico1_ex2](https://raw.githubusercontent.com/Megalonnix/ChallengeAluraStore/refs/heads/master/images/2_vendas_por_categoria_A_.png)
![grafico2_ex2](https://raw.githubusercontent.com/Megalonnix/ChallengeAluraStore/refs/heads/master/images/2_vendas_por_categoria_B.png)

Observa-se nos dois gráficos acima que:
- I. Todas as lojas ofertam o mesmo tipo de produtos, variando apenas o número de vendas por loja.
- II. A categoria de produtos mais comprada nas 4 lojas é a de *Móveis*.
- III. Observa-se que há 3 categorias com **menor índice de vendas**, sendo elas: 
    - 1º: *Utilidades domésticas*; 
    - 2º: *Livros*;
    - 3º: *Intrumentos Musicais*.

Observando o próprio gráfico acima, a categoria com menor **média** de vendas seria *Utilidades domésticas*. Conforme o cálculo abaixo:

$$
\text{Utilidades domesticas} = \frac{171 + 181 + 177 + 201}{4} = 182.5 = x
$$
$$
\text{Livros} = \frac{173+197+185+187}{4} = 185.5 = y
$$
$$
\text{Instrumentos Musicais} = \frac{182 + 224 + 177 + 170}{4} = 188.25 = z
$$
$$
\text{Logo: } z > y > x
$$

Concluímos então, com base  no gráfico acima, que em ordem de items vendidos temos
as seguintes *médias de vendas por categoria* (em ordem decrescente):

 - 1º Lugar: *Móveis*.
 - 2º Lugar: *Eletrônicos*.
 - 3º Lugar: *Brinquedos*.
 - 4º Lugar: *Eletrodomésticos*.
 - 5º Lugar: *Esporte e Lazer*.
 - 6º Lugar: *Instrumentos Musicais*.
 - 7º Lugar: *Livros*.
 - 8º Lugar: *Utilidades Domésticas*.

---
### **3. Análise da Média de avaliação das lojas:**

![grafico3](https://raw.githubusercontent.com/Megalonnix/ChallengeAluraStore/refs/heads/master/images/3_media_avaliacao_lojas.png)

Todas as lojas possuem avaliações ligeiramente diferentes umas das outras. Com:
- I. A Loja 3 tendo o maior desempenho nesse quesito.
- II. A Loja 1 possuindo o pior desempenho.

---
### **4. Análise dos Produtos Mais e Menos vendidos de cada loja:**

![grafico4](https://raw.githubusercontent.com/Megalonnix/ChallengeAluraStore/refs/heads/master/images/4_prods_mais_menos_vendidos.png)

Utilizando-se do gráfico acima, mais do *código abaixo* **(localizado nas análises feitas)**:

```python
    def getCincoItemsMaisMenosVendidos_2(numLoja=None):
        loja = escolher_loja(numLoja)
        x = list(zip(loja['Produto'], loja['Categoria do Produto']))
        count_frquencia_prods = Counter(x)
        cinco_mais_freq = count_frquencia_prods.most_common(5)
        cinco_menos_freq = count_frquencia_prods.most_common()[:-6:-1]
        
        return { 'cinco_mais_vendidos': cinco_mais_freq, 
                'cinco_menos_vendidos': cinco_menos_freq[::-1] }
```

Foram-se obtidos os items com *maiores* e *menores* índices de vendas por loja individual, mais suas categorias. Em conjunto com informações presentes na análise de vendas por categoria, foram montadas as tabelas abaixo:

<table>
  <thead>
    <tr>
        <th colspan="3">
            Loja 1 - Produtos (<span style="color:blue;">+</span>) Vendidos</th>
        </tr>
    <tr>
      <th>Nome Produto</th>
      <th>Nome Categoria</th>
      <th>Ranking Média Vendas Categoria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Micro-ondas</td>
      <td>Eletrodomésticos</td>
      <td>4º lugar</td>
    </tr>
    <tr>
      <td>TV LED UHD 4K</td>
      <td>Eletrônicos</td>
      <td>2º Lugar</td>
    </tr>
    <tr>
      <td>Guarda Roupas</td>
      <td>Móveis</td>
      <td>1º Lugar</td>
    </tr>
  </tbody>
</table>

<br>

<table>
  <thead>
    <tr><th colspan="3">Loja 1 - Produtos (<span style="color:red;">-</span>) Vendidos</th></tr>
    <tr>
      <th>Nome Produto</th>
      <th>Nome Categoria</th>
      <th>Ranking Média Vendas Categoria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Mochila</td>
      <td>Esporte e Lazer</td>
      <td>5º Lugar</td>
    </tr>
    <tr>
      <td>Pandeiro</td>
      <td>Instrumentos Musicais</td>
      <td>6º Lugar</td>
    </tr>
    <tr>
      <td>Panela de Pressão</td>
      <td>Utilidades Domésticas</td>
      <td>8º Lugar</td>
    </tr>
  </tbody>
</table>

<br>

<table>
  <thead>
    <tr>
        <th colspan="3">
            Loja 2 - Produtos (<span style="color:blue;">+</span>) Vendidos</th>
        </tr>
    <tr>
      <th>Nome Produto</th>
      <th>Nome Categoria</th>
      <th>Ranking Média Vendas Categoria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Iniciando em Programação</td>
      <td>Livros</td>
      <td>7º Lugar</td>
    </tr>
    <tr>
      <td>Microondas</td>
      <td>Eletrodomésticos</td>
      <td>4º Lugar</td>
    </tr>
    <tr>
      <td>Bateria</td>
      <td>Instrumentos Musicais</td>
      <td>6º Lugar</td>
    </tr>
  </tbody>
</table>

<br>

<table>
  <thead>
    <tr><th colspan="3">Loja 2 - Produtos (<span style="color:red;">-</span>) Vendidos</th></tr>
    <tr>
      <th>Nome Produto</th>
      <th>Nome Categoria</th>
      <th>Ranking Média Vendas Categoria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Fone de Ouvido</td>
      <td>Eletrônicos</td>
      <td>2º Lugar</td>
    </tr>
    <tr>
      <td>Poltrona</td>
      <td>Móveis</td>
      <td>1º Lugar</td>
    </tr>
    <tr>
      <td>Mesa de Jantar</td>
      <td>Móveis</td>
      <td>1º Lugar</td>
    </tr>
  </tbody>
</table>

<br>

<table>
  <thead>
    <tr>
        <th colspan="3">
            Loja 3 - Produtos (<span style="color:blue;">+</span>) Vendidos</th>
        </tr>
    <tr>
      <th>Nome Produto</th>
      <th>Nome Categoria</th>
      <th>Ranking Média Vendas Categoria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Kit Banquetas</td>
      <td>Móveis</td>
      <td>1º Lugar</td>
    </tr>
    <tr>
      <td>Mesa de Jantar</td>
      <td>Móveis</td>
      <td>1º Lugar</td>
    </tr>
    <tr>
      <td>Cama King</td>
      <td>Móveis</td>
      <td>1º Lugar</td>
    </tr>
  </tbody>
</table>

<br>

<table>
  <thead>
    <tr><th colspan="3">Loja 3 - Produtos (<span style="color:red;">-</span>) Vendidos</th></tr>
    <tr>
      <th>Nome Produto</th>
      <th>Nome Categoria</th>
      <th>Ranking Média Vendas Categoria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Copo Térmico</td>
      <td>Esporte e Lazer</td>
      <td>5º Lugar</td>
    </tr>
    <tr>
      <td>Jogo de Copos</td>
      <td>Utilidades Domésticas</td>
      <td>8º Lugar</td>
    </tr>
    <tr>
      <td>Mochila</td>
      <td>Esporte e Lazer</td>
      <td>5º Lugar</td>
    </tr>
  </tbody>
</table>

<br>

<table>
  <thead>
    <tr>
        <th colspan="3">
            Loja 4 - Produtos (<span style="color:blue;">+</span>) Vendidos</th>
        </tr>
    <tr>
      <th>Nome Produto</th>
      <th>Nome Categoria</th>
      <th>Ranking Média Vendas Categoria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Cama Box</td>
      <td>Móveis</td>
      <td>1º Lugar</td>
    </tr>
    <tr>
      <td>Faqueiro</td>
      <td>Utilidades Domésticas</td>
      <td>8º Lugar</td>
    </tr>
    <tr>
      <td>Dashboards com Power BI</td>
      <td>Livros</td>
      <td>7º Lugar</td>
    </tr>
  </tbody>
</table>

<br>

<table>
  <thead>
    <tr><th colspan="3">Loja 4 - Produtos (<span style="color:red;">-</span>) Vendidos</th></tr>
    <tr>
      <th>Nome Produto</th>
      <th>Nome Categoria</th>
      <th>Ranking Média Vendas Categoria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Lavadoura de Roupas</td>
      <td>Eletrodomésticos</td>
      <td>4º Lugar</td>
    </tr>
    <tr>
      <td>Ciência de dados com python</td>
      <td>Livros</td>
      <td>7º Lugar</td>
    </tr>
    <tr>
      <td>Violão</td>
      <td>Instrumentos Musicais</td>
      <td>6º Lugar</td>
    </tr>
  </tbody>
</table>

Com tais tabelas, torna-se perceptível quais categorias geram mais renda para cada loja.

### **5. Análise do Frete médio de vendas realizadas por loja:**

![grafico5](https://raw.githubusercontent.com/Megalonnix/ChallengeAluraStore/refs/heads/master/images/5_media_frete_por_loja.png)

Quanto aos fretes por compra: 
  - I. A Loja 1 é a que apresenta *maior taxa de frete*.
  - II. A Loja 4 é a com *menor taxa de frete*.

### 📋 Conclusão Final:
--- 

Tendo sido apresentados os pontos dessa análise, conclui-se nesse relatório que a *Loja 4* é a mais adequada para ser vendida pelo Senhor João. Abaixo apresentam-se as justificativas:

  - I. A Loja 4 possui o *menor* faturamento.
  - II. A Loja 4 possui entre seus 3 items mais vendidos, 2 dos quais estão nas categorias com *menor índice de vendas*. 
      - Sendo tais categorias *Utilidades domésticas* (8º Lugar) e *Livros* (7º Lugar).
  - III. Além do fato, a Loja 4 possui a *2º menor avaliação entre os clientes*.
