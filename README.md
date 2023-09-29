# **Manutenção Preditiva**

## Sobre o problema:

Na indústria de fabricação de alumínio, fornos rotativos basculantes equipados com um sistema de combustão de oxigênio-gás têm sido amplamente adotados por muitos anos. Esses fornos são conhecidos por fornecer metal de alta qualidade e exigir esforços mínimos de manutenção. No entanto, ainda existem problemas de qualidade que podem ser aprimorados ainda mais com estratégias de manutenção preditiva. Aumentar a frequência das atividades de manutenção pode ajudar a lidar com esses problemas, mas também resulta em mais tempo de inatividade e custos de manutenção mais elevados.

O objetivo principal deste projeto é determinar o momento ideal para a manutenção com base nas previsões do modelo preditivo. Vamos assumir que a manutenção é realizada após cada ciclo "ruim". Se pudermos prever com precisão um ciclo ruim, podemos minimizar o tempo de inatividade para apenas 30 minutos e incorrer em um custo de R$16.000. No entanto, se um ciclo ruim passar despercebido, a manutenção exigirá uma hora completa de tempo de inatividade, resultando em uma perda de R$32.560. Além disso, haverá custos adicionais com mão de obra de R$300 por hora. Não detectar ciclos de decapagem de baixa qualidade pode levar a níveis mais elevados de escória preta, com cada quilo de escória preta custando pelo menos R$60. A baixa qualidade do metal pode resultar em 50 quilos a mais de escória preta em comparação com o metal de boa qualidade. Portanto, alarmes oportunos para ciclos de decapagem de baixa qualidade são fundamentais para potencialmente evitar perdas significativas nos negócios.

## Dados
O projeto utiliza três tabelas de dados principais:

**a) Sensor.csv**
- Dados de sensores do OSIPi, contendo dados de séries temporais com 27 colunas.
- Colunas iniciadas com "B_" são derivadas de sensores.
- Cada ciclo durante o período atual é identificado de forma única pelo "ID do ciclo".
- A coluna "Bom/Ruim" indica se o ciclo é classificado como bom ou ruim.
- A coluna "timestamp" representa o momento de conclusão do ciclo.
- A taxa de amostragem não é constante, pois apenas os pontos de dados de "grande mudança" são registrados no banco de dados.

**b) Sensor_high freq.csv**
- Dados de sensores do controlador, apresentando dados com uma frequência mais alta e uma taxa de amostragem não constante.
- Esses dados de séries temporais consistem em 8 colunas, com aquelas iniciadas com "B" originárias de controladores.
- A coluna "Percentagem" indica a porcentagem de ocupação do transportador, que é crucial para o processo de decapagem.
- Diferentes porcentagens de ocupação do transportador exigem ajustes nos parâmetros de combustível, fluxo de ar e outros.
- Duas colunas de referência, "Percentagem_mínima" e "Percentagem_máxima," podem ser encontradas em "Percent_reference.csv," definindo a faixa aceitável de porcentagem de ocupação do transportador para os valores correspondentes relacionados à combustão.

**c) Percent_reference.csv**
- Fornece dados relacionados à combustão e receitas para diferentes porcentagens de ocupação do transportador.
- Ao contrário dos outros conjuntos de dados, esses dados não estão em um formato de séries temporais.


Notas
a) 
Python Enviroment with Package Versions
  Please use a Python 3.7+ environment with the following packages:
  Pandas==1.2.4
  scikit-learn==0.24.2
  numpy==1.17.4
  matplotlib==3.1.1
