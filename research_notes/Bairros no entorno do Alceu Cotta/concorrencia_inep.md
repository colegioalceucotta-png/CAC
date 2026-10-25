# Concorrência privada no entorno do Colégio Alceu Cotta (dados INEP / Censo Escolar)

Data da pesquisa: 2026-10-25. Escola de referência: Colégio Alceu Cotta – Unidade Jardim Atlântico, Av. Portugal 535, Jardim Atlântico, Belo Horizonte/MG (código INEP 31380342).

Arquivos de apoio salvos na mesma pasta (extraídos dos microdados INEP, filtrados para escolas privadas ativas de Belo Horizonte nos bairros-alvo):
- `inep_privadas_bairros_alvo_2024.csv` (Censo 2024, 90 escolas, com endereço/bairro/CEP, etapas e matrículas por etapa)
- `inep_privadas_bairros_alvo_2025.csv` (Censo 2025, 87 escolas; endereço herdado do Censo 2024 pelo código INEP — ver lacuna)
- `inep_privadas_geocod_osm_2024.csv` (174 escolas privadas ativas dos CEPs da Pampulha/Venda Nova/Norte geocodificadas via OSM Nominatim, com distância haversine)

---

## Pergunta 1 — Quais produtos INEP fornecem os dados e o que foi possível obter

### Takeaway
Os microdados do Censo Escolar (2024 e 2025) foram baixados integralmente do servidor do INEP e processados; eles trazem código, nome, dependência administrativa, etapas e matrículas por etapa por escola, mas não trazem latitude/longitude. O Catálogo de Escolas (que tem coordenadas) está atrás de um painel Oracle Analytics só operável em navegador com JavaScript e não pôde ser exportado; as coordenadas foram substituídas por geocodificação aproximada (nível de rua) via OpenStreetMap/Nominatim.

