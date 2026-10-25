# Mercado imobiliário — preço do m² (venda e aluguel) nos bairros do entorno do Alceu Cotta (Belo Horizonte/MG)

Data da pesquisa: 25/10/2026. Bairros pesquisados: Jardim Atlântico, Copacabana, Santa Amélia, Garças/Enseada das Garças, Jardim Leblon, Céu Azul, Santa Mônica, Trevo, Braúnas, Santa Branca, Sinimbu, Rio Branco, São João Batista, Nova Pampulha, Candelária, Piratininga, Itapoã, Planalto, Bandeirantes, São Luiz, Ouro Preto.

Convenções usadas nas tabelas:
- **ANÚNCIO** = preço pedido em anúncios (asking price); **TRANSAÇÃO** = valor declarado em escritura/ITBI quitado.
- "n" = tamanho da amostra quando conhecido. "não encontrado" = nenhuma fonte localizada.
- Cálculos próprios (a partir de dados brutos públicos) estão marcados como **[cálculo próprio]** e devem ser citados como tal, não como número oficial da fonte.

## Pergunta 1 — Quais fontes publicam preço do m² por bairro em Belo Horizonte e o que dizem sobre os 21 bairros?

### Takeaway
Nenhum índice oficial (FipeZap, Índice QuintoAndar/Imovelweb, Loft, Secovi) publica séries por bairro para esses 21 bairros; a cobertura por bairro desses índices se limita aos ~10–15 bairros mais caros (Centro-Sul/Oeste). As únicas fontes com número por bairro para todos (ou quase todos) os 21 são (a) as páginas de bairro do QuintoAndar ("média do preço do m²", anúncios, venda) e (b) os microdados de ITBI da PBH (transações), que exigem cálculo próprio.

### Cited Findings

