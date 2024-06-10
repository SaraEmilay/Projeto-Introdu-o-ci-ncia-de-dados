### Análise de Dados do Perfil dos Alunos - 2020

#### Introdução
Este projeto realiza uma análise detalhada dos dados de perfil dos alunos das escolas públicas e privadas do Recife em 2020. O dataset utilizado pode ser acessado através do [link](http://dados.recife.pe.gov.br/dataset/2015a954-4f3a-4ff2-84a1-f915feffd9ac/resource/6d9b3998-85fd-4c8a-9ec2-9932b9e5b90d/download/alunos.csv).

#### Estrutura do Projeto
O notebook contém as seguintes seções:

1. **Importação de Bibliotecas**: Importação das bibliotecas essenciais para a análise de dados, como pandas, numpy e matplotlib.
2. **Carregamento dos Dados**: Leitura do arquivo CSV contendo os dados dos alunos.
3. **Exploração dos Dados**: Análise inicial para entender a estrutura dos dados, incluindo:
    - Visualização das primeiras linhas do dataset.
    - Resumo estatístico das variáveis numéricas.
    - Informações sobre valores ausentes e tipos de dados.
4. **Limpeza dos Dados**: Tratamento de valores ausentes, remoção de duplicatas e correção de tipos de dados, se necessário.
5. **Análise Descritiva**:
    - Distribuição dos alunos por gênero.
    - Distribuição dos alunos por faixa etária.
    - Análise da distribuição de alunos entre escolas públicas e privadas.
    - Distribuição geográfica dos alunos.
6. **Visualização de Dados**: Criação de gráficos e visualizações para melhor compreensão dos dados, incluindo histogramas, gráficos de barras e mapas.
7. **Teste de Normalidade**:
    - Aplicação do teste de Shapiro-Wilk para verificar a normalidade de várias colunas do conjunto de dados.
    - Interpretação dos resultados do teste de normalidade.
8. **Conclusões**: Sumário dos principais insights obtidos a partir da análise.

#### Descrição do Teste de Normalidade
Este projeto utiliza o teste de Shapiro-Wilk para verificar a normalidade de várias colunas em um conjunto de dados. A normalidade dos dados é uma suposição comum em muitas técnicas estatísticas e de machine learning, tornando este teste uma ferramenta importante para a análise exploratória de dados.

#### Código
```python
from scipy.stats import shapiro

colunas = ['NU_MES', 'NU_ANO', 'NU_IDADE', 'TP_COR_RACA', 'TP_DEPENDENCIA', 'TP_LOCALIZACAO', 'IN_NECESSIDADE_ESPECIAL']

resultados = df[colunas].apply(lambda coluna: shapiro(coluna.dropna()), axis=0)

print(resultados)
```

#### Explicação do Código
O código acima executa o teste de Shapiro-Wilk para verificar a normalidade das colunas especificadas em um DataFrame. Aqui está uma explicação detalhada de cada parte do código:

#### Importação da Função Shapiro-Wilk
```python
from scipy.stats import shapiro
```
Esta linha importa a função shapiro da biblioteca scipy.stats, que é usada para realizar o teste de Shapiro-Wilk.

#### Definição das Colunas
```python
colunas = ['NU_MES', 'NU_ANO', 'NU_IDADE', 'TP_COR_RACA', 'TP_DEPENDENCIA', 'TP_LOCALIZACAO', 'IN_NECESSIDADE_ESPECIAL']
```
Esta linha define uma lista de nomes de colunas que serão testadas para normalidade. Essas colunas devem estar presentes no DataFrame df.

#### Aplicação do Teste de Shapiro-Wilk
```python
resultados = df[colunas].apply(lambda coluna: shapiro(coluna.dropna()), axis=0)
df[colunas]: Seleciona apenas as colunas especificadas no DataFrame df.
.apply(lambda coluna: shapiro(coluna.dropna()), axis=0):
```
Aplica uma função lambda a cada coluna selecionada. A função lambda faz o seguinte:
- coluna.dropna(): Remove os valores ausentes (NaNs) da coluna para que o teste de Shapiro-Wilk possa ser aplicado.
- shapiro(coluna.dropna()): Aplica o teste de Shapiro-Wilk à coluna sem valores ausentes.
- axis=0: Especifica que a função lambda deve ser aplicada ao longo das colunas.
 
#### Impressão dos Resultados
```python
print(resultados)
```
Esta linha imprime os resultados do teste de Shapiro-Wilk para cada coluna. Cada resultado é uma tupla contendo dois valores:

#### O valor do teste estatístico.
- O valor-p (p-value), que indica a probabilidade de que a amostra siga uma distribuição normal. Se o valor-p for menor que um certo nível de significância (por exemplo, 0.05), rejeita-se a hipótese nula de que a amostra segue uma distribuição normal.

### Metodologia
A metodologia usada neste projeto inclui:

- **Importação de Bibliotecas:** Importação da função necessária para realizar o teste estatístico.
- **Preparação dos Dados:** Seleção das colunas relevantes e tratamento de valores ausentes para garantir que o teste possa ser aplicado corretamente.
- **Aplicação do Teste de Normalidade:** Uso do teste de Shapiro-Wilk para verificar a normalidade das distribuições das colunas selecionadas.
- **Interpretação dos Resultados:** Análise dos valores-p para determinar se as colunas seguem uma distribuição normal, o que é crucial para muitas análises estatísticas subsequentes.

### Conclusão
Este projeto demonstra como realizar e interpretar o teste de Shapiro-Wilk para verificar a normalidade dos dados em um conjunto de dados. A verificação de normalidade é um passo importante na análise de dados, especialmente em preparações para técnicas estatísticas que assumem distribuições normais.
