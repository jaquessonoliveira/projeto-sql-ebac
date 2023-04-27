# **Análise Exploratória de Dados de Crédito - SQL**

> Projeto desenvolvido durante o curso de SQL para análise de dados da EBAC.

---

# **Tópicos**

<ol type="1">
  <li>Dados;</li>
  <li>Configuração do Bucket;</li>
  <li>Tabela;</li>
  <li>Exploração dos Dados;</li>
  <li>Conclusão.</li>
</ol>

---

#  1\. **Dados**

Os dados representam informações de clientes de um banco, e contam com as seguintes colunas:

- idade = idade do cliente
- sexo = sexo do cliente (F ou M)
- dependentes = número de dependentes do cliente
- escolaridade = nível de escolaridade do cliente
- salario_anual = faixa salarial do cliente
- tipo_cartao = tipo de cartão do cliente
- qtd_produtos = quantidade de produtos comprados nos últimos 12 meses
- iteracoes_12m = quantidade de iterações/transações nos ultimos 12 meses
- meses_inativo_12m = quantidade de meses que o cliente ficou inativo
- limite_credito = limite de crédito do cliente
- valor_transacoes_12m = valor das transações dos últimos 12 meses
- qtd_transacoes_12m = quantidade de transações dos últimos 12 meses

A tabela foi criada no AWS Athena junto com o S3 Bucket com uma versão dos dados disponibilizados em: https://github.com/andre-marcos-perez/ebac-course-utils/tree/main/dataset

A base de dados do link acima contém mais linhas do que a seleção utilizada. Na prática, quanto maior a quantidade de dados utilizada, mais confiável será a análise! Neste caso houve redução para poder atender uma demanda de estudo.

---

#  2\. **Configuração do Bucket**

Configuração do bucket no AWS S3 para armazenar os dados dos clientes, que serão carregados na tabela de credito, e utilizados durante a exploração e análise de crédito.


<center>
<img src="https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/bucket.png?raw=true">
    
---

#  3\. **Tabela**

A tabela foi criada no Amazon Athena usando o recurso "S3 bucket data", com base nos arquivos que estão armazenados no bucket S3. A abordagem para criar a tabela é semelhante à execução de uma consulta no Athena.

<center>
<img src="https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/query%20tabela.png?raw=true">
    
---

#  4\. **Exploração dos Dados**

A fase inicial da análise consiste em compreender a natureza dos dados. Realizando uma exploração detalhada podemos observar:

**Qual a quantidade de linhas com as informações sobre os clientes temos na nossa base de dados?**

Query:

![Query_1](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Query_1.png?raw=true)

Resposta:

![Resposta_1](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Resposta_1.png?raw=true)

**Quais são os tipos de dados em cada coluna?**

Query:

![Query_2](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Query_2.png?raw=true)

Resposta:

![Resposta_2](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Resposta_2.png?raw=true)

**Como são os dados?**

Query:

![Query_3](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Query_3.png?raw=true)

Resposta:

![Resposta_3](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Resposta_3.png?raw=true)

> Nessa primeira visualização dos dados é possível identificar colunas que possuem valores nulos (na).

**Qual o nível de escolaridade dos clientes?**

Query:

![Query_4](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Query_4.png?raw=true)

Resposta:

![Resposta_4](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Resposta_4.png?raw=true)

Visualização gráfica:

![Planilha_4](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Planilha_4.png?raw=true)



![Gráfico_4](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Gr%C3%A1fico_4.png?raw=true)


> Com as análises acima podemos ver que 13,49% dos clientes não informaram, ou não possuem escolaridade, e que 50,94% dos clientes possuem graduação, mestrado, ou doutorado.


**Qual o limite de crédito de cada cliente de acordo com a faixa salarial, e o sexo?**

Query:

![Query_5](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Query_5.png?raw=true)

Resposta:

![Resposta_5](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Resposta_5.png?raw=true)


Visualização gráfica:

![Planilha_5](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Planilha_5.png?raw=true)



![Gráfico_5](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Gr%C3%A1fico_5.png?raw=true)

> De acordo com a análise dos dados, há uma correlação positiva entre o salário e o limite de crédito. As mulheres representam a maioria dos clientes com renda anual abaixo de 60 dólares, enquanto apenas homens foram identificados nas faixas salariais acima de 60 dólares. Essa informação pode ajudar a criar campanhas específicas para clientes de alta renda.


**O consumo do crédito disponibilizado pelo banco está correlacionado com o salário?**

Query:

![Query_6](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Query_6.png?raw=true)

Resposta:

![Resposta_6](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Resposta_6.png?raw=true)


Visualização gráfica:

![Gráfico_6](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Gr%C3%A1fico_6.png?raw=true)

> Apesar de as mulheres estarem em uma faixa salarial mais baixa que a maioria dos homens, ainda assim o consumo de crédito é muito parecido, portanto o consumo de crédito não tem correlação direta com o salário. 


**Quais as características dos clientes que possuem os maiores créditos?**

Query:

![Query_7](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Query_7.png?raw=true)

Resposta:

![Resposta_7](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Resposta_7.png?raw=true)


Visualização gráfica:

![Gráfico_7](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Gr%C3%A1fico_7.png?raw=true)

> Com a análise dos dados podemos notar que o limite de crédito não tem relação direta com a escolaridade, pois o maior limite de crédito é de alguém que não possui educação formal. Também não há uma relação entre o limite de crédito, e a bandeira do cartão oferecida ao cliente pelo banco, algo que pode ser analisado, para que seja ofertado aos clientes de alta renda uma bandeira com mais benefícios.


**Qual a quantidade de homens e mulheres no banco de dados de clientes?**

Query:

![Query_8](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Query_8.png?raw=true)

Resposta:

![Resposta_8](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Resposta_8.png?raw=true)


Visualização gráfica:

![Gráfico_8](https://github.com/jaquessonoliveira/projeto-sql-ebac/blob/main/Arquivos/Gr%C3%A1fico_8.png?raw=true)

> Os registros no banco de dados indicam que a maioria dos clientes são do sexo masculino.

---

#  5\. **Conclusão**

Através da análise exploratória dos dados de crédito foi possível extrair alguns insights:

- O salário dos clientes, assim como o limite de crédito não está relacioando a sua escolaridade;
- A maioria dos clientes tem uma renda anual abaixo dos 40 dólares, em sua maioria mulheres;
- As mulheres estão em uma faixa salarial abaixo dos 60 dólares anual;
- Os clientes de alta renda são do sexo masculino;
- Apesar de as mulheres terem uma renda menor que a dos homens, o consumo de crédito disponibilizado pelo banco é parecido;
- Não há relação entre o salário, ou limite de crédito, e a bandeira do cartão oferecida aos clientes;
- A maioria dos clientes no banco de dados são do sexo masculino (61%).

---