**Cobertura das fontes (o que existe e o que não existe)**
- FipeZap (Fipe + Grupo OLX/ZAP) publica para BH o preço médio de venda e locação da cidade e um ranking dos ~10 bairros mais caros; em set/2026 o ranking de venda foi Savassi (R$ 17.281/m²), Santo Agostinho (16.643), Lourdes (16.605), Funcionários (15.171), Santa Lúcia (11.851), Sion (11.798), Santo Antônio (11.493), Serra (11.315), Gutierrez (10.913), Buritis (9.703) — nenhum bairro da Pampulha, Venda Nova ou Norte aparece — [Diário do Comércio, 2026](https://diariodocomercio.com.br/economia/preco-imoveis-bh-setembro-2026/)
- FipeZap locação (ago/2026): ranking dos 10 bairros mais caros de BH: Santo Agostinho (R$ 73,40/m²), Savassi (69,00), Belvedere (68,20), Lourdes (68,00), Funcionários (62,20), Buritis (53,10), Serra (47,60), Sion (44,70), Gutierrez (43,00), Santo Antônio (40,20); nenhum bairro do entorno do Alceu Cotta aparece — [Diário do Comércio, 16/09/2026](https://diariodocomercio.com.br/economia/aluguel-residencial-bh-sobe-agosto/)
- O relatório FipeZap em PDF (datazap.com.br) é publicado com páginas em imagem; a tentativa de extração de texto do PDF de jan/2026 não retornou tabela legível por bairro — [DataZap, FipeZap jan/2026](https://www.datazap.com.br/wp-content/uploads/2026/02/fipezap-202601-residencial-venda-.pdf)
- Índice de Aluguel QuintoAndar Imovelweb (anual 2025): média de BH R$ 43,56/m² (+13,55% em 2025); bairros citados com valor: Lourdes 79,90; Savassi 72,10; São Pedro 67,20; Anchieta 65,10; Santo Agostinho 64,80; Barro Preto 62,60; Funcionários 58,80; Santa Efigênia 52,60; Buritis 50,90; Centro 50,30. Santa Amélia (Pampulha) é citada apenas pela variação: −2,1% em 2025, sem valor em R$/m² — [Portas, 03/02/2026](https://portas.com.br/noticias/barro-preto-e-sao-pedro-lideram-valorizacao-do-aluguel-em-bh/)
- Em mar/2024 o mesmo Índice QuintoAndar Imovelweb apontou Santa Amélia entre as maiores altas de aluguel em 12 meses (+35,9%), de novo sem valor em R$/m² — [Diário do Comércio, 16/04/2024](https://diariodocomercio.com.br/economia/preco-alugueis-residenciais-belo-horizonte-ranking-bairros/)
- Loft (anúncios de venda, 127 bairros, jul–set/2026 vs jul–set/2025): preço médio anunciado em BH R$ 1,01 milhão (+8,3%); bairros do nosso recorte citados: **Piratininga (Venda Nova) R$ 410.306** (entre os mais baratos) e **Bandeirantes (Pampulha) R$ 2,74 milhões** (3º maior tíquete da cidade); a reportagem não traz R$/m² por bairro — [Diário do Comércio, 14/10/2026](https://diariodocomercio.com.br/economia/imoveis-bh-valorizacao-bairros/)
- Loft (anúncios de locação, 6,5 mil anúncios abr–jun/2025, só bairros com ≥50 anúncios): **Planalto** com tíquete médio de aluguel R$ 3.730 (+31,7% no trimestre), área média 151 m² (≈ R$ 24,7/m², cálculo da própria página de extração); média de BH R$ 4.914 (+10% a/a) — [Portas/Loft, 29/08/2025](https://portas.com.br/noticias_da_loft/serra-planalto-e-santo-antonio-lideram-alta-no-aluguel-em-belo-horizonte-em-2025/)
- QuintoAndar estudo por **regional** (publicado 27/05/2024, período de referência não informado): aluguel médio Centro-Sul R$ 2.514; Oeste 2.195; Nordeste 1.847; **Pampulha 1.840**; Leste 1.808; Noroeste 1.503; **Norte 1.392**; **Venda Nova 1.089**; área média Norte 60 m², Venda Nova 58 m² — [Diário do Comércio, 27/05/2024](https://diariodocomercio.com.br/economia/aluguel-belo-horizonte-venda-nova-regiao-centro-sul/)
- Imovelweb (relatórios mensais por regional, anos não identificados nos resultados; provavelmente 2021–2022): venda — Pampulha R$ 5.389,19/m² (outro mês: 5.310,91), Norte R$ 4.188,07 (outro mês: 4.167,46), Venda Nova R$ 4.238,17 (outro mês: 4.202,49); aluguel médio mensal — Pampulha R$ 1.727–1.745, Norte R$ 1.256–1.319, Venda Nova R$ 1.198–1.267 — [Diário do Comércio](https://diariodocomercio.com.br/?p=333893); [Guia do Investidor](https://guiadoinvestidor.com.br/?p=163199)
- IPEAD/UFMG "Pesquisa do Mercado Imobiliário de BH": os releases localizados são de 2015 a dez/2018 (aluguel por regional, a partir de anúncios de imobiliárias, médias só com ≥4 imóveis); dez/2018: apartamento Pampulha R$ 1.504,58/mês, Venda Nova R$ 785,94/mês. Nenhum release de 2025/2026 foi encontrado e o site ipead.face.ufmg.br/mercadoimobiliario/ retornou HTTP 503 em 25/10/2026 — [IPEAD, dez/2018](https://www.ipead.face.ufmg.br/mercadoimobiliario/arquivos/Release%20alugu%C3%A9is%20Dezembro%2018_%20completo%20residencial.pdf)

**QuintoAndar — páginas de bairro (ANÚNCIO, venda; acessadas em 25/10/2026)**

A página de cada bairro exibe o texto "R$ X é a média do preço do m² no bairro de …, MG" e "A partir dos imóveis anunciados pelo QuintoAndar". Não há data de referência nem metodologia detalhada; os valores mudam ao longo do tempo (ex.: snippets de busca mostraram Céu Azul a R$ 3.550/m² e Santa Amélia a R$ 5.455/m² em datas anteriores). A página "/apartamento" e "/casa" exibe a média só daquele tipo. Página de aluguel exibe o **aluguel médio mensal (tíquete, R$)**, não R$/m². URL padrão: `https://www.quintoandar.com.br/comprar/imovel/<slug>-belo-horizonte-mg-brasil` (+ `/apartamento`, `/casa`) e `https://www.quintoandar.com.br/alugar/imovel/<slug>-belo-horizonte-mg-brasil`.

| Bairro (slug) | Venda, todos os tipos (R$/m²) | Venda, apartamento (R$/m²) | Venda, casa (R$/m²) | Nº anúncios venda | Aluguel médio mensal (R$) | Nº anúncios aluguel |
|---|---|---|---|---|---|---|
| Jardim Atlântico (jardim-atlantico) | 4.450 | 6.480 | 3.802 | 1.471 | 11.000 | 149 |
| Copacabana (copacabana) | 4.300 | 4.486 | 4.242 | 890 | 3.040 | 67 |
| Santa Amélia (santa-amelia) | 5.448 | 5.935 | 5.078 | 1.297 | 3.200 | 190 |
| Garças (garcas) — "enseada-das-garcas" redireciona (301) para esta página | 4.683 | 5.416 | 4.151 | 504 | 4.942 | 49 |
| Jardim Leblon (jardim-leblon) | 3.655 | 4.486 | 3.119 | 695 | 3.040 | 90 |
| Céu Azul (ceu-azul) | 3.183 | 3.944 | 2.957 | 697 | 5.625 | 67 |
| Santa Mônica (santa-monica) | 4.938 | 5.616 | 4.413 | 1.396 | 2.510 | 84 |
| Trevo (trevo) | 4.938 | 5.416 | 3.540 | 400 | 4.942 | 73 |
| Braúnas (braunas) | 5.472 | 7.953 | 4.964 | 634 | 2.350 | 49 |
| Santa Branca (santa-branca) | 6.073 | 7.258 | 4.335 | 1.124 | 2.635 | 146 |
| Sinimbu (sinimbu) | não exibido (página sem bloco de média) | não exibido | não exibido | 610 (inclui bairros vizinhos) | não exibido | 84 |
| Rio Branco (rio-branco) | 4.279 | 5.345 | 3.704 | 861 | 2.950 | 75 |
| São João Batista (sao-joao-batista) | 4.023 | 5.000 | 3.343 | 1.229 | 2.583 | 177 |
| Nova Pampulha (nova-pampulha) | não exibido | não exibido | não exibido | 185 (página mistura bairros de Ribeirão das Neves: Justinópolis, Xangri-Lá) | não exibido | — |
| Candelária (candelaria) | 4.010 | 5.045 | 2.500 | 493 | 5.575 | 55 |
| Piratininga (piratininga) | não exibido | não exibido | não exibido | 558 | 3.400 | 27 |
| Itapoã (itapoa) | 5.867 | 6.824 | 5.000 | 1.108 | 4.163 | 129 |
| Planalto (planalto) | 4.766 | 5.800 | 4.100 | 1.202 | 2.250 | 84 |
| Bandeirantes (bandeirantes) | 6.300 | 9.248 | 5.702 | 957 | 9.500 | 21 |
| São Luiz (sao-luiz) | 6.316 | 7.008 | 5.042 | 1.579 | 5.810 | 69 |
| Ouro Preto (ouro-preto) | 6.939 | 7.273 | 5.595 | 1.067 | 3.300 | 243 |

Fonte de todas as linhas: páginas de bairro do QuintoAndar, ex.: [Céu Azul](https://www.quintoandar.com.br/comprar/imovel/ceu-azul-belo-horizonte-mg-brasil), [Jardim Atlântico](https://www.quintoandar.com.br/comprar/imovel/jardim-atlantico-belo-horizonte-mg-brasil), [Santa Amélia](https://www.quintoandar.com.br/comprar/imovel/santa-amelia-belo-horizonte-mg-brasil), [Bandeirantes](https://www.quintoandar.com.br/comprar/imovel/bandeirantes-belo-horizonte-mg-brasil), [Ouro Preto](https://www.quintoandar.com.br/comprar/imovel/ouro-preto-belo-horizonte-mg-brasil) (demais seguem o mesmo padrão de URL). O JSON embutido das páginas também expõe o "avgPrice" (preço médio anunciado de venda) de bairros vizinhos, p.ex. Céu Azul R$ 748.000; Jardim Atlântico R$ 1.600.000; Santa Amélia R$ 757.500; Copacabana R$ 620.000; Santa Mônica R$ 620.000; Santa Branca R$ 702.500; Rio Branco R$ 600.000; Jardim Leblon R$ 480.000; Itapoã R$ 950.000; Planalto R$ 765.875; Candelária R$ 630.000; São João Batista R$ 657.500; Trevo R$ 1.200.000; Braúnas R$ 1.350.000; Garças R$ 2.200.000; Bandeirantes R$ 2.975.000 — [QuintoAndar, JSON das páginas](https://www.quintoandar.com.br/comprar/imovel/santa-amelia-belo-horizonte-mg-brasil).

**Aluguel em R$/m² por bairro — [cálculo próprio] a partir dos anúncios da 1ª página de resultados do QuintoAndar (ANÚNCIO; 25/10/2026)**

Nenhuma fonte publica aluguel por m² para esses bairros. Como proxy, foram lidos os ~24 anúncios embutidos na 1ª página de aluguel de cada bairro no QuintoAndar, filtrados pelos anúncios cujo campo "neighbourhood" coincide com o bairro, e calculada a mediana de (aluguel mensal ÷ área). Amostras são pequenas (muitas vezes n ≤ 5) e devem ser lidas como ordem de grandeza. Fonte bruta: páginas `https://www.quintoandar.com.br/alugar/imovel/<slug>-belo-horizonte-mg-brasil`.

| Bairro | Aluguel apto, mediana R$/m²/mês (n) | Aluguel casa, mediana R$/m²/mês (n) | Mediana do aluguel mensal da amostra (R$) |
|---|---|---|---|
| Jardim Atlântico | 39,2 (6) | 35,4 (7) | 4.031 |
| Copacabana | 32,0 (3) | 18,2 (5) | 3.050 |
| Santa Amélia | 33,1 (14) | 32,1 (5) | 4.200 |
| Garças | — (0) | 34,2 (3) | 17.217 |
| Jardim Leblon | 29,1 (2) | 20,0 (3) | 2.550 |
| Céu Azul | 24,2 (1) | 21,0 (9) | 5.625 |
| Santa Mônica | 50,6 (5) | 29,9 (6) | 2.800 |
| Trevo | 39,1 (4) | 14,4 (6) | 7.451 |
| Braúnas | 36,1 (12) | 16,0 (5) | 1.800 |
| Santa Branca | 40,3 (9) | 22,9 (3) | 2.500 |
| Sinimbu | não encontrado (0 anúncios no bairro) | não encontrado | — |
| Rio Branco | 34,9 (4) | 13,9 (2) | 2.530 |
| São João Batista | 29,0 (9) | 12,5 (3) | 2.583 |
| Nova Pampulha | 22,0 (4; anúncios rotulados "Conjunto Habitacional Nova Pampulha", possivelmente fora de BH) | — | 990 |
| Candelária | 36,8 (3) | 40,6 (1) | 4.462 |
| Piratininga | 23,6 (1) | 19,0 (3) | 1.850 |
| Itapoã | 40,1 (19) | 19,0 (3) | 4.062 |
| Planalto | 34,4 (9) | 38,3 (4) | 1.842 |
| Bandeirantes | 44,0 (5) | 22,5 (8) | 9.000 |
| São Luiz | 32,0 (6) | 44,3 (4) | 6.210 |
| Ouro Preto | 35,2 (12) | 25,3 (12) | 3.245 |

Para comparação, a mesma leitura da 1ª página de **venda** (mediana preço ÷ área, anúncios do próprio bairro) deu, p.ex., Sinimbu R$ 4.831/m² (n=8; casas 4.831 n=6; aptos 5.239 n=2), Piratininga R$ 4.444/m² (n=9; aptos 4.621 n=7) e Nova Pampulha R$ 3.700/m² (n=1) — únicos valores de anúncio encontrados para esses três bairros — [QuintoAndar Sinimbu](https://www.quintoandar.com.br/comprar/imovel/sinimbu-belo-horizonte-mg-brasil); [QuintoAndar Piratininga](https://www.quintoandar.com.br/comprar/imovel/piratininga-belo-horizonte-mg-brasil); [QuintoAndar Nova Pampulha](https://www.quintoandar.com.br/comprar/imovel/nova-pampulha-belo-horizonte-mg-brasil)

### Inferences
- Os valores de venda do QuintoAndar por bairro (R$ 3,2 mil a 6,9 mil/m²) ficam entre 30% e 65% da média FipeZap da cidade (R$ 10.686/m²); isso reflete em parte a composição (muitas casas e lotes grandes na Pampulha/Venda Nova; o FipeZap é dominado por apartamentos nos bairros centrais) e não apenas desvalorização relativa.
- Dentro do recorte, há um gradiente claro: Ouro Preto, São Luiz, Bandeirantes, Santa Branca, Itapoã, Braúnas e Santa Amélia formam o grupo de maior valor (≥ R$ 5,4 mil/m² em anúncios; ≥ R$ 4,7 mil/m² em transações); Céu Azul, Jardim Leblon, São João Batista, Piratininga, Rio Branco e Candelária formam o grupo de menor valor (anúncios R$ 3,2–4,3 mil/m²; transações R$ 3,4–4,4 mil/m²).
- Os tíquetes médios de aluguel muito altos em Jardim Atlântico (R$ 11.000), Bandeirantes (R$ 9.500) e Garças (R$ 17.217 na amostra) são puxados por casas grandes de alto padrão em condomínio/orla da Pampulha, não pelo apartamento típico; o R$/m² de apartamento nesses bairros (R$ 32–44/m²) fica abaixo da média FipeZap da cidade (R$ 50,38/m²).
- Bairros de Venda Nova (Céu Azul, Piratininga, Rio Branco, Jardim Leblon, Copacabana, São João Batista, Candelária) apresentam aluguel de casa na faixa R$ 12–21/m², muito abaixo da média da cidade, coerente com o estudo regional do QuintoAndar que coloca Venda Nova como a regional mais barata.

### Gaps
- Nenhuma fonte publica série temporal oficial (FipeZap, Índice QuintoAndar/Imovelweb, Loft) por bairro para esses 21 bairros; os números de bairro disponíveis são "fotografias" de páginas de anúncio sem data de referência e sem metodologia publicada.
- Aluguel em R$/m² por bairro: não existe publicação; só o cálculo próprio acima (amostras pequenas).
- Sinimbu, Nova Pampulha e Piratininga: a página do QuintoAndar não exibe a "média do m²" (provavelmente por amostra insuficiente); Enseada das Garças não tem página própria (redireciona para Garças).
- Loft "dados por bairro" (loft.com.br/bairros) não foi localizado como página pública com R$/m² para esses bairros; só reportagens derivadas.
- IPEAD/UFMG: sem releases pós-2018 localizados; site indisponível (503) no dia da consulta.
- Viva Real/ZAP "preço médio do m²" por bairro e OLX: não foram testados diretamente por limite de chamadas; não há evidência nos resultados de busca de páginas com média por bairro para esses bairros.

## Pergunta 2 — A PBH publica dados de ITBI por bairro? Qual o R$/m² de transação por bairro?

### Takeaway
Sim: o conjunto "ITBI Relatórios" no CKAN da PBH traz microdados mensais de ITBI quitado com endereço, bairro, área construída adquirida, tipo construtivo, valor declarado e valor base de cálculo, atualizados até **agosto/2026**. Não há tabela pronta de R$/m² por bairro; calculei medianas por bairro (set/2025–ago/2026) a partir dos CSVs.

### Cited Findings
- O conjunto antigo "Relatório ITBI" (dados.pbh.gov.br/dataset/relatorio-itbi) cobre jan/2008–abr/2024 e está marcado como descontinuado, apontando para o substituto ckan.pbh.gov.br/dataset/itbi-relatorios — [PBH Dados Abertos](https://dados.pbh.gov.br/dataset/relatorio-itbi)
- O conjunto atual "ITBI Relatórios" tem um CSV consolidado 01/2008–05/2024 e CSVs mensais de jun/2024 a **ago/2026** (último: pda_itbi_relatorio_202608.csv), mais dicionários de dados (05/2024, 08/2024, 01/2025) — [PBH CKAN, ITBI Relatórios](https://ckan.pbh.gov.br/dataset/itbi-relatorios)
- Campos (dicionário 01/2025): Endereço; Bairro; Ano de Construção; Área Terreno Total; **Área Construída Adquirida** ("resultado da aplicação do percentual adquirido pela área de construção da unidade"); Área Adquirida (Unidades Somadas); Padrão de Acabamento (P1…); Fração Ideal Adquirida; **Tipo Construtivo Preponderante** (AP apartamento, CA casa, BA barracão, LJ loja, SL sala, LV lote vago, VR/VC vaga etc.); Descrição Tipo Ocupação (residencial/não residencial/territorial); **Valor Declarado** ("valor de aquisição declarado pelo contribuinte"); **Valor Base Cálculo** ("valor venal … em condições normais de mercado"); Zona de Uso; Data de Quitação — [PBH, dicionário de dados 01/2025](https://ckan.pbh.gov.br/dataset/0e13bf71-5355-47ce-8607-966413b08c0a/resource/2e0419d2-068b-43a7-8b3b-ad3b4f3fefd9/download/dicionario_de_dados_atualizado_2025_01.pdf)
- Volume: os 12 CSVs de set/2025 a ago/2026 somam 29.091 lançamentos de ITBI quitado em BH (≈2.000–3.000/mês) — [PBH CKAN, ITBI Relatórios](https://ckan.pbh.gov.br/dataset/itbi-relatorios) **[cálculo próprio]**
- Os nomes de bairro do cadastro PBH presentes nos CSVs para o recorte são: BANDEIRANTES, BRAUNAS, CANDELARIA, CEU AZUL, COPACABANA, GARCAS, ITAPOA, JARDIM ATLANTICO, JARDIM LEBLON, NOVA PAMPULHA, OURO PRETO, PIRATININGA, PLANALTO, RIO BRANCO, SANTA AMELIA, SANTA BRANCA, SANTA MONICA, SAO JOAO BATISTA, SAO LUIZ, TREVO. **"SINIMBU" e "ENSEADA DAS GARCAS" não aparecem** como bairro em nenhum dos 12 meses — [PBH CKAN, ITBI Relatórios](https://ckan.pbh.gov.br/dataset/itbi-relatorios) **[cálculo próprio]**

**R$/m² de TRANSAÇÃO por bairro — [cálculo próprio] sobre os CSVs de ITBI da PBH, set/2025–ago/2026 (12 meses)**

Método: filtrados lançamentos com ocupação "RESIDENCIAL" e tipo construtivo AP (apartamento) ou CA (casa), área construída adquirida > 15 m² e valor declarado > R$ 20 mil; R$/m² = Valor Declarado ÷ Área Construída Adquirida; estatística = mediana (menos sensível a outliers). "Base" = mesma conta com Valor Base de Cálculo (venal de referência da PBH). Fonte bruta: [PBH CKAN, ITBI Relatórios](https://ckan.pbh.gov.br/dataset/itbi-relatorios).

| Bairro | n (AP+CA) | Mediana R$/m² (AP+CA) | AP: n / mediana R$/m² | CA: n / mediana R$/m² | Base de cálculo: AP / CA (R$/m²) | Mediana valor declarado AP / CA (R$) | Só 2026 (jan–ago): n / mediana R$/m² |
|---|---|---|---|---|---|---|---|
| Jardim Atlântico | 15 | 4.642 | 7 / 4.642 | 8 / 5.050 | 4.840 / 5.378 | 308.000 / 1.600.000 | 5 / 4.598 |
| Copacabana | 142 | 4.576 | 92 / 4.729 | 50 / 4.323 | 5.016 / 4.545 | 350.000 / 330.000 | 97 / 4.560 |
| Santa Amélia | 414 | 5.239 | 291 / 5.208 | 123 / 5.455 | 5.251 / 5.749 | 418.515 / 675.000 | 263 / 5.076 |
| Garças | 14 | 6.010 | 0 / — | 14 / 6.010 | — / 6.623 | — / 1.460.000 | 9 / 4.002 |
| Enseada das Garças | não encontrado (bairro não consta no cadastro ITBI) | | | | | | |
| Jardim Leblon | 65 | 4.541 | 34 / 4.599 | 31 / 3.556 | 4.652 / 4.656 | 232.500 / 270.000 | 40 / 4.689 |
| Céu Azul | 64 | 3.415 | 32 / 3.572 | 32 / 2.868 | 4.083 / 3.163 | 210.000 / 320.000 | 42 / 3.662 |
| Santa Mônica | 377 | 4.297 | 297 / 4.292 | 80 / 4.475 | 4.588 / 4.704 | 315.000 / 460.500 | 270 / 4.352 |
| Trevo | 76 | 4.489 | 46 / 4.125 | 30 / 5.103 | 4.530 / 5.233 | 212.500 / 840.000 | 58 / 4.529 |
| Braúnas | 4 | 4.460 | 0 / — | 4 / 4.460 | — / 5.082 | — / 845.000 | 2 / 2.268 |
| Santa Branca | 133 | 4.752 | 102 / 4.499 | 31 / 6.228 | 4.600 / 6.236 | 317.112 / 540.000 | 95 / 4.671 |
| Sinimbu | não encontrado (bairro não consta no cadastro ITBI) | | | | | | |
| Rio Branco | 129 | 4.025 | 85 / 4.090 | 44 / 3.774 | 4.554 / 3.950 | 270.000 / 442.000 | 90 / 3.954 |
| São João Batista | 274 | 3.817 | 217 / 3.844 | 57 / 3.567 | 4.340 / 4.210 | 231.500 / 350.000 | 186 / 3.921 |
| Nova Pampulha | 1 | 2.147 | 0 / — | 1 / 2.147 | — / 2.147 | — / 350.000 | 1 / 2.147 |
| Candelária | 92 | 4.410 | 65 / 4.462 | 27 / 3.976 | 4.516 / 4.680 | 275.000 / 300.000 | 61 / 4.456 |
| Piratininga | 157 | 3.834 | 112 / 3.883 | 45 / 3.491 | 4.500 / 3.644 | 227.500 / 281.454 | 105 / 3.870 |
| Itapoã | 193 | 4.503 | 141 / 4.524 | 52 / 4.383 | 4.810 / 5.060 | 500.000 / 725.000 | 129 / 4.524 |
| Planalto | 334 | 4.836 | 255 / 4.930 | 79 / 4.448 | 4.937 / 4.880 | 360.000 / 600.000 | 220 / 4.969 |
| Bandeirantes | 108 | 5.660 | 67 / 5.884 | 41 / 4.803 | 5.884 / 5.758 | 285.000 / 1.870.000 | 77 / 5.918 |
| São Luiz | 124 | 6.250 | 98 / 6.837 | 26 / 4.742 | 7.360 / 5.942 | 587.310 / 1.508.000 | 71 / 6.018 |
| Ouro Preto | 433 | 5.385 | 397 / 5.392 | 36 / 5.277 | 5.593 / 5.513 | 480.000 / 861.450 | 309 / 6.070 |
| **BH (todos os bairros)** | **24.582** | **4.711** (média 4.953) | **21.456 / 4.824** (média 5.088) | **3.126 / 3.593** (média 4.032) | 5.056 / 4.103 | — | 16.409 / 4.797 |

### Inferences
- Para apartamentos, os bairros do recorte transacionam entre ~R$ 3,6 mil/m² (Céu Azul) e ~R$ 6,8 mil/m² (São Luiz), com a mediana da cidade em R$ 4.824/m²: Santa Amélia, Planalto, Ouro Preto, Bandeirantes e São Luiz estão acima da mediana municipal de ITBI; Céu Azul, São João Batista, Piratininga, Rio Branco, Trevo, Santa Mônica, Candelária e Santa Branca, abaixo.
- A mediana municipal de ITBI (R$ 4,8 mil/m² para AP) é menos da metade do FipeZap (R$ 10.686/m²) porque (i) a base ITBI inclui todos os segmentos (inclusive MCMV e imóveis antigos), (ii) a área é a construída adquirida (maior que a privativa usada em anúncios), (iii) valor declarado pode ser subdeclarado (o valor base de cálculo da PBH é 5–10% maior na maioria dos bairros), e (iv) o FipeZap é uma média ponderada de anúncios concentrada em bairros valorizados. Comparações devem ser feitas dentro da mesma base (ITBI vs ITBI; anúncio vs anúncio).
- Bairros com poucas transações (Jardim Atlântico 15, Garças 14, Braúnas 4, Nova Pampulha 1) têm medianas instáveis; para Jardim Atlântico, Garças e Braúnas a maior parte são casas de alto tíquete (medianas de R$ 845 mil a R$ 1,6 milhão).
- A diferença entre anúncio (QuintoAndar) e transação (ITBI) é pequena ou até invertida em vários bairros (ex.: Santa Amélia 5.448 vs 5.239; Planalto 4.766 vs 4.836; Copacabana 4.300 vs 4.576), o que sugere que a base ITBI desses bairros é dominada por apartamentos novos/MCMV com área construída próxima da privativa, enquanto o anúncio geral do QuintoAndar inclui muitas casas de m² mais barato.

### Gaps
- Sinimbu e Enseada das Garças não existem como bairro no cadastro de ITBI (provavelmente registrados sob bairros vizinhos ou outro nome cadastral); não foi possível verificar o mapeamento.
- O ITBI não distingue área privativa de área construída total e não informa se o imóvel é novo ou usado; não há coluna de regional administrativa (Pampulha/Venda Nova/Norte), então agregados por regional exigiriam tabela de correspondência bairro→regional (não feita aqui).
- Não há publicação oficial da PBH ("Estatísticas e Indicadores") com R$/m² por bairro; só os microdados.

## Pergunta 3 — Referências da cidade (venda e aluguel) no mesmo período, para posicionar cada bairro

### Takeaway
Belo Horizonte: venda R$ 10.686/m² (FipeZap, set/2026, anúncios) e aluguel R$ 50,38/m² (FipeZap, ago/2026, anúncios; yield 5,38% a.a.); em transações, Data Secovi aponta apartamentos a R$ 14.574/m² de área privativa no 1º sem/2026, e o ITBI dá mediana municipal de R$ 4.824/m² (apartamentos, área construída, set/2025–ago/2026).

### Cited Findings
- **Venda (ANÚNCIO, FipeZap, set/2026):** BH R$ 10.686/m²; +0,18% no mês; +0,19% no ano; +1,97% em 12 meses; média das 56 cidades R$ 10.015/m²; Contagem R$ 6.235/m²; Betim R$ 5.121/m² — [Diário do Comércio, out/2026](https://diariodocomercio.com.br/economia/preco-imoveis-bh-setembro-2026/)
- MySide (agregador) confirma R$ 10.686/m² em set/2026 (+2,20% em 12 meses na versão deles; BH 11ª entre 56 cidades) e cita a metodologia FipeZap (anúncios do ZAP, descarte de anúncios repetidos/irreais) — [MySide](https://myside.com.br/guia-imoveis/valor-metro-quadrado-belo-horizonte-mg)
- **Aluguel (ANÚNCIO, FipeZap Locação, ago/2026):** BH R$ 50,38/m²; +0,47% no mês; +4,91% no ano; +7,45% em 12 meses; média das 36 cidades R$ 54,47/m²; rentabilidade do aluguel em BH 0,45% ao mês / 5,38% ao ano (média nacional 6,14%) — [Diário do Comércio, 16/09/2026](https://diariodocomercio.com.br/economia/aluguel-residencial-bh-sobe-agosto/)
- Aluguel FipeZap em fev/2026: R$ 48,28/m² (+10,52% em 12 meses) — [Diário do Comércio, 17/03/2026](https://diariodocomercio.com.br/economia/belo-horizonte-alugueis-preco/)
- **Aluguel (ANÚNCIO, Índice QuintoAndar Imovelweb, ano 2025):** BH R$ 43,56/m² (+13,55% em 2025); por dormitórios: 1 dorm R$ 64,32/m², 2 dorm R$ 41,64/m², 3 dorm R$ 38,75/m² — [Portas, 03/02/2026](https://portas.com.br/noticias/barro-preto-e-sao-pedro-lideram-valorizacao-do-aluguel-em-bh/)
- **Aluguel (ANÚNCIO, Loft, 2º tri/2025):** tíquete médio anunciado em BH R$ 4.914 (+10% a/a) — [Portas/Loft, 29/08/2025](https://portas.com.br/noticias_da_loft/serra-planalto-e-santo-antonio-lideram-alta-no-aluguel-em-belo-horizonte-em-2025/)
- **Venda (ANÚNCIO, Loft, jul–set/2026):** preço médio anunciado em BH R$ 1,01 milhão (+8,3% a/a; 127 bairros, alta em 122) — [Diário do Comércio, 14/10/2026](https://diariodocomercio.com.br/economia/imoveis-bh-valorizacao-bairros/)
- **Venda (TRANSAÇÃO, Data Secovi / CMI-Secovi-MG, 1º sem/2026):** 12.099 unidades vendidas em BH (−6,7% a/a), 9.485 apartamentos; preço médio do m² privativo de apartamentos R$ 14.574 (vs R$ 14.356; +1,5%); bairros acima de R$ 21 mil/m²: Lourdes, Gutierrez, São José; abaixo de R$ 3.150/m²: Pilar, Olaria, Madre Gertrudes — [Portas, 02/09/2026](https://portas.com.br/dados-inteligencia/mercado-de-bh-vende-12-mil-imoveis-enquanto-credito-imobiliario-recua-14-em-minas/)
- **Venda (TRANSAÇÃO, Data Secovi, 1º tri/2026):** 6.672 imóveis (−9,8% a/a); valor médio residencial R$ 689,9 mil (+4% vs média 2025 de R$ 662,8 mil); m² médio de apartamentos de R$ 14,3 mil para R$ 15,2 mil (+6,3%) — [Jornal do Brás](https://jornaldobras.com.br/noticia/120986/data-secovi-aponta-a-venda-de-6-672-imoveis-em-belo-horizonte-no-primeiro-trimestre-de-2026) (página retornou 403 ao fetch direto; valores vêm do snippet de busca); [Diário do Comércio](https://diariodocomercio.com.br/?p=582213)
- **Venda (TRANSAÇÃO, ITBI PBH, set/2025–ago/2026) [cálculo próprio]:** mediana municipal R$ 4.824/m² para apartamentos (n=21.456) e R$ 3.593/m² para casas (n=3.126); com valor base de cálculo: R$ 5.056 (AP) e R$ 4.103 (CA) — [PBH CKAN, ITBI Relatórios](https://ckan.pbh.gov.br/dataset/itbi-relatorios)

### Inferences
- Posição relativa em anúncios de venda (QuintoAndar bairro ÷ FipeZap cidade R$ 10.686): Ouro Preto 65%, São Luiz 59%, Bandeirantes 59%, Santa Branca 57%, Itapoã 55%, Braúnas 51%, Santa Amélia 51%, Santa Mônica 46%, Trevo 46%, Planalto 45%, Garças 44%, Jardim Atlântico 42%, Copacabana 40%, Rio Branco 40%, São João Batista 38%, Candelária 38%, Jardim Leblon 34%, Céu Azul 30%. (Mistura de bases: QuintoAndar inclui casas; FipeZap é majoritariamente apartamentos — usar só como ordem de grandeza.)
- Posição relativa em transações (ITBI AP bairro ÷ ITBI AP cidade R$ 4.824): São Luiz 142%, Bandeirantes 122%, Ouro Preto 112%, Santa Amélia 108%, Planalto 102%, Copacabana 98%, Jardim Atlântico 96%, Jardim Leblon 95%, Itapoã 94%, Santa Branca 93%, Candelária 93%, Santa Mônica 89%, Trevo 86%, Rio Branco 85%, Piratininga 81%, São João Batista 80%, Céu Azul 74%.
- Aluguel de apartamento nos bairros do recorte (R$ 29–44/m² nas amostras do QuintoAndar) fica em geral abaixo do FipeZap da cidade (R$ 50,38/m²) e próximo da faixa "3 dormitórios" do Índice QuintoAndar Imovelweb (R$ 38,75/m²).

### Gaps
- Não foi possível obter o relatório FipeZap de locação de set/2026 (o dado mais recente é ago/2026) nem a tabela completa de bairros do PDF FipeZap (PDF em imagem).
- Data Secovi não publica R$/m² por regional ou pelos bairros do recorte; só extremos da cidade.

## Pergunta 4 — Proxies para bairros sem dado (Sinimbu, Trevo, Braúnas, Nova Pampulha, Enseada das Garças)

### Takeaway
Trevo e Braúnas têm dado direto (QuintoAndar e ITBI, embora Braúnas tenha só 4 transações); Sinimbu, Nova Pampulha e Enseada das Garças precisam de proxies: Sinimbu → Rio Branco/Santa Mônica/Trevo; Nova Pampulha → Trevo/Braúnas; Enseada das Garças → Garças (o próprio QuintoAndar redireciona).

### Cited Findings
- QuintoAndar redireciona (HTTP 301) `enseada-das-garcas-belo-horizonte-mg-brasil` para `garcas-belo-horizonte-mg-brasil` — tratando os dois como o mesmo bairro — [QuintoAndar Garças](https://www.quintoandar.com.br/comprar/imovel/garcas-belo-horizonte-mg-brasil)
- A página de Sinimbu no QuintoAndar lista 610 anúncios de venda, mas os anúncios embutidos na 1ª página estão rotulados como Sinimbu, Rio Branco e Santa Mônica (bairros vizinhos), e a página não exibe "média do m²"; os 8 anúncios rotulados "Sinimbu" têm mediana de R$ 4.831/m² (6 casas) **[cálculo próprio]** — [QuintoAndar Sinimbu](https://www.quintoandar.com.br/comprar/imovel/sinimbu-belo-horizonte-mg-brasil)
- A página de Nova Pampulha lista 185 anúncios, rotulados como Braúnas, Trevo, Pio XII, Parque Xangri-Lá, Justinópolis e "Conjunto Habitacional Nova Pampulha" (os três últimos em Ribeirão das Neves) — ou seja, a página mistura municípios e não serve de referência direta — [QuintoAndar Nova Pampulha](https://www.quintoandar.com.br/comprar/imovel/nova-pampulha-belo-horizonte-mg-brasil)
- No ITBI, Nova Pampulha teve apenas 1 transação residencial (casa, R$ 350 mil, R$ 2.147/m²) em 12 meses e Braúnas apenas 4 (casas, mediana R$ 845 mil e R$ 4.460/m²) **[cálculo próprio]** — [PBH CKAN, ITBI Relatórios](https://ckan.pbh.gov.br/dataset/itbi-relatorios)
- Proxies regionais disponíveis (todos antigos): QuintoAndar por regional (2024): aluguel Pampulha R$ 1.840, Venda Nova R$ 1.089, Norte R$ 1.392 — [Diário do Comércio, 27/05/2024](https://diariodocomercio.com.br/economia/aluguel-belo-horizonte-venda-nova-regiao-centro-sul/); Imovelweb por regional (c. 2021–22): venda Pampulha R$ 5.310–5.389/m², Venda Nova R$ 4.202–4.238/m², Norte R$ 4.167–4.188/m² — [Diário do Comércio](https://diariodocomercio.com.br/?p=333893)

### Inferences
- **Sinimbu (proxy):** vizinhos imediatos Rio Branco (anúncio R$ 4.279/m²; ITBI AP R$ 4.090/m²), Santa Mônica (anúncio R$ 4.938/m²; ITBI AP R$ 4.292/m²) e Trevo (anúncio R$ 4.938/m²; ITBI AP R$ 4.125/m²) → faixa de referência R$ 4,1–4,9 mil/m² (venda) e R$ 30–39/m² (aluguel de apartamento, amostras pequenas). Rótulo: PROXY.
- **Nova Pampulha (proxy):** vizinhos Trevo e Braúnas → venda R$ 4,9–5,5 mil/m² em anúncio (casas R$ 3,5–5,0 mil/m²); aluguel apartamento R$ 36–39/m² (amostras pequenas). Rótulo: PROXY; os anúncios "Nova Pampulha" do QuintoAndar incluem Ribeirão das Neves e não devem ser usados.
- **Enseada das Garças (proxy):** usar Garças (anúncio R$ 4.683/m², casas R$ 4.151/m²; ITBI casas R$ 6.010/m², n=14; aluguel casa ≈ R$ 34/m², n=3). Rótulo: PROXY.
- **Braúnas e Trevo:** têm dado direto de anúncio (QuintoAndar) e de transação (ITBI), mas o ITBI de Braúnas (n=4) é frágil; para Braúnas, Trevo (n=76) e Garças funcionam como complemento.

### Gaps
- Não há publicação com média por Regional administrativa (Pampulha, Venda Nova, Norte) em 2025–2026 em nenhuma das fontes consultadas; os únicos agregados regionais são de 2021–2024.
- Não foi encontrado nenhum dado (anúncio ou transação) com rótulo "Enseada das Garças".