### Cited Findings
- O INEP publica os microdados do Censo Escolar por ano na página oficial; os links para 2024 e 2025 são, respectivamente, `microdados_censo_escolar_2024.zip` e `microdados_censo_escolar_2025_.zip` (com sublinhado final), e a página marca o arquivo 2025 como "Documento atualizado em julho/2026" (última atualização da página: 31/07/2026) — [INEP – Microdados Censo Escolar](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados/censo-escolar)
- Download efetuado nesta pesquisa: `https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2024.zip` (33,8 MB; Last-Modified 08/07/2026; pasta interna `microdados_censo_escolar_2024_defeso`; arquivo `dados/microdados_ed_basica_2024.csv`, 217,9 MB, uma linha por escola, 1 coluna de endereço `DS_ENDERECO`, `NU_ENDERECO`, `NO_BAIRRO`, `CO_CEP`, flags `IN_INF/IN_FUND_AI/IN_FUND_AF/IN_MED` e contagens `QT_MAT_BAS/INF/FUND_AI/FUND_AF/MED`, `QT_DOC_BAS`). O cabeçalho não contém `NU_LATITUDE`/`NU_LONGITUDE` — verificação direta no arquivo baixado — [INEP download 2024](https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2024.zip)
- Download efetuado: `https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2025_.zip` (537,2 MB; pasta `microdados_censo_escolar_2025_v2`; Leia-me datado "Julho de 2026"). A estrutura mudou: há tabelas separadas `Tabela_Escola_2025_V2.csv` (290 colunas, sem colunas de endereço/bairro/CEP), `Tabela_Matricula_2025_V2.csv` (263 colunas, com `QT_MAT_BAS`, `QT_MAT_INF`, `QT_MAT_INF_CRE/PRE`, `QT_MAT_FUND_AI/AF`, `QT_MAT_MED` por escola, 178.767 linhas), `Tabela_Docente_2025_V2.csv` (`QT_DOC_BAS`), `Tabela_Turma_2025_V2.csv` (`QT_TUR_BAS`), além de Gestor e Curso Técnico. O Leia-me descreve a `Tabela_Escola_2025` como "a relação dos estabelecimentos de Educação Básica que participaram" do Censo — verificação direta no arquivo baixado — [INEP download 2025](https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2025_.zip)
- O Catálogo de Escolas é um serviço InepData lançado em 2019 com dados de endereço, telefone e oferta educacional de >226 mil escolas, com filtros por UF/município, etapa, porte, categoria e dependência administrativa; a página oficial diz que os dados "podem ser exportados" mas não oferece link direto de CSV; o acesso é por painel em `anonymousdata.inep.gov.br/analytics/saw.dll?Portal&PortalPath=/shared/Censo da Educação Básica/_portal/Catálogo de Escolas` — [INEP – Catálogo de Escolas](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/inep-data/catalogo-de-escolas)
- O painel do Catálogo retornou apenas um esqueleto HTML de 3,8 KB com a mensagem "To use Oracle Analytics, please enable javascript in your browser"; nenhuma rota de exportação CSV foi descoberta sem navegador — verificação direta (curl) nesta pesquisa — [Portal Catálogo de Escolas](https://anonymousdata.inep.gov.br/analytics/saw.dll?Portal&PortalPath=%2Fshared%2FCenso%20da%20Educa%C3%A7%C3%A3o%20B%C3%A1sica%2F_portal%2FCat%C3%A1logo%20de%20Escolas)
- O QEdu publica página por escola com dados do Censo Escolar 2025 (código INEP, endereço, matrículas, docentes, infraestrutura), mas bloqueia buscas automatizadas (HTTP 403 para fetch genérico; HTTP 404 para códigos sem "slug" de nome na URL) — [QEdu – Alceu Cotta](https://qedu.org.br/escola/31380342-colegio-alceu-cotta-unidade-jardim-atlantico)
- O diretório escolas.com.br lista escolas por bairro com o código INEP no fim da URL (ex.: Jardim Atlântico: 4 escolas, todas particulares) e cita "Dados do Censo Escolar 2025", mas sem matrículas — [escolas.com.br – Jardim Atlântico](https://escolas.com.br/brasil/mg/belo-horizonte/jardim-atlantico)
- A Base dos Dados (BigQuery público `basedosdados`) não pôde ser consultada: a CLI `bq` retornou "Invalid Credentials" (sem projeto GCP autenticado) — verificação direta nesta pesquisa.

### Inferences
- Para fins de contagem de concorrentes, matrículas e etapas, os microdados são a fonte primária e completa (INEP, oficial); o Catálogo seria necessário apenas para coordenadas oficiais.
- A ausência de endereço na `Tabela_Escola_2025` obriga a herdar o endereço do Censo 2024 pelo código INEP; escolas que só aparecem em 2025 ficam sem bairro.

### Gaps
- Coordenadas oficiais INEP (Catálogo de Escolas) não foram obtidas; usou-se geocodificação OSM/Nominatim de nível de rua (ver Pergunta 3).
- Não foi encontrado espelho público (Hugging Face/Kaggle/dados.gov.br) do CSV do Catálogo com lat/long.

---

## Pergunta 2 — Registro INEP do Colégio Alceu Cotta

### Takeaway
Código INEP 31380342, escola privada particular, urbana, ativa; em 2024 tinha 446 matrículas (sem Educação Infantil declarada) e em 2025 passou a 590 matrículas, incluindo 15 na pré-escola, 162 nos anos iniciais, 238 nos anos finais e 175 no Ensino Médio, com 45 docentes.

### Cited Findings
- Censo Escolar 2024 (microdados, linha CO_ENTIDADE=31380342): nome "COLEGIO ALCEU COTTA - UNIDADE JARDIM ATLANTICO"; endereço AV. PORTUGAL 535, CASA, bairro JARDIM ATLANTICO, CEP 31550-000, tel. (31) 3221-2108; TP_DEPENDENCIA=4 (privada), TP_CATEGORIA_ESCOLA_PRIVADA=1 (particular), TP_SITUACAO_FUNCIONAMENTO=1 (em atividade), TP_LOCALIZACAO=1 (urbana); IN_INF=0, IN_FUND_AI=1, IN_FUND_AF=1, IN_MED=1, IN_ESP=1; QT_MAT_BAS=446 (INF 0; FUND_AI 130; FUND_AF 203; MED 113; ESP 9); QT_DOC_BAS=37; QT_TUR_BAS=19; 12 salas utilizadas (10 dentro do prédio); biblioteca, lab. informática, lab. ciências, quadra, piscina e internet = sim — [INEP microdados 2024](https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2024.zip)
- Censo Escolar 2025 (microdados v2, junção Tabela_Escola/Matricula/Docente/Turma por CO_ENTIDADE=31380342): ativa, privada particular, urbana; QT_MAT_BAS=590; QT_MAT_INF=15 (creche 0; pré-escola 15); QT_MAT_FUND=400 (anos iniciais 162; anos finais 238); QT_MAT_MED=175; QT_MAT_ESP=12; QT_DOC_BAS=45; QT_TUR_BAS=25 — [INEP microdados 2025](https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2025_.zip)
- QEdu (fonte declarada "Censo Escolar 2025, Inep"): código INEP 31380342, "PORTUGAL, 535 - CASA. JARDIM ATLÂNTICO. 31550000", escola privada, urbana, "575 Matriculas, 0 Reprovações, 0 Abandonos, 45 Professores" — [QEdu](https://qedu.org.br/escola/31380342-colegio-alceu-cotta-unidade-jardim-atlantico)
- O site da escola e diretórios comerciais afirmam atendimento "da Educação Infantil ao Ensino Médio" e atuação desde 2004 — [Quero Bolsa](https://querobolsa.com.br/escolas/colegio-alceu-cotta-unidade-jardim-atlantico); [Melhor Escola](https://www.melhorescola.com.br/escola/colegio-alceu-cotta-unidade-jardim-atlantico)
- O escolas.com.br lista a escola com etapas "Educação Infantil, Ensino Fundamental, Ensino Médio" e CEP 31550-000, citando "Dados do Censo Escolar 2025" — [escolas.com.br](https://escolas.com.br/colegio-alceu-cotta-unidade-jardim-atlantico-31380342)

### Inferences
- Crescimento de 446 (2024) para 590 (2025) matrículas = +32% em um ano; o Ensino Médio cresceu de 113 para 175 (+55%) e os anos finais de 203 para 238.
- A Educação Infantil só aparece no Censo em 2025 (15 alunos de pré-escola), coerente com uma abertura recente dessa etapa; em 2024 o INEP não registrava Infantil, embora o marketing já anunciasse.
- A diferença 575 (QEdu) vs 590 (microdados v2) provavelmente decorre de versão/recorte dos dados usados pelo QEdu (ex.: versão preliminar ou exclusão de alguma categoria); não foi possível confirmar a causa.

### Gaps
- Não foi localizado o registro de uma eventual segunda unidade do Alceu Cotta nos microdados de BH (apenas "UNIDADE JARDIM ATLANTICO" consta).

---

## Pergunta 3 — Escolas privadas num raio de 2 km (com coordenadas aproximadas)

### Takeaway
Com geocodificação OSM de nível de rua, 37 escolas privadas ativas ficam a ≤2 km da coordenada de referência fornecida (-19.83165, -43.96989), somando 8.110 matrículas em 2024 e 8.111 em 2025; porém essa coordenada reverte para a Rua Campista (Santa Branca), não para a Av. Portugal, e a Av. Portugal 535 geocodifica cerca de 1,3 km ao sul, então a lista é apresentada com a distância a dois pontos-âncora e deve ser tratada como aproximada.

### Cited Findings
- Método: 174 escolas privadas ativas de BH com CEP nas faixas 3127x–3137x, 3151x–3159x, 3161x–3165x e 3170x–3174x (Censo 2024) foram geocodificadas no Nominatim (consulta "rua + número, Belo Horizonte"; fallback "rua, bairro"; depois CEP; depois bairro). Precisão obtida: 162 "rua (número não casado)", 6 "rua+número", 6 "bairro". Distância por haversine — [OSM Nominatim](https://nominatim.openstreetmap.org/) (dados © OpenStreetMap contributors, ODbL)
- Reverse geocoding da coordenada de referência (-19.83165, -43.96989): "Rua Campista, Santa Branca, Santa Mônica, Pampulha, Belo Horizonte, 31565-180" — [Nominatim reverse](https://nominatim.openstreetmap.org/reverse?format=json&lat=-19.83165&lon=-43.96989&zoom=18)
- Geocodificação de "Avenida Portugal 535, Jardim Atlântico, Belo Horizonte": o Nominatim devolve apenas segmentos da via (sem número), em Jardim Atlântico/Santa Amélia, nas posições (-19.8386, -43.9913), (-19.8433, -43.9709) e (-19.8448, -43.9716), a 2,37 km, 1,30 km e 1,47 km da referência — [Nominatim search](https://nominatim.openstreetmap.org/search?format=json&q=Avenida+Portugal+535,+Jardim+Atl%C3%A2ntico,+Belo+Horizonte)
- Tabela ≤2 km (dA = distância à âncora A fornecida na tarefa; dB = distância à âncora B = segmento OSM da Av. Portugal em Jardim Atlântico/Santa Amélia, -19.84329, -43.97091). Matrículas: Censo 2024 e Censo 2025; etapas conforme Censo 2025 (2024 quando inativa em 2025). Fonte das matrículas/etapas: microdados INEP 2024 e 2025 citados na Pergunta 1; distâncias: geocodificação OSM aproximada.

| dA km | dB km | INEP | Escola | Bairro (INEP) | Etapas 2025 | Mat. 2024 | Mat. 2025 |
|---|---|---|---|---|---|---|---|
| 0,10 | 1,40 | 31007587 | SISTEMA PIAGET DE ENSINO | Santa Branca | FundII+Médio | 200 | 199 |
| 0,17 | 1,43 | 31346535 | MASTER EDUCADORA LTDA | Santa Branca | Creche+Pré+FundI | 178 | 162 |
| 1,01 | 0,42 | 31322873 | COLEGUIUM – UNIDADE SANTA AMÉLIA | Santa Branca | Creche+Pré+FundI+FundII+Médio | 691 | 692 |
| 0,46 | 1,15 | 31007561 | COLÉGIO SANTA BRANCA (2025: REDE DECISÃO – UNIDADE SANTA BRANCA) | Santa Branca | Creche+Pré+FundI+FundII+Médio+Prof | 420 | 432 |
| 0,51 | 1,07 | 31360775 | INSTITUTO PEDAGÓGICO PIU PIU | Santa Amélia | Creche+Pré | 58 | 53 |
| 0,58 | 0,78 | 31356093 | ESCOLA INFANTIL CASINHA ENCANTADA | Santa Branca | Creche+Pré | 43 | 47 |
| 1,27 | 0,60 | 31261866 | DINÂMICA CENTRO EDUCACIONAL | Santa Amélia | Creche+Pré+FundI | 190 | 174 |
| 0,76 | 0,67 | 31282260 | CRECHE COMUNITÁRIA PEQUENO ALEXANDRE | Santa Branca | Creche | 50 | 47 |
| 0,68 | 1,02 | 31367400 | TRILHA DO SOL JARDIM DE INFÂNCIA | Itapoã | Creche+Pré | 22 | 17 |
| 0,75 | 1,07 | 31360791 | JARDIM DE INFÂNCIA MINHA VIDA | Santa Amélia | Creche+Pré | 123 | 109 |
| 0,79 | 1,20 | 31380555 | IICE CRECHE INFANTIL | Itapoã | Creche+Pré | 59 | 43 |
| 1,00 | 1,11 | 31360899 | NÚCLEO DE APRENDIZAGEM DA CRIANÇA | Itapoã | Creche+Pré | 59 | 59 |
| 1,07 | 2,03 | 31348007 | NÚCLEO EDUCACIONAL PIU PIU | Santa Mônica | Creche+Pré | 24 | 16 |
| 1,88 | 1,11 | 31333670 | COLÉGIO SANTA AMÉLIA | Jardim Atlântico | Creche+Pré+FundI+FundII | 74 | 146 |
| 1,88 | 1,11 | 31304166 | INST STA AMÉLIA | Jardim Atlântico | Creche+Pré (2024) | 23 | paralisada (status 2) |
| 1,16 | 2,17 | 31220353 | COLÉGIO HELENA BICALHO (2025: ESCOLA SESI BELO HORIZONTE SÃO JOÃO BATISTA) | São João Batista (Venda Nova) | FundI+FundII+Médio+Prof | 291 | 426 |
| 2,48 | 1,28 | 31360589 | CANGURU CENTRO DE EDUCAÇÃO INFANTIL | São Luiz | Creche+Pré | 52 | 45 |
| 1,42 | 2,24 | 31379956 | COLÉGIO ÁGAPE | Santa Mônica | Creche+Pré+FundI+FundII | 97 | 46 |
| 1,42 | 2,39 | 31308781 | CENTRO INFANTIL COMUNITÁRIO DE EDUCAÇÃO CRIARTE | Santa Mônica | Creche | 84 | 94 |
| 1,43 | 2,59 | 31340391 | INSTITUTO EDUCACIONAL MISSÃO PAZ | São João Batista (Venda Nova) | Creche+Pré+FundI+FundII+Médio+Prof | 1.308 | 1.267 |
| 2,74 | 1,49 | 31006220 | INSTITUTO EDUCACIONAL ROUXINOL – COLÉGIO NEUSA ROCHA | São Luiz | Creche+Pré+FundI+FundII | 1.100 | 1.040 |
| 1,90 | 1,50 | 31004481 | INSTITUTO ITAPOÃ | Itapoã | FundI+FundII+Médio+Prof | 265 | 274 |
| 2,56 | 1,52 | 31372633 | INSTITUTO EDUCACIONAL CRESCERE | São Luiz | Creche+Pré | 8 | 10 |
| 2,81 | 1,54 | 31377775 | COL CHROMOS PAMPULHA – UNIDADE II | São Luiz | Creche+Pré+FundI+FundII | 458 | 519 |
| 2,97 | 1,68 | 31004031 | COLÉGIO SANTA MARCELINA | São Luís | Creche+Pré+FundI+FundII+Médio+Prof | 1.680 | 1.637 |
| 1,77 | 1,68 | 31326674 | CENTRO EDUCACIONAL IZA RIZZOTTI | Itapoã | Creche+Pré | 149 | 149 |
| 3,02 | 1,75 | 31378992 | ESCOLA HUB SÃO LUIZ | São Luiz | Creche+Pré+FundI+FundII | 76 | 138 |
| 1,75 | 2,98 | 31262048 | FAMA COLÉGIO | Santa Mônica | Creche+Pré+FundI | 131 | 147 |
| 1,79 | 1,97 | 31384348 | ENCANTADOS PLANALTO | Planalto | Creche | 7 | 15 |
| 1,79 | 2,98 | 31332330 | MORIÁ SIST CRISTÃO DE ENSINO | Rio Branco | Pré+FundI | 78 | 80 |
| 1,82 | 3,12 | 31246077 | INSTITUTO EDUCACIONAL EVANGÉLICO MONTE SIÃO | São João Batista (Venda Nova) | Creche+Pré+FundI+FundII+Médio | 306 | 329 |
| 1,83 | 2,34 | 31345245 | CRECHE ARCO ÍRIS | Jardim Leblon | Creche+Pré | 216 | 215 |
| 1,85 | 2,98 | 31383732 | CENTRO EDUCACIONAL UNIKENNEDY | Rio Branco | Prof (2024) | 258 | paralisada (status 2) |
| 1,85 | 3,14 | 31246468 | COL CHROMOS VENDA NOVA | Candelária | Creche+Pré+FundI+FundII+Médio+Prof | 1.051 | 1.278 |
| 1,85 | 2,98 | 31375233 | REDE M2 – VENDA NOVA | Rio Branco | FundI+FundII+Médio | 212 | 203 |
| 2,28 | 1,91 | 31298204 | INSTITUTO EDUCACIONAL RECANTO DOS ANJOS | Jardim Atlântico | Creche+Pré+FundI | 59 | 49 |
| 1,91 | 2,27 | 31308757 | LAR ESCOLA TEREZINHA DELAMARE | Jardim Leblon | Creche+Pré | 106 | 107 |
| 1,91 | 1,96 | 31309753 | CENTRO EDUCACIONAL EFIGÊNIA TOBIAS | Planalto | FundI+FundII+Médio | 344 | 269 |
| 2,28 | 1,91 | 31376043 | ESCOLA ADVENTISTA DA PAMPULHA | Santa Amélia (Rua Carlos Sá 121) | Creche+Pré+FundI+FundII | 703 | 654 |
| 1,92 | 2,63 | 31332283 | ESPAÇO PEDAGÓGICO DA CRIANÇA LTDA | Planalto | FundI | 121 | 66 |
| 1,92 | 2,93 | 31298158 | EDUCAR C EDUC PEDAGÓGICO | Rio Branco | Pré+FundI+FundII | 86 | 119 |
| 1,92 | 3,22 | 31344591 | INSTITUTO EDUCACIONAL GIRASSOL | Candelária | Creche+Pré+FundI | 39 | 65 |
| 1,94 | 2,38 | 31351750 | INSTITUTO EDUCACIONAL COPACABANA | Copacabana | Pré+FundI | 72 | 102 |
| 1,96 | 3,21 | 31007498 | COLÉGIO FRANCISCANO CORAÇÃO DE MARIA | São João Batista (Venda Nova) | Creche+Pré+FundI+FundII+Médio | 618 | 613 |
| 1,98 | 3,23 | 31315109 | CRECHE SONHO DE CRIANÇA | São João Batista | Creche | 57 | 51 |

- Síntese: ≤2 km da âncora A: 37 escolas (8.110 matrículas em 2024; 8.111 em 2025 entre as ativas); ≤2 km da âncora B: 26 escolas; ≤2 km de pelo menos uma âncora: 45 escolas — cálculo desta pesquisa sobre os microdados INEP 2024/2025 e geocodificação OSM.
- Faixa 2–3 km da âncora A (41 escolas), maiores por matrícula 2024: Colégio Santa Marcelina (São Luís, 2,97 km, 1.680), Colégio Conclusão (Venda Nova, 2,42 km, 1.560), Colégio Santa Maria Minas – Unidade Pampulha (Planalto, 2,16 km, 1.388), Instituto Educacional Rouxinol – Colégio Neusa Rocha (São Luiz, 2,74 km, 1.100), Grau Técnico Venda Nova (2,13 km, 886), Escola Adventista da Pampulha (2,28 km, 703), Instituto Educacional Rio Branco (2,49 km, 637), Col Chromos Pampulha II (2,81 km, 458) — microdados INEP 2024 + geocodificação OSM.
- O próprio Alceu Cotta (Av. Portugal 535) ficou a 2,37 km da âncora A na geocodificação de nível de rua, evidência direta do erro do método para vias longas — cálculo desta pesquisa.

### Inferences
- Os concorrentes mais próximos e certos (≤1,5 km de ambas as âncoras, mesma quadra/bairros contíguos Santa Branca–Santa Amélia–Jardim Atlântico) são: Coleguium Santa Amélia (692 alunos, Infantil ao Médio), Colégio Santa Branca/Rede Decisão (432, Infantil ao Médio), Sistema Piaget (199, FundII+Médio), Master Educadora (162, Infantil+FundI), Dinâmica (174), Colégio Santa Amélia (146), Jardim de Infância Minha Vida (109) e várias creches pequenas.
- A Escola Adventista da Pampulha (654 alunos em 2025, Rua Carlos Sá 121, CEP 31550-200, bairro INEP "Santa Amélia", mas listada em Jardim Atlântico pelo escolas.com.br) está a cerca de 2 km de ambas as âncoras e é o maior concorrente de Fundamental do entorno imediato sem Ensino Médio.
- Pelo CEP 31550-xxx e pela listagem do escolas.com.br, Alceu Cotta, Ipê Amarelo, Recanto dos Anjos e Adventista da Pampulha compartilham o mesmo núcleo de Jardim Atlântico, logo estão a bem menos de 2 km entre si, apesar das distâncias OSM imprecisas.

### Gaps
- Coordenadas oficiais não obtidas; distâncias têm erro potencial de várias centenas de metros (até >1 km em vias longas como Av. Portugal, Av. Cristiano Guimarães, Av. Guarapari). Recomenda-se confirmar a coordenada de referência da escola (a fornecida reverte para Rua Campista/Santa Branca) antes de usar a lista por raio.
- O OSM não tem POI da escola ("Colégio Alceu Cotta" não retornou resultado no Nominatim), nem das demais escolas testadas.

---

## Pergunta 4 — Escolas privadas por bairro listado (Censo 2024 e 2025)

### Takeaway
Nos 21 bairros solicitados há 90 escolas privadas ativas no Censo 2024 (20.010 matrículas) e 87 no Censo 2025 (20.134 matrículas); Nova Pampulha, Sinimbu e Garças/Enseada das Garças não têm nenhuma escola privada registrada com esse bairro, e Bandeirantes tem apenas uma creche (ativa só em 2025).

### Cited Findings
- Critério: `CO_MUNICIPIO`=3106200, `TP_DEPENDENCIA`=4, `TP_SITUACAO_FUNCIONAMENTO`=1, campo `NO_BAIRRO` normalizado (sem acentos/caixa); grafias casadas incluem "SAO LUIZ"/"SAO LUIS", "SAO JOAO BATISTA VENDA NOVA", "LAGOINHA LEBLON (VENDA NOVA)" (agrupado em Jardim Leblon), "VISCONDE DO RIO BRANCO" (agrupado em Rio Branco). Universo BH: 814 escolas privadas ativas em 2024 (183.028 matrículas) e 819 em 2025 (172.322 matrículas) — microdados INEP [2024](https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2024.zip) e [2025](https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2025_.zip)
- Lista completa por bairro (Censo 2025; matrículas 2025 e, entre parênteses, 2024). Etapas: Cr=creche, Pré, FI=anos iniciais, FII=anos finais, Méd=Ensino Médio, Prof=profissional. Endereços do Censo 2024. Fonte: microdados INEP 2024/2025.

**Jardim Atlântico** (4 ativas em 2025; 848 mat.)
- 31380342 COLÉGIO ALCEU COTTA – UNIDADE JARDIM ATLÂNTICO — Av. Portugal 535 — Pré+FI+FII+Méd — 590 (446); Inf 15 / FI 162 / FII 238 / Méd 175; 45 docentes
- 31333670 COLÉGIO SANTA AMÉLIA — Rua Augusto Moreira 871, CEP 31555-100 — Cr+Pré+FI+FII — 146 (74); Inf 42 / FI 63 / FII 41
- 31297721 SISTEMA EDUCACIONAL IPÊ AMARELO — Av. Portugal 450, CEP 31550-000 — Pré — 63 (65)
- 31298204 INSTITUTO EDUCACIONAL RECANTO DOS ANJOS — Rua Carlos Sá 96, CEP 31550-200 — Cr+Pré+FI — 49 (59)
- 31304166 INST STA AMÉLIA — Rua Augusto Moreira 871 — Cr+Pré — 23 em 2024; paralisada em 2025

**Copacabana** (4; 589 mat.)
- 31261840 SISTEMA DE ENSINO ÉRIDA DURÃES — Rua Princesa Isabel 85 — Cr+Pré+FI+FII — 296 (259)
- 31289841 CRECHE UNIVERSO INFANTIL AMURT AMURTEL — Rua Viveiros de Castro 118 — Cr — 105 (110)
- 31351750 INSTITUTO EDUCACIONAL COPACABANA — Rua Central 504 — Pré+FI — 102 (72)
- 31350176 CENTRO PEDAGÓGICO CRISTÃO REOBOTE — Av. Francisco Negrão de Lima 230 — Cr+Pré+FI — 86 (99)

**Santa Amélia** (4; 990 mat.)
- 31376043 ESCOLA ADVENTISTA DA PAMPULHA — Rua Carlos Sá 121, CEP 31550-200 — Cr+Pré+FI+FII — 654 (703); Inf 82 / FI 359 / FII 213
- 31261866 DINÂMICA CENTRO EDUCACIONAL — Rua Levindo Ignácio Ribeiro 240 — Cr+Pré+FI — 174 (190)
- 31360791 JARDIM DE INFÂNCIA MINHA VIDA — Rua Júlio Ferreira Pinto 123 — Cr+Pré — 109 (123)
- 31360775 INSTITUTO PEDAGÓGICO PIU PIU — Av. Guarapari 1313 — Cr+Pré — 53 (58)

**Garças / Enseada das Garças** — nenhuma escola privada com esse bairro no Censo 2024 ou 2025.

**Jardim Leblon** (7; 456 mat., todas só Infantil)
- 31345245 CRECHE ARCO ÍRIS — Rua Visconde de Itaboraí 191 — Cr+Pré — 215 (216)
- 31308757 LAR ESCOLA TEREZINHA DELAMARE — Rua Wenceslau Braz 107 — Cr+Pré — 107 (106)
- 31355763 INSTITUTO EDUCACIONAL RAIO DE SOL — Rua Central 1176 — Cr — 51 (50)
- 31373427 CENTRO COMUNITÁRIO DE EDUCAÇÃO LAGOINHA — Rua São Cristóvão 48 — Cr — 51 (53)
- 31373125 ESCOLA INFANTIL PEQUENINOS DO REINO — Rua Serra dos Aimorés 286 — Cr+Pré — 16 (15)
- 31217212 INSTITUTO EDUCACIONAL SETE ANÕES — Rua Gávea 72 — Cr+Pré — 10 (5)
- 31355909 SISTEMA CRISTÃO DE ENSINO ÁGAPE — Rua Córrego Fundo 71 — Cr+Pré — 6 (13)
- 31364819 IEMA — Rua Paquetá 296 — 19 em 2024; extinta em 2025 (status 3)

**Céu Azul** (5; 419 mat.)
- 31346560 INSTITUTO PÉROLA DE ENSINO — Rua Radialista Nadir Lima 49 — Cr+Pré+FI — 100 (95)
- 31004448 INST EDUC CÉU AZUL — Rua João Gualberto dos Santos 108 — Pré+FI+FII — 98 (97)
- 31377880 INSTITUTO EDUCACIONAL SHALOM — Rua Radialista Caetano Silva 105 — Cr — 98 (96)
- 31375543 ASSOCIAÇÃO ARCO ENCANTADO — Rua Radialista Mário Marcos 49 — Cr — 98 (96)
- 31372340 ESCOLA TÉCNICA TECNOTÓRIOS — Rua Antônio José dos Santos 412 — Prof — 25 (0 na básica em 2024)

**Santa Mônica** (5; 475 mat.)
- 31360643 ESCOLA INFANTIL BATISTA BABY (2025: "BATISTA COLÉGIO S") — Rua Euclides da Cunha 37 — Cr+Pré+FI — 172 (166)
- 31262048 FAMA COLÉGIO — Rua Cândido de Figueiredo 179 — Cr+Pré+FI — 147 (131)
- 31308781 CENTRO INFANTIL COMUNITÁRIO DE EDUCAÇÃO CRIARTE — Rua Clélia 231 — Cr — 94 (84)
- 31379956 COLÉGIO ÁGAPE — Rua dos Javaés 188 — Cr+Pré+FI+FII — 46 (97)
- 31348007 NÚCLEO EDUCACIONAL PIU PIU — Rua Alzira Maria Ferreira 06 — Cr+Pré — 16 (24)

**Trevo** (2; 713 mat.)
- 31356417 CENTRO DE EDUCAÇÃO INFANTIL PROFESSORA MARIA LÚCIA HANNAS — Rua Copenhague 500, CEP 31370-240 — Cr+Pré — 665 (658); 40 docentes
- 31343102 CENTRO EDUCACIONAL PÉ DE MOLEQUE — Rua Carlos Lacerda 262 — Cr+Pré+FI — 48 (49)

**Braúnas** (2; 306 mat.)
- 31368300 COLÉGIO M2 – BH — Rua Dona Chiquita de Castro 205, CEP 31370-310 — Cr+Pré+FI+FII+Méd+Prof — 284 (425); Inf 36 / FI 124 / FII 86 / Méd 38
- 31360910 VITÓRIA RÉGIA JARDIM WALDORF — Rua Arnaldo Cathoud 685 — Cr+Pré — 22 (23)

**Santa Branca** (6; 1.579 mat.)
- 31322873 COLEGUIUM – UNIDADE SANTA AMÉLIA — Rua das Canárias 2171, CEP 31560-050 — Cr+Pré+FI+FII+Méd — 692 (691); Inf 51 / FI 223 / FII 259 / Méd 159; 58 docentes
- 31007561 COLÉGIO SANTA BRANCA (2025: REDE DECISÃO – UNIDADE SANTA BRANCA) — Rua São João da Lagoa 380, CEP 31565-170 — Cr+Pré+FI+FII+Méd+Prof — 432 (420); Inf 20 / FI 157 / FII 167 / Méd 88
- 31007587 SISTEMA PIAGET DE ENSINO — Rua do Carmelo 150, CEP 31565-260 — FII+Méd — 199 (200); FII 150 / Méd 49
- 31346535 MASTER EDUCADORA LTDA — Rua Norte 285 — Cr+Pré+FI — 162 (178)
- 31282260 CRECHE COMUNITÁRIA PEQUENO ALEXANDRE — Rua Antero de Quental 49 — Cr — 47 (50)
- 31356093 ESCOLA INFANTIL CASINHA ENCANTADA — Rua Ramalho Ortigão 1150 — Cr+Pré — 47 (43)

**Sinimbu** — nenhuma escola privada com esse bairro no Censo 2024 ou 2025.

**Rio Branco** (5; 1.130 mat.)
- 31270024 INSTITUTO EDUCACIONAL RIO BRANCO — Rua Maria Lúcia Petit 373 — Cr+Pré+FI+FII — 680 (637); Inf 135 / FI 250 / FII 295
- 31375233 REDE M2 – VENDA NOVA — Rua José Dias Vieira 46 — FI+FII+Méd — 203 (212); Méd 64
- 31298158 EDUCAR C EDUC PEDAGÓGICO — Rua Luiz Fernando 510 — Pré+FI+FII — 119 (86)
- 31332330 MORIÁ SIST CRISTÃO DE ENSINO — Rua Nacip Raydan 247 — Pré+FI — 80 (78)
- 31376167 BALÃO AMARELO — Rua Beatriz 227 — Cr — 48 (47)
- 31383732 CENTRO EDUCACIONAL UNIKENNEDY — Rua José Dias Vieira 46 — Prof — 258 em 2024; paralisada em 2025

**São João Batista (Venda Nova)** (5; 2.686 mat.)
- 31340391 INSTITUTO EDUCACIONAL MISSÃO PAZ — Rua Cyrene Crivellari Bellonia 85, CEP 31515-320 — Cr+Pré+FI+FII+Méd+Prof — 1.267 (1.308); Inf 147 / FI 503 / FII 443 / Méd 174; 63 docentes
- 31007498 COLÉGIO FRANCISCANO CORAÇÃO DE MARIA — Rua Des. Onofre Mendes Júnior 63 — Cr+Pré+FI+FII+Méd — 613 (618); Méd 89
- 31220353 COLÉGIO HELENA BICALHO (2025: ESCOLA SESI BELO HORIZONTE SÃO JOÃO BATISTA) — Rua Moacyr Fróes 83 — FI+FII+Méd+Prof — 426 (291); Méd 109
- 31246077 INSTITUTO EDUCACIONAL EVANGÉLICO MONTE SIÃO — Rua Érico Veríssimo 1826 — Cr+Pré+FI+FII+Méd — 329 (306); Méd 39
- 31315109 CRECHE SONHO DE CRIANÇA — Rua Alcides Lins 112 — Cr — 51 (57)

**Nova Pampulha** — nenhuma escola privada com esse bairro no Censo 2024 ou 2025 (duas escolas registram bairro "PAMPULHA": Coleguium – Unidade Internacional Pampulha, 31302104, CEP 31310-070, 262 mat. 2024, Infantil+Fund; e outra não detalhada).

**Candelária** (4; 1.474 mat.)
- 31246468 COL CHROMOS VENDA NOVA — Rua Ritápolis 22, CEP 31510-340 — Cr+Pré+FI+FII+Méd+Prof — 1.278 (1.051); Inf 64 / FI 258 / FII 380 / Méd 576; 69 docentes
- 31377007 INSTITUTO BETÂNIA PRIMEIROS PASSOS — Rua Padre Pedro Pinto 2435 — Cr — 87 (66)
- 31344591 INSTITUTO EDUCACIONAL GIRASSOL — Rua Buritis 46 — Cr+Pré+FI — 65 (39)
- 31364983 CENTRO INFANTIL DONA LUZIA CEDRO — Rua Pedra da Lua 200 — Cr+Pré — 44 (35)

**Piratininga** (1; 70 mat.)
- 31371220 SISTEMA DE ENSINO EVANGÉLICO CASTELO FORTE — Rua Ribeirão Preto 203 — Cr+Pré — 70 (65)

**Itapoã** (5; 542 mat.)
- 31004481 INSTITUTO ITAPOÃ — Rua São Miguel 1577, CEP 31710-350 — FI+FII+Méd+Prof — 274 (265); FI 156 / FII 89 / Méd 29
- 31326674 CENTRO EDUCACIONAL IZA RIZZOTTI — Rua Manoel Lopes Coelho 30 — Cr+Pré — 149 (149)
- 31360899 NÚCLEO DE APRENDIZAGEM DA CRIANÇA — Rua Dona Queridinha 367 — Cr+Pré — 59 (59)
- 31380555 IICE CRECHE INFANTIL — Rua São Sebastião do Paraíso 110 — Cr+Pré — 43 (59)
- 31367400 TRILHA DO SOL JARDIM DE INFÂNCIA — Rua Montese 397 — Cr+Pré — 17 (22)

**Planalto** (8; 2.099 mat.)
- 31004952 COLÉGIO SANTA MARIA MINAS – UNIDADE PAMPULHA — Rua Adelina Sales Pereira 273, CEP 31720-440 — Cr+Pré+FI+FII+Méd+Prof — 1.326 (1.388); Inf 118 / FI 418 / FII 493 / Méd 297; 78 docentes
- 31309753 CENTRO EDUCACIONAL EFIGÊNIA TOBIAS — Av. Dr. Cristiano Guimarães 755 — FI+FII+Méd — 269 (344); Méd 48
- 31351768 INSTITUTO CRISTÃO CALVÁRIO — Rua dos Salesianos 538 — Cr — 132 (137)
- 31372870 INSTITUTO EDUCACIONAL CRISTÃO SEMEAR — Rua Irmã Celeste 185 — Cr+Pré+FI — 112 (82)
- 31367109 INSTITUTO EDUCACIONAL PLANALTO — Rua José Benjamim de Castro 326 — Cr+Pré+FI — 108 (72)
- 31283606 CRECHE COMUNITÁRIO CRISTO OPERÁRIO — Rua Risoleta Pinto Sardinha 41 — Cr — 71 (71)
- 31332283 ESPAÇO PEDAGÓGICO DA CRIANÇA — Rua Hélio Baggetti 20 — FI — 66 (121)
- 31384348 ENCANTADOS PLANALTO — Rua Henrique Horta 151 — Cr — 15 (7)

**Bandeirantes** (1; 32 mat.)
- 31385590 NÚCLEO PEDAGÓGICO ARTE DE APRENDER — Rua Prof. Alberto Deodato 285, CEP 31365-340 — Cr — 32 (não ativa em 2024)

**São Luís / São Luiz** (11; 4.106 mat.)
- 31004031 COLÉGIO SANTA MARCELINA — Alameda das Falcatas 505, CEP 31275-070 — Cr+Pré+FI+FII+Méd+Prof — 1.637 (1.680); Inf 244 / FI 599 / FII 528 / Méd 266; 89 docentes
- 31006220 INSTITUTO EDUCACIONAL ROUXINOL – COLÉGIO NEUSA ROCHA — Alameda do Ipê Branco 1197 — Cr+Pré+FI+FII — 1.040 (1.100)
- 31377775 COL CHROMOS PAMPULHA – UNIDADE II — Av. Alfredo Camarati 121 — Cr+Pré+FI+FII — 519 (458)
- 31379000 VERITAS ESCOLA CRISTÃ CLÁSSICA — Rua Exp. Mário Alves de Oliveira 825 — Cr+Pré+FI — 177 (144)
- 31353582 MIGUEL ARCANJO ESCOLA WALDORF — Av. Exp. Benvindo Belém de Lima 271 — Cr+Pré+FI+FII — 163 (162)
- 31282499 CENTRO INFANTIL SÃO FRANCISCO DE ASSIS — Av. Exp. Benvindo Belém de Lima 730 — Cr+Pré — 157 (159)
- 31370266 COLÉGIO ÂNGULO MINAS — Rua Jornalista Wilson Ângelo 140 — Cr+Pré+FI+FII+Méd — 153 (141); Méd 24
- 31378992 ESCOLA HUB SÃO LUIZ — Alameda dos Jacarandás 1315 — Cr+Pré+FI+FII — 138 (76)
- 31360678 ESCOLA KIDS VILLAGE — Av. Exp. Benvindo Belém de Lima 1169 — Cr+Pré — 67 (67)
- 31360589 CANGURU CENTRO DE EDUCAÇÃO INFANTIL — Av. Santa Rosa 756 — Cr+Pré — 45 (52)
- 31372633 INSTITUTO EDUCACIONAL CRESCERE — Rua Henrique Cabral 226 — Cr+Pré — 10 (8)

**Ouro Preto** (8; 1.620 mat.)
- 31217123 COLEGUIUM – UNIDADE OURO PRETO — Rua Carlos Frederico Campos 630, CEP 31310-400 — Cr+Pré+FI+FII+Méd — 816 (827); Inf 53 / FI 190 / FII 307 / Méd 266; 70 docentes
- 31362417 COLÉGIO COPBH – UNIDADE II — Rua Sena Madureira 455 — Cr+Pré+FI+FII+Méd — 292 (253); Méd 82
- 31361089 COLÉGIO MAXIMUS UNIDADE OURO PRETO CASTELO — Rua Dep. André de Almeida 251 — Cr+Pré+FI+FII — 206 (217)
- 31351725 COLEGUIUM – UNIDADE OURO PRETO INTEGRAL — Rua Funchal 250 — Méd — 85 (81)
- 31356107 CENTRO EDUCACIONAL ALFABETO — Rua Des. Pedro Licínio 165 — Cr+Pré+FI — 63 (68)
- 31366099 INSTITUTO INFANTIL AMBJA II — Rua Arnaldo Bueno Azevedo — Cr+Pré — 57 (54)
- 31385808 BANANAS DE PIJAMA — Rua Ozório de Moraes 53 — Cr — 52 (47)
- 31355674 INSTITUTO PEDAGÓGICO EDUCANDO PARA O FUTURO (2024: PEQUENO APRENDIZ) — Rua Paschoal Carlos Magno 85 — Cr+Pré — 49 (54)
- 31308897 CRECHE OÁSIS DE ESPERANÇA — Rua Jordânia 300 — 51 em 2024; extinta em 2025

- Em 2025 há 25 escolas privadas ativas em BH sem registro em 2024 (portanto sem bairro nos microdados); as maiores são ESCOLA SESI BH CORAÇÃO EUCARÍSTICO (31388041, 325 mat.), COLÉGIO BATISTA MINEIRO – UNIDADE CASTELO II (31388220, 319), COLÉGIO MAGNUM AGOSTINIANO (31387860, 266; Inf 31 / Fund 172 / Méd 63) e COLÉGIO VERA CRUZ (31387649, 132); as demais 21 são creches/pré-escolas de 3 a 98 alunos, entre elas INSTITUTO PEDAGÓGICO PIU PIU (31389315, 31) e INSTITUTO BETÂNIA PRIMEIROS PASSOS UNIDADE II (31389650, 27), cujos nomes sugerem filiais das escolas homônimas de Santa Amélia e Candelária — microdados INEP 2025.
- A nova unidade do Colégio Magnum Agostiniano aberta em 2025 fica na Av. João Pinheiro 580, bairro Lourdes (Centro-Sul), com capacidade para 900 alunos — [Diário do Comércio](https://diariodocomercio.com.br/negocios/colegio-magnum-nova-unidade-praca-da-liberdade/); portanto não está na área de estudo.

### Inferences
- A oferta privada nos bairros-alvo é dominada por creches/pré-escolas pequenas: dos 87 estabelecimentos de 2025, 39 oferecem só Educação Infantil e apenas 20 oferecem Ensino Médio.
- Jardim Atlântico em si tem só 4 escolas privadas ativas e o Alceu Cotta concentra 70% das matrículas privadas do bairro (590 de 848) e 100% do Ensino Médio privado do bairro.

### Gaps
- Bairro é autodeclarado pela escola no Educacenso (ex.: Coleguium "Santa Amélia" está em Santa Branca; Escola Adventista "da Pampulha" está em Santa Amélia/limite com Jardim Atlântico); divergências com o bairro oficial da PBH são esperadas.
- Endereços das 25 escolas novas em 2025 não constam nos microdados; QEdu retornou 404 para consulta por código sem slug e o Catálogo não foi exportável.

---

## Pergunta 5 — Concorrentes diretos por etapa e grandes redes

### Takeaway
No raio aproximado de 2 km, os concorrentes com Ensino Médio são Coleguium Santa Amélia, Colégio Santa Branca/Rede Decisão, Sistema Piaget, Instituto Missão Paz, Chromos Venda Nova, Escola SESI São João Batista (ex-Helena Bicalho), Rede M2 Venda Nova, Monte Sião, Coração de Maria, Instituto Itapoã e Efigênia Tobias; das grandes redes citadas, só Coleguium e Chromos têm unidades nos bairros-alvo — Bernoulli, Santo Agostinho, Magnum, Pitágoras e Sagrado Coração não têm unidade na Pampulha/Venda Nova segundo o Censo 2024/2025.

### Cited Findings
- Escolas privadas ativas com Ensino Médio nos bairros-alvo (Censo 2025, matrículas de EM): Chromos Venda Nova 576; Santa Maria Minas Pampulha 297; Coleguium Ouro Preto 266; Santa Marcelina 266; Missão Paz 174; Alceu Cotta 175; Coleguium Santa Amélia 159; SESI São João Batista 109; Coração de Maria 89; Colégio Santa Branca/Rede Decisão 88; Coleguium Ouro Preto Integral 85; COPBH II 82; Rede M2 Venda Nova 64; Sistema Piaget 49; Efigênia Tobias 48; Monte Sião 39; M2 BH (Braúnas) 38; Instituto Itapoã 29; Ângulo Minas 24 — microdados INEP 2025.
- Pelo total de matrículas de EM em 2025, o Alceu Cotta (175) é a 5ª maior escola privada de Ensino Médio dos 21 bairros, atrás de Chromos Venda Nova, Santa Maria Minas Pampulha, Coleguium Ouro Preto e Santa Marcelina — cálculo sobre microdados INEP 2025.
- Escolas só de Educação Infantil (creche/pré) nos bairros-alvo em 2025: 39 estabelecimentos; a maior é o CEI Professora Maria Lúcia Hannas (Trevo, 665 alunos, 40 docentes), seguida da Creche Arco Íris (Jardim Leblon, 215), Iza Rizzotti (Itapoã, 149), Instituto Cristão Calvário (Planalto, 132), Jardim de Infância Minha Vida (Santa Amélia, 109) — microdados INEP 2025.
- Unidades de grandes redes em BH e seus bairros (Censo 2024, escolas privadas ativas): Bernoulli — Lourdes (617, só EM) e Barro Preto/Gonçalves Dias (917, FII+EM) e "Bernoulli GO" em Santo Antônio (656, Inf+FI); Santo Agostinho — Santo Agostinho (3.591) e Gutierrez (1.291); Magnum Agostiniano — Nova Floresta (1.904) e nova unidade 2025 (266, Lourdes); Pitágoras — Carlos Prates (309); Sagrado Coração de Jesus — Funcionários (703); Santo Antônio — Savassi (2.924); Loyola — Lourdes (2.292); Batista Mineiro — Colégio Batista (2.948), Buritis II/Estoril (1.641), Castelo/Paquetá (385) e Castelo II (319, 2025); Marista — São Pedro (1.910) e Padre Eustáquio (1.802). Nenhuma dessas unidades está nos 21 bairros-alvo — microdados INEP [2024](https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2024.zip) e [2025](https://download.inep.gov.br/dados_abertos/microdados_censo_escolar_2025_.zip).
- Redes com presença na Pampulha/Venda Nova (Censo 2024): Coleguium — Ouro Preto (827), Santa Amélia/Santa Branca (691), Internacional Pampulha (262), Castelo (289), Manacás/Castelo (274), Jaraguá/Santa Rosa (349), além de Ouro Preto Integral (81); Chromos — Venda Nova/Candelária (1.051), Pampulha/São José (318, só EM), Pampulha II/São Luiz (458), Castelo (120); Santa Maria Minas — Pampulha/Planalto (1.388); M2 — BH/Braúnas (425) e Venda Nova/Rio Branco (212); Maximus — Ouro Preto/Castelo (217); Santa Marcelina — São Luís (1.680) — microdados INEP 2024.
- Variação 2024→2025 de concorrentes próximos: Chromos Venda Nova +227 (1.051→1.278; EM 340→576); Helena Bicalho/SESI +135 (291→426); Colégio Santa Amélia +72 (74→146); Alceu Cotta +144 (446→590); M2 BH −141 (425→284); Efigênia Tobias −75 (344→269); Colégio Ágape −51 (97→46); Adventista da Pampulha −49 (703→654); Missão Paz −41 (1.308→1.267); Santa Maria Minas Pampulha −62 (1.388→1.326) — microdados INEP 2024/2025.

### Inferences
- A concorrência direta de Ensino Médio no entorno imediato (Santa Branca/Santa Amélia/Jardim Atlântico) se resume a Coleguium Santa Amélia (159 alunos de EM), Rede Decisão Santa Branca (88) e Sistema Piaget (49); o Alceu Cotta já tem mais alunos de EM (175) que qualquer um deles.
- Para Educação Infantil o Alceu Cotta (15 alunos de pré-escola) enfrenta oferta local densa e consolidada (Ipê Amarelo 63 e Recanto dos Anjos 49 no próprio bairro; Minha Vida 109, Piu Piu 53, Dinâmica 174 em Santa Amélia; Adventista 82).
- A rede Chromos Venda Nova (a ~2 km, 576 alunos de EM) é o principal polo de captação de Ensino Médio da região e cresceu fortemente em 2025.
- A transformação do Colégio Helena Bicalho em Escola SESI (2025) e do Colégio Santa Branca em Rede Decisão indica entrada de redes no entorno próximo entre 2024 e 2025.

### Gaps
- Nomes de redes nos microdados dependem do nome declarado (ex.: "Rede Decisão" só aparece em 2025); mantenedoras não foram verificadas.
- Não foi confirmado se as unidades "Bernoulli GO" ou outras redes abriram unidades na Pampulha em 2026 (fora do alcance do Censo 2025).

---

## Pergunta 6 — Oferta privada por bairro (escolas e matrículas): quadro de oferta

### Takeaway
A oferta privada é mais densa em São Luís (11 escolas; 4.106 matrículas), São João Batista (5; 2.686), Planalto (8; 2.099), Ouro Preto (8; 1.620), Santa Branca (6; 1.579) e Candelária (4; 1.474); Jardim Atlântico tem 4 escolas e 848 matrículas, e vários bairros (Jardim Leblon, Trevo, Piratininga, Bandeirantes, Céu Azul) têm oferta privada quase exclusivamente de Educação Infantil.

### Cited Findings
- Tabela por bairro — Censo 2025 (microdados INEP 2025; endereço/bairro do Censo 2024). Colunas: nº de escolas privadas ativas | matrículas básicas | Infantil | Anos iniciais | Anos finais | Ensino Médio | nº com EM | nº só Infantil.

| Bairro | Escolas | Mat. 2025 | Inf | FI | FII | EM | c/ EM | só Inf |
|---|---|---|---|---|---|---|---|---|
| São Luís/São Luiz | 11 | 4.106 | 916 | 1.583 | 1.317 | 290 | 2 | 4 |
| São João Batista (VN) | 5 | 2.686 | 304 | 1.045 | 926 | 411 | 4 | 1 |
| Planalto | 8 | 2.099 | 464 | 709 | 581 | 345 | 2 | 3 |
| Ouro Preto | 8 | 1.620 | 313 | 408 | 466 | 433 | 3 | 3 |
| Santa Branca | 6 | 1.579 | 179 | 528 | 576 | 296 | 3 | 2 |
| Candelária | 4 | 1.474 | 209 | 309 | 380 | 576 | 1 | 2 |
| Rio Branco | 5 | 1.130 | 207 | 425 | 434 | 64 | 1 | 1 |
| Santa Amélia | 4 | 990 | 301 | 476 | 213 | 0 | 0 | 2 |
| Jardim Atlântico | 4 | 848 | 128 | 266 | 279 | 175 | 1 | 1 |
| Trevo | 2 | 713 | 677 | 36 | 0 | 0 | 0 | 1 |
| Copacabana | 4 | 589 | 210 | 276 | 103 | 0 | 0 | 1 |
| Itapoã | 5 | 542 | 268 | 156 | 89 | 29 | 1 | 4 |
| Santa Mônica | 5 | 475 | 322 | 137 | 16 | 0 | 0 | 2 |
| Jardim Leblon | 7 | 456 | 456 | 0 | 0 | 0 | 0 | 7 |
| Céu Azul | 5 | 419 | 239 | 117 | 38 | 0 | 0 | 2 |
| Braúnas | 2 | 306 | 58 | 124 | 86 | 38 | 1 | 1 |
| Piratininga | 1 | 70 | 70 | 0 | 0 | 0 | 0 | 1 |
| Bandeirantes | 1 | 32 | 32 | 0 | 0 | 0 | 0 | 1 |
| Garças/Enseada das Garças | 0 | 0 | — | — | — | — | — | — |
| Sinimbu | 0 | 0 | — | — | — | — | — | — |
| Nova Pampulha | 0 | 0 | — | — | — | — | — | — |
| **Total** | **87** | **20.134** | **5.353** | **6.595** | **5.504** | **2.657** | **20** | **39** |

- Mesma tabela no Censo 2024 (para comparação): total 90 escolas e 20.010 matrículas; por bairro: São Luís 11/4.047; São João Batista 5/2.580; Planalto 8/2.222; Ouro Preto 9/1.652; Santa Branca 6/1.582; Rio Branco 6/1.318; Candelária 4/1.191; Santa Amélia 4/1.074; Trevo 2/707; Jardim Atlântico 5/667; Itapoã 5/554; Copacabana 4/540; Santa Mônica 5/502; Jardim Leblon 8/477; Braúnas 2/448; Céu Azul 5/384; Piratininga 1/65; Bandeirantes/Garças/Sinimbu/Nova Pampulha 0 — microdados INEP 2024.
- Contexto municipal: Belo Horizonte tinha 814 escolas privadas ativas com 183.028 matrículas básicas no Censo 2024 e 819 com 172.322 no Censo 2025 (queda de 5,8% no total privado municipal entre os dois censos, segundo os arquivos baixados) — microdados INEP 2024/2025.
- Variação de matrículas privadas 2024→2025 nos 21 bairros: +124 (+0,6%), contra −10.706 (−5,8%) no total privado de BH — cálculo sobre microdados INEP.
- Jardim Atlântico subiu de 667 para 848 matrículas privadas (+27%), puxado pelo Alceu Cotta (+144) e pelo Colégio Santa Amélia (+72) — microdados INEP 2024/2025.

### Inferences
- A soma dos 21 bairros (20.134 matrículas) equivale a 11,7% das matrículas privadas de BH em 2025, mas o Ensino Médio privado da área (2.657 alunos em 20 escolas) está concentrado em seis escolas com mais de 150 alunos de EM (Chromos VN, Santa Maria Minas Pampulha, Coleguium Ouro Preto, Santa Marcelina, Alceu Cotta, Missão Paz, Coleguium Santa Amélia).
- Bairros com oferta privada só de Infantil (Jardim Leblon, Trevo, Piratininga, Bandeirantes) e sem nenhuma oferta (Garças, Sinimbu, Nova Pampulha) são áreas de captação potencial para Fundamental/Médio, dependendo da demografia (a ser cruzada com as notas de IBGE da mesma pasta).
- A estabilidade da área (+0,6%) enquanto o total privado municipal recuou sugere que a região Pampulha/Venda Nova manteve demanda relativa; porém a queda municipal de −5,8% em um ano é incomum e pode refletir mudança metodológica da versão v2 de 2025 (ver lacuna).

### Gaps
- A queda de 183.028 para 172.322 matrículas privadas em BH entre 2024 e 2025 não foi validada contra a Sinopse Estatística oficial; pode refletir diferenças de recorte entre `microdados_ed_basica_2024` e `Tabela_Matricula_2025_V2` (ex.: tratamento de EJA/profissional/educação especial). Deve ser confirmada antes de uso.
- Não foi possível estimar demanda (população em idade escolar por bairro) a partir do INEP; isso depende das notas demográficas do IBGE produzidas em paralelo.
