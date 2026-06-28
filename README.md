# Análise de Sinistros nas Rodovias Federais do Brasil

Este projeto tem como objetivo analisar sinistros de trânsito nas rodovias federais do país, buscando identificar fatores associados a ocorrências graves ou fatais. A proposta combina dados públicos da Polícia Rodoviária Federal com informações externas sobre veículos, como valor médio de mercado pela Tabela FIPE e avaliações de segurança veicular do Latin NCAP.

A ideia central é investigar se características do acidente, do local, dos envolvidos e dos veículos podem estar relacionadas à gravidade dos sinistros.

## Equipe:

- Andre Luis Soares Ferreira;
- Helena Couto dos Santos;
- Juliana Fernandes Barreto;
- Mariana Esthefany Xavier dos Santos.

## Objetivo

O objetivo principal do projeto é analisar quais fatores estão mais associados à gravidade dos sinistros de trânsito nas rodovias federais do Brasil.

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

Veículos com melhores características de segurança e maior valor médio de mercado estão associados a uma menor gravidade entre os ocupantes envolvidos em sinistros nas rodovias federais do Brasil?

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

## Conjunto de Dados

A base final utilizada neste projeto é uma versão enriquecida dos dados de sinistros da Polícia Rodoviária Federal. Além das informações originais sobre local, data, horário, tipo de acidente, causa, condições da via, veículos e envolvidos, a base inclui variáveis adicionais obtidas pelo cruzamento com fontes externas, como estimativa de valor de mercado pela Tabela FIPE e avaliações de segurança veicular do Latin NCAP. Dessa forma, é possível investigar possíveis relações entre as características dos veículos e a gravidade dos acidentes registrados.

## Dicionário de Dados

