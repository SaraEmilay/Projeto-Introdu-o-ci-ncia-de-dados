<!DOCTYPE html>
<html lang="pt-br">

<body>
    <h1>Projeto: Análise dos Dados</h1>
    <h2>Descrição</h2>
    <p>Este projeto utiliza o teste de Shapiro-Wilk para verificar a normalidade de várias colunas em um conjunto de dados. A normalidade dos dados é uma suposição comum em muitas técnicas estatísticas e de machine learning, tornando este teste uma ferramenta importante para a análise exploratória de dados.</p>
    
  <h2>Código</h2>
  <pre><code>from scipy.stats import shapiro

colunas = ['NU_MES', 'NU_ANO', 'NU_IDADE', 'TP_COR_RACA', 'TP_DEPENDENCIA', 'TP_LOCALIZACAO', 'IN_NECESSIDADE_ESPECIAL']

resultados = df[colunas].apply(lambda coluna: shapiro(coluna.dropna()), axis=0)

print(resultados)</code></pre>

  <h2>Explicação do Código</h2>
  <p>O código acima executa o teste de Shapiro-Wilk para verificar a normalidade das colunas especificadas em um DataFrame. Aqui está uma explicação detalhada de cada parte do código:</p>
  
  <h3>Importação da Função Shapiro-Wilk</h3>
  <pre><code>from scipy.stats import shapiro</code></pre>
  <p>Esta linha importa a função <code>shapiro</code> da biblioteca <code>scipy.stats</code>, que é usada para realizar o teste de Shapiro-Wilk.</p>
  
  <h3>Definição das Colunas</h3>
  <pre><code>colunas = ['NU_MES', 'NU_ANO', 'NU_IDADE', 'TP_COR_RACA', 'TP_DEPENDENCIA', 'TP_LOCALIZACAO', 'IN_NECESSIDADE_ESPECIAL']</code></pre>
  <p>Esta linha define uma lista de nomes de colunas que serão testadas para normalidade. Essas colunas devem estar presentes no DataFrame <code>df</code>.</p>
  
  <h3>Aplicação do Teste de Shapiro-Wilk</h3>
  <pre><code>resultados = df[colunas].apply(lambda coluna: shapiro(coluna.dropna()), axis=0)</code></pre>
  <p>
      <ul>
          <li><code>df[colunas]</code>: Seleciona apenas as colunas especificadas no DataFrame <code>df</code>.</li>
          <li><code>.apply(lambda coluna: shapiro(coluna.dropna()), axis=0)</code>: Aplica uma função lambda a cada coluna selecionada. A função lambda faz o seguinte:
              <ul>
                  <li><code>coluna.dropna()</code>: Remove os valores ausentes (NaNs) da coluna para que o teste de Shapiro-Wilk possa ser aplicado.</li>
                  <li><code>shapiro(coluna.dropna())</code>: Aplica o teste de Shapiro-Wilk à coluna sem valores ausentes.</li>
              </ul>
          </li>
          <li><code>axis=0</code>: Especifica que a função lambda deve ser aplicada ao longo das colunas.</li>
      </ul>
  </p>
  
  <h3>Impressão dos Resultados</h3>
  <pre><code>print(resultados)</code></pre>
  <p>Esta linha imprime os resultados do teste de Shapiro-Wilk para cada coluna. Cada resultado é uma tupla contendo dois valores:</p>
  <ul>
      <li>O valor do teste estatístico.</li>
      <li>O valor-p (p-value), que indica a probabilidade de que a amostra siga uma distribuição normal. Se o valor-p for menor que um certo nível de significância (por exemplo, 0.05), rejeita-se a hipótese nula de que a amostra segue uma distribuição normal.</li>
  </ul>
  
  <h2>Metodologia</h2>
  <p>A metodologia usada neste projeto inclui:</p>
  <ul>
      <li><strong>Importação de Bibliotecas:</strong> Importação da função necessária para realizar o teste estatístico.</li>
      <li><strong>Preparação dos Dados:</strong> Seleção das colunas relevantes e tratamento de valores ausentes para garantir que o teste possa ser aplicado corretamente.</li>
      <li><strong>Aplicação do Teste de Normalidade:</strong> Uso do teste de Shapiro-Wilk para verificar a normalidade das distribuições das colunas selecionadas.</li>
      <li><strong>Interpretação dos Resultados:</strong> Análise dos valores-p para determinar se as colunas seguem uma distribuição normal, o que é crucial para muitas análises estatísticas subsequentes.</li>
  </ul>
  
  <h2>Conclusão</h2>
  <p>Este projeto demonstra como realizar e interpretar o teste de Shapiro-Wilk para verificar a normalidade dos dados em um conjunto de dados. A verificação de normalidade é um passo importante na análise de dados, especialmente em preparações para técnicas estatísticas que assumem distribuições normais.</p>
</body>
</html>
