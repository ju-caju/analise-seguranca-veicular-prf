# Análise de Sinistros nas Rodovias Federais da Paraíba

Este projeto tem como objetivo analisar sinistros de trânsito nas rodovias federais da Paraíba, buscando identificar fatores associados a ocorrências graves ou fatais. A proposta combina dados públicos da Polícia Rodoviária Federal com informações externas sobre veículos, como valor médio de mercado pela Tabela FIPE e avaliações de segurança veicular do Latin NCAP.

A ideia central é investigar se características do acidente, do local, dos envolvidos e dos veículos podem estar relacionadas à gravidade dos sinistros.

## Equipe:

- André Luis Soares Ferreira;
- Helena Couto dos Santos;
- Juliana Fernandes Barreto;
- Mariana Esthefany Xavier dos Santos.

## Objetivo

O objetivo principal do projeto é analisar quais fatores estão mais associados à gravidade dos sinistros de trânsito nas rodovias federais da Paraíba.

Entre os pontos investigados, destacam-se:

- Local do acidente;
- BR e quilômetro;
- Data e horário da ocorrência;
- Tipo de acidente;
- Causa principal;
- Condição climática;
- Tipo de pista;
- Perfil dos envolvidos;
- Tipo, marca/modelo e ano de fabricação dos veículos;
- Valor estimado do veículo pela Tabela FIPE;
- Avaliação de segurança veicular pelo Latin NCAP.

## Problema de pesquisa

Veículos com melhores características de segurança e maior valor médio de mercado estão associados a uma menor gravidade entre os ocupantes envolvidos em sinistros nas rodovias federais da Paraíba?

## Bases de dados

### Dados Abertos da PRF

A base principal do projeto vem dos Dados Abertos da Polícia Rodoviária Federal. São utilizados dados de acidentes agrupados por ocorrência e por pessoa/veículo.

Principais informações utilizadas:

- Município;
- Unidade federativa;
- BR;
- Quilômetro;
- Data e horário;
- Tipo de acidente;
- Causa do acidente;
- Condição climática;
- Tipo de pista;
- Número de mortos;
- Número de feridos;
- Tipo de veículo;
- Marca/modelo;
- Ano de fabricação;
- Estado físico dos envolvidos.

Fonte:  
https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf

### Latin NCAP

O Latin NCAP é utilizado como fonte externa para enriquecer a base com informações de segurança veicular.

Fonte:  
https://www.latinncap.com/po/resultados

### Tabela FIPE

A Tabela FIPE é utilizada para aproximar o valor médio de mercado dos veículos envolvidos nos sinistros.

Fonte:  
https://veiculos.fipe.org.br/

## Enriquecimento dos dados

Um dos diferenciais do projeto é o enriquecimento da base original da PRF.

A base da PRF informa o modelo do veículo em formato textual, mas esse campo pode apresentar variações, abreviações e inconsistências. Por isso, o projeto realiza uma etapa de normalização para tentar identificar a família do modelo do veículo.

Exemplos:

- `VW/GOL 1.0` e `VW/GOL SPECIAL` podem ser associados à família `VOLKSWAGEN/GOL`;
- `I/TOYOTA HILUX` pode ser associado à família `TOYOTA/HILUX`;
- `GM/ONIX` pode ser associado à família `CHEVROLET/ONIX`.

Após essa normalização, os veículos são comparados com as bases externas da FIPE e do Latin NCAP.

## Possíveis análises

As análises pretendidas estão divididas em três grupos principais.

#### 1. Análise dos sinistros

#### 2. Análise dos veículos

#### 3. Análise de segurança veicular

## Preparacao da base final enriquecida

A base final e construida em etapas para manter rastreabilidade entre os dados originais da PRF e os campos adicionados por FIPE e Latin NCAP.

### 1. Coleta dos dados da PRF

O processo comeca com a coleta dos arquivos publicos da Policia Rodoviaria Federal. Sao utilizados os dados de acidentes agrupados por ocorrencia e por pessoa/veiculo, pois eles reunem informacoes do local, data, tipo de acidente, causa, condicoes da via, veiculos envolvidos e estado fisico dos participantes.

### 2. Consolidacao inicial da base

Depois da coleta, os arquivos sao consolidados para reunir registros de ocorrencias, pessoas e veiculos em uma estrutura unica de analise. Essa etapa organiza as informacoes de origem e prepara a base para as etapas seguintes de normalizacao e enriquecimento.

### 3. Normalizacao de marca e modelo

Em seguida, o campo textual de marca/modelo informado pela PRF e padronizado. A normalizacao reduz abreviacoes, prefixos e variacoes de versao para aproximar veiculos de uma mesma familia de modelo, como Volkswagen/Gol, Toyota/Hilux ou Chevrolet/Onix. Essa etapa torna possivel comparar os registros da PRF com as bases externas, mesmo quando o texto original nao segue um padrao unico.