| Coluna | Descrição | Exemplo |
|---|---|---|
| `ano_base` | Ano de referência do registro dos dados | `2010` |
| `arquivo_origem_enriquecido` | Caminho relativo do arquivo de origem processado e enriquecido | `prf_analise/data/processed/`<br>`multiyear/final_by_year/2010/`<br>`acidentes_enriquecido.csv` |
| `id` | Identificador único do sinistro/acidente | `636034` |
| `pesid` | Identificador único da pessoa envolvida no sinistro | `1906759` |
| `data_inversa` | Data da ocorrência do sinistro (formato DD/MM/AAAA) | `01/01/2010` |
| `dia_semana` | Dia da semana em que o sinistro ocorreu | `Sexta` |
| `horario` | Horário exato em que o sinistro foi registrado | `03:00:00` |
| `uf` | Unidade da Federação onde ocorreu o sinistro | `SC` |
| `br` | Número da rodovia federal (BR) onde ocorreu o sinistro | `282` |
| `km` | Quilômetro da rodovia onde ocorreu o ponto de impacto | `1.5` |
| `municipio` | Nome do município onde o sinistro foi registrado | `FLORIANOPOLIS` |
| `causa_acidente` | Principal fator ou causa presumível do sinistro | `Falta de atenção` |
| `tipo_acidente` | Classificação da dinâmica ou tipo de impacto do sinistro | `Colisão lateral` |
| `classificacao_acidente` | Gravidade do sinistro com base no estado das vítimas | `Com Vítimas Feridas` |
| `fase_dia` | Condição de iluminação natural no momento do sinistro | `Plena noite` |
| `sentido_via` | Orientação do fluxo da via onde ocorreu o fato | `Crescente` |
| `condicao_meteorologica` | Condição climática no momento do sinistro | `Ceu Claro` |
| `tipo_pista` | Tipo de pista de rolamento da rodovia | `Dupla` |
| `tracado_via` | Geometria ou traçado da via no local do sinistro | `Reta` |
| `uso_solo` | Classificação da área como urbana ou rural | `Urbano` |
| `id_veiculo` | Identificador único do veículo envolvido | `1118603` |
| `tipo_veiculo` | Categoria ou tipo do veículo envolvido | `Automóvel` |
| `marca` | Marca e modelo do veículo envolvido | `GM/CLASSIC LIFE` |
| `ano_fabricacao_veiculo` | Ano de fabricação do veículo envolvido | `2009` |
| `tipo_envolvido` | Papel ou função da pessoa no sinistro | `Condutor` |
| `estado_fisico` | Condição física ou estado de saúde da pessoa após o sinistro | `Ferido Leve` |
| `idade` | Idade da pessoa envolvida em anos | `23` |
| `sexo` | Gênero biológico ou registro de sexo da pessoa | `Masculino` |
| `nacionalidade` | País de origem ou nacionalidade da pessoa envolvida | `Brasil` |
| `naturalidade` | Cidade de nascimento da pessoa envolvida | `Florianopolis` |
| `marca_normalizada` | Marca do veículo padronizada após a limpeza do texto original da PRF | `VOLKSWAGEN` |
| `modelo_normalizado` | Modelo do veículo padronizado após a limpeza do texto original da PRF | `GOL` |
| `familia_modelo` | Agrupamento do veículo em sua família comercial correspondente | `VOLKSWAGEN/GOL` |
| `confianca_familia` | Nível de certeza do algoritmo no agrupamento da família | `Alta ou 0.95` |
| `metodo_familia` | Biblioteca utilizada para realizar a manipulação e o mapeamento dos dados | `Pandas` |
| `observacao_familia` | Notas adicionais sobre exceções ou detalhes do mapeamento da família | `Nenhuma` |
| `status_latin_ncap` | Indica o cruzamento com a base de dados do Latin NCAP | `Localizado` |
| `confianca_latin_ncap` | Grau de certeza do algoritmo na correspondência com a base do Latin NCAP | `Alta` |
| `latin_ncap_protocolo` | Ano das regras e critérios de avaliação do teste de colisão aplicado | `2020` |
| `latin_ncap_ano_teste` | Ano em que o teste de colisão foi feito | `2019` |
| `latin_ncap_distancia_ano` | Intervalo em anos entre a fabricação do veículo e a realização do teste | `3` |
| `latin_ncap_quantidade_testes_compativeis` | Número de testes de segurança encontrados na base para o mesmo modelo | `2` |
| `latin_ncap_airbags_min` | Quantidade mínima de airbags na versão testada do modelo | `2` |
| `latin_ncap_airbags_max` | Quantidade máxima de airbags nas versões do modelo avaliado | `4` |
| `latin_ncap_estrelas_min` | Pontuação mínima obtida pelo modelo na avaliação dos testes de segurança | `1` |
| `latin_ncap_estrelas_max` | Pontuação máxima obtida pelo modelo na avaliação dos testes de segurança | `3` |
| `latin_ncap_estrelas_adulto_min` | Menor quantidade de estrelas que o modelo do veículo ganhou na proteção para adultos | `2` |
| `latin_ncap_estrelas_adulto_max` | Maior quantidade de estrelas que o modelo do veículo ganhou na proteção para adultos | `3` |
| `latin_ncap_estrelas_crianca_min` | Menor quantidade de estrelas que o modelo do veículo ganhou na proteção para crianças | `1` |
| `latin_ncap_estrelas_crianca_max` | Maior quantidade de estrelas que o modelo do veículo ganhou na proteção para crianças | `4` |
| `latin_ncap_score_adulto_min` | Pontuação mínima numérica que o veículo recebeu para a segurança de adultos | `19.10` |
| `latin_ncap_score_adulto_max` | Pontuação máxima numérica que o veículo recebeu para a segurança de adultos | `28.35` |
| `latin_ncap_score_crianca_min` | Pontuação mínima numérica que o veículo recebeu para a segurança de crianças | `18.50` |
| `latin_ncap_score_crianca_max` | Pontuação máxima numérica que o veículo recebeu para a segurança de crianças | `32.15` |
| `latin_ncap_percentual_adulto_min` | Porcentagem mínima de proteção que o veículo recebeu para adultos | `20%` |
| `latin_ncap_percentual_adulto_max` | Porcentagem máxima de proteção que o veículo recebeu para adultos | `69%` |
| `latin_ncap_percentual_crianca_min` | Porcentagem mínima de proteção que o veículo recebeu para crianças | `35%` |
| `latin_ncap_percentual_crianca_max` | Porcentagem máxima de proteção que o veículo recebeu para crianças | `75%` |
| `latin_ncap_urls` | Link das páginas dos relatórios do Latin NCAP | `https://www.latinncap.com/po/resultados`|
| `observacao_latin_ncap` | Notas de texto livre sobre exceções ou detalhes do vínculo com o Latin NCAP | `Nenhuma` |
| `status_fipe` | Indica se o veículo foi encontrado na tabela FIPE | `Encontrado` |
| `confianca_fipe` | Grau de certeza do algoritmo na associação com o código da Tabela FIPE | `Média` |
| `fipe_categoria` | Categoria comercial de classificação do veículo segundo a FIPE | `Carros e Utilitários Pequenos` |
| `fipe_score_match` | Índice numérico de similaridade textual obtido no cruzamento do nome do veículo | `0.92` |
| `fipe_margem_segundo_candidato` | Diferença numérica entre a nota de similaridade do melhor candidato encontrado na FIPE e o segundo colocado | `0.15` |
| `fipe_quantidade_candidatos_plausiveis` | Quantidade de variações de modelos da FIPE compatíveis com a busca | `3` |
| `fipe_marca_sugerida` | Marca retornada pela FIPE | `CHEVROLET` |
| `fipe_modelo_sugerido` | Modelo retornado pela FIPE | `GOL 1.0 TOTAL FLEX 8V 4P` |
| `fipe_ano_modelo_sugerido` | O ano do modelo do carro segundo a FIPE | `2012` |
| `fipe_combustivel_sugerido` | Tipo de combustível do modelo segundo a FIPE | `Gasolina` |
| `fipe_codigo_sugerido` | Código identificador de 7 dígitos do carro na tabela FIPE | `004331-1` |
| `fipe_valor_sugerido` | Preço médio estimado do carro | `Entre R$ 25.000 e R$ 35.000` |
| `fipe_valor_min` | Preço mínimo estimado para o veículo dentro das variações encontradas na FIPE | `R$ 25.000` |
| `fipe_valor_max` | Preço máximo estimado para o veículo dentro das variações encontradas na FIPE | `R$ 35.000` |
| `fipe_valor_mediano` | Valor mediano calculado a partir dos preços de mercado encontrados para o modelo | `R$ 30.000` |
| `fipe_referencia` | Mês e ano da versão da Tabela FIPE utilizada como parâmetro oficial para a consulta | `Junho de 2026` |
| `fipe_metodo_match` | Função ou método computacional empregado para realizar o cruzamento com a FIPE | `Merge do Pandas` |
| `fipe_fonte` | Fonte de extração dos dados de valor de mercado | `Tabela FIPE` |
| `observacao_fipe` | Notas de texto livre sobre exceções ou detalhes do vínculo com a FIPE | `Modelo mapeado por similaridade de ano` |
| `ilesos` | Indicador binário se a pessoa envolvida ficou ilesa (sem ferimentos) | `0` ou `1` |
| `feridos_leves` | Indicador binário se a pessoa sofreu ferimentos leves | `0` ou `1` |
| `feridos_graves` | Indicador binário se a pessoa sofreu ferimentos graves | `0` ou `1` |
| `mortos` | Indicador binário se a pessoa foi a óbito em decorrência do sinistro | `0` ou `1` |
| `latitude` | Coordenada geográfica (latitude) do local do sinistro | `-25,8529` |
| `longitude` | Coordenada geográfica (longitude) do local do sinistro | `-49,0007` |
| `regional` | Superintendência Regional da PRF responsável pelo trecho onde ocorreu o sinistro | `SPRF-PR` |
| `delegacia` | Delegacia da PRF responsável pela área do sinistro | `DEL01-PR` |
| `uop` | Unidade Operacional da PRF responsável pelo trecho | `UOP04-DEL01-PR` |

