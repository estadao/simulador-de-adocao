# Simulação mostra quais crianças são adotadas (e quais não são) no Brasil

Esse repositório contém o código que gerou as análises [desta matéria](https://arte.estadao.com.br/brasil/adocao/criancas/).

Menino de 14 anos, pardo e com irmãos. Menina de 2 anos, branca e filha única. Este material ajuda a entender o contraste entre as crianças disponíveis para adoção e as características mais buscadas por possíveis pais.


## Como foi feito?

Os dados apresentados nesta página possuem três origens diferentes.

Duas delas são o Instituto Brasileiro de Geografia e Estatística (IBGE), que traz números sobre as características da população de crianças e adolescentes no Brasil, e o Cadastro Nacional de Adoção (CNA), que detalha quais são as características que os pretendentes buscam ao adotar.

A outra é resultado das simulações feitas pelo Estadão. Com base em números reais provenientes das duas fontes acima, criamos um algoritmo que gera crianças e pretendentes – e depois checa se houve “match” entre eles. O “match” acontece quando há uma criança com todas as características que os pais buscam.


### Quer um exemplo?

Segundo o sistema do [CNA](http://www.cnj.jus.br/cnanovo/pages/publico/index.jsf) – em consulta feita no dia 10 de agosto de 2019 – havia 42.546 pretendentes no Brasil. Entre eles, 15.694 aceitavam adotar uma criança que tivesse irmãos. Isto indica que aproximadamente 37% dos pretendentes aceitam adotar crianças com irmãos.

Quando o simulador gera um novo pretendente, ele faz uma espécie de cara ou coroa para decidir se este pretendente aceita crianças com irmãos. Porém, diferente de uma moeda normal, em que há 50% de chance de acontecer uma coisa ou outra, esta moeda tem 37% de chance de cair em uma das faces. Se ela cair deste lado, este pretendente aceita adotar irmãos.

Agora imagine que fizemos 100 arremessos desta moeda. O número de vezes em que ela caiu com a face do “aceita adotar crianças com irmãos” tende a ser 37. Isso significa que ele deve ficar próximo a 37, mas pode ser 40 ou 35, por exemplo.

De forma similar a este arremesso de moeda, o simulador define todas as outras características que este pretendente vai aceitar: idade máxima, sexo, cor/raça, presença de irmãos e existência de deficiências ou doenças.


### E as crianças disponíveis para adoção?

Assim como no caso dos pretendentes, cada criança da simulação é criada com base em probabilidades reais. Para isso, utilizamos dados do CNA.

A única exceção é a idade das crianças e adolescentes, que é gerada com [números do IBGE](https://www.ibge.gov.br/estatisticas/sociais/populacao/9109-projecao-da-populacao.html?=&t=resultados) (uma previsão para 2018 com base no último Censo). Desta forma, evitamos um viés estatístico que exageraria o resultado da simulação.

É importante ressaltar que o “match” entre possíveis pais e crianças para adoção é um modelo simplificado da realidade. Sendo assim, ele desconsidera limites geográficos (como pretendentes que moram em outro estado) e desistências no processo de adoção. Além disso, considera apenas a existência de deficiências físicas e cognitivas (desconsidera HIV, por ter baixa prevalência entre as crianças disponíveis e também a categoria “outro tipo de doença detectada”, por ser muito abrangente).


### Como foi calculado o tempo da simulação?

Por dia, 4 possíveis pais precisam ter suas preferências de adoção checadas em relação às crianças para adoção neste abrigo fictício. Assim, o percentual de crianças adotadas (a quantidade que deu “match”) seria condizente com a realidade brasileira.

Vamos aos números. No dia da coleta de dados, existiam 4.940 crianças disponíveis para adoção no País. Tomando por base os anos de 2016 a 2018, a média de crianças adotadas por ano é de 2.014 crianças. Ou seja, são adotadas 6 crianças por dia.

Executando a simulação até atingir um número de 100.000 crianças adotadas, descobrimos que, em geral, uma criança é adotada a cada 31 possíveis pais. Portanto, no Brasil devem existir 62.230 pretendentes ao longo de um ano.

Como criamos uma simulação que reduz estes números para um abrigo com capacidade para 100 crianças, precisamos fazer uma regra de três: 4.940 crianças no Brasil equivalem a 100%, assim como 100 crianças na simulação equivalem a 2%.

Se aplicarmos esta proporção ao número de pretendentes (62.230), teremos 1.260. Esta é a quantidade de possíveis pais que buscam crianças para adoção neste abrigo fictício, em um ano. Ao dividir pela quantidade de dias em um ano, chegamos aos 4 pretendentes por dia.


## Como usar?

`…`