## Disponibilização dos Dados

- *Link de Acesso aos Dados:* [Acesse a pasta do Google Drive aqui](https://drive.google.com/file/d/1hm489_DjbC63kHTPpaCd0gST-enV_Yjh/view?usp=sharing)

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

## Preparação da base final enriquecida

A base final é construída em etapas para manter rastreabilidade entre os dados originais da PRF e os campos adicionados por FIPE e Latin NCAP.

### 1. Coleta dos dados da PRF

O processo começa com a coleta dos arquivos públicos da Polícia Rodoviária Federal. São utilizados os dados de acidentes agrupados por ocorrência e por pessoa/veículo, pois eles reúnem informações do local, data, tipo de acidente, causa, condições da via, veículos envolvidos e estado físico dos participantes.

### 2. Consolidação inicial da base

Depois da coleta, os arquivos são consolidados para reunir registros de ocorrências, pessoas e veículos em uma estrutura única de análise. Essa etapa organiza as informações de origem e prepara a base para as etapas seguintes de normalização e enriquecimento.

### 3. Normalização de marca e modelo

Em seguida, o campo textual de marca/modelo informado pela PRF é padronizado. A normalização reduz abreviações, prefixos e variações de versão para aproximar veículos de uma mesma família de modelo, como Volkswagen/Gol, Toyota/Hilux ou Chevrolet/Onix. Essa etapa torna possível comparar os registros da PRF com as bases externas, mesmo quando o texto original não segue um padrão único.

### 4. Enriquecimento com FIPE

Com as famílias de modelo identificadas, os veículos são comparados com a base FIPE. O objetivo é obter uma estimativa de valor médio de mercado por marca, modelo e ano, registrando também níveis de confiança ou faixas de preço quando há mais de uma versão plausível. Esses valores são usados como variáveis de análise, não como preço exato de cada veículo envolvido.

### 5. Enriquecimento com Latin NCAP

Após o enriquecimento com FIPE, a base é cruzada com os resultados do Latin NCAP. A associação considera a família do modelo e a proximidade do ano de fabricação com o ano do teste disponível. Quando há correspondência, são adicionados campos relacionados a estrelas, protocolo do teste, airbags e confiança do pareamento.

### 6. Geração da base final enriquecida

Ao final do pipeline, as informações originais da PRF, a família de modelo, os campos FIPE e os campos Latin NCAP são reunidos em uma única base enriquecida. Essa base final preserva os identificadores e variáveis do acidente, permitindo relacionar características do sinistro, do local, dos envolvidos e dos veículos com a gravidade das ocorrências analisadas.
