# Demografia IBGE (Censo 2022 e 2010) dos bairros no entorno do Colégio Alceu Cotta — Belo Horizonte/MG

Data da pesquisa: 2026-10-25. Todos os arquivos citados foram baixados e processados nesta sessão (Python 3, sem GIS; overlay geométrico feito com ponto-em-polígono em puro Python). Tabela consolidada em CSV: `demografia_ibge_tabela.csv` (mesma pasta).

Convenções: **2022** = Censo Demográfico 2022 (IBGE); **2010** = Censo 2010 (via PBH). Nível de aproximação de cada número está indicado: [camada bairro IBGE], [camada bairro PBH], [soma de setores], [estimativa].

## Pergunta 1 — O IBGE publicou o Censo 2022 por "bairro" para Belo Horizonte? Há recorte etário por bairro?

### Takeaway
Sim. O IBGE publica, dentro do produto "Censo 2022 – Agregados por Setores Censitários: Resultados do Universo", planilhas agregadas por **Bairro** (arquivos `Agregados_por_bairros_*_BR.csv`), e o arquivo `demografia` traz população por sexo e **grupos quinquenais de idade** (0–4, 5–9, 10–14, 15–19…) para cada um dos 476 bairros de Belo Horizonte (código de bairro `3106200NNN`). Não existe faixa 0–5 / 6–14 / 15–17 exata: a idade é divulgada só em grupos de 5 anos por regra de sigilo; as faixas escolares abaixo são **estimativas por interpolação**. Não encontrei tabela SIDRA com recorte por bairro.

### Cited Findings
- Diretório oficial do produto, com subpastas `Agregados_por_Bairro_csv/`, `Agregados_por_Setor_csv/`, `Agregados_por_Distrito_csv/`, `Agregados_por_SubDistrito_csv/`, `Agregados_por_Municipio_csv/`, `malha_com_atributos/` e o dicionário `dicionario_de_dados_agregados_por_setores_censitarios_20260520.xlsx` — [IBGE FTP – Agregados por Setores Censitários](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/)
- Arquivos por bairro usados (nomes exatos): `Agregados_por_bairros_basico_BR_20260520.zip` (CSV interno `Agregados_por_bairros_basico_BR.csv`, 4,8 MB, Last-Modified no servidor 20/05/2026) e `Agregados_por_bairros_demografia_BR.zip` (CSV `Agregados_por_bairros_demografia_BR.csv`, 4,0 MB, Last-Modified 12/11/2024) — [IBGE FTP – Agregados_por_Bairro_csv](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/Agregados_por_Bairro_csv/)
- Nota metodológica do produto: "Adicionalmente às informações agregadas por Setores Censitários, estão incluídas nessa divulgação planilhas com agregações nos níveis de Distritos, Subdistritos e Bairros, permitindo que sejam feitas consultas mais diretas a esses níveis territoriais". Sobre sigilo: "para os setores com menos de cinco domicílios particulares permanentes omitiram-se os valores da maioria das variáveis (...) preenchidos com 'x'" e "a variável de idade da pessoa, é apresentada em grupos quinquenais. Após este procedimento, restando células com frequências iguais a 1 ou 2, estes valores também são substituídos por 'x'" — [IBGE, Agregados por Setores Censitários – Resultados do Universo, Nota metodológica n. 06 (PDF)](https://biblioteca.ibge.gov.br/visualizacao/livros/liv102136.pdf)
- Colunas do arquivo básico por bairro: `CD_BAIRRO;NM_BAIRRO;CD_REGIAO;NM_REGIAO;CD_UF;NM_UF;CD_MUN;NM_MUN;CD_DIST;NM_DIST;CD_SUBDIST;NM_SUBDIST;CD_NU;NM_NU;CD_AGLOM;NM_AGLOM;CD_RGINT;NM_RGINT;CD_RGI;NM_RGI;CD_CONCURB;NM_CONCURB;AREA_KM2;v0001..v0009` (separador `;`, codificação Latin-1, decimal com vírgula). Dicionário: v0001 = Total de pessoas; v0002 = Total de domicílios (DPPO+DPPV+DPPUO+DPIO+DCCM+DCSM); v0003 = Total de domicílios particulares; v0004 = domicílios coletivos; v0005 = média de moradores em domicílios particulares ocupados; v0006 = % de DPO imputados; **v0007 = Total de Domicílios Particulares Ocupados (DPPO+DPIO)**; v0008 = de uso ocasional; v0009 = permanentes vagos — [Dicionário de dados IBGE (xlsx)](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/dicionario_de_dados_agregados_por_setores_censitarios_20260520.xlsx)
- Colunas do arquivo demografia por bairro: `CD_BAIRRO;NM_BAIRRO;V01006..V01041`. Dicionário (aba "Dicionário não PCT", tema Demografia, universo = moradores em domicílios particulares permanentes ocupados): V01006 = Quantidade de moradores; V01007/V01008 = sexo; V01009–V01019 = homens por idade; V01020–V01030 = mulheres por idade; **V01031 = 0 a 4 anos; V01032 = 5 a 9; V01033 = 10 a 14; V01034 = 15 a 19**; V01035 = 20–24; V01036 = 25–29; V01037 = 30–39; V01038 = 40–49; V01039 = 50–59; V01040 = 60–69; V01041 = 70+ — [Dicionário de dados IBGE (xlsx)](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/dicionario_de_dados_agregados_por_setores_censitarios_20260520.xlsx)
- Belo Horizonte (CD_MUN 3106200) tem 476 linhas (bairros) no arquivo IBGE; a soma de v0001 dos 476 bairros = 2.315.560 pessoas, igual à população total do município no Censo 2022 (2.315.560) divulgada pela imprensa — [IBGE bairros basico (processado)](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/Agregados_por_Bairro_csv/); [Itatiaia – Censo 2022 BH 2.315.560 moradores](https://www.itatiaia.com.br/brasil/sudeste/mg/censo-2022-saiba-qual-e-a-regional-mais-populosa-de-bh/)
- Definição de bairro do IBGE: "O IBGE considera como bairros apenas as divisões ou zoneamentos internos aos municípios legalmente instituídos pelo poder municipal"; no Censo 2022, 119.431.359 pessoas viviam fora de bairros — [IBGE Educa](https://educa.ibge.gov.br/jovens/materias-especiais/22550-87-da-populacao-brasileira-vivia-em-areas-urbanas.html). Metadado da "Malha de Bairros (Censo Demográfico) – 2022": setores censitários foram usados para representar os bairros, por isso alguns limites oficiais foram aproximados e a área representada pode diferir da área legal — [IBGE Metadados Geo – Malha de Bairros 2022](https://metadadosgeo.ibge.gov.br/geonetwork_ibge/srv/api/records/c0a902c4-1e02-43b3-ac7b-1318cc733da5) (página retornou HTTP 403 neste ambiente; conteúdo via trecho de busca — verificar).
- Malha de bairros com atributos (para GIS): `malha_com_atributos/bairros/gpkg/BR/` e `.../gpkg/UF/`, `.../bairros/shp/` — [IBGE FTP – malha_com_atributos/bairros](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/malha_com_atributos/bairros/)

#### Tabela A — Censo 2022 por bairro, camada de bairros do IBGE [camada bairro IBGE] (exato, sem interpolação)
Fonte: IBGE, `Agregados_por_bairros_basico_BR.csv` e `Agregados_por_bairros_demografia_BR.csv`, filtrados por `CD_MUN = 3106200`. "Subdistrito" = regional PBH à qual o IBGE vinculou o bairro (NM_SUBDIST). DPPO = v0007 (domicílios particulares ocupados). Faixas etárias = V01031–V01034 (moradores em DPPO).

| Bairro (NM_BAIRRO IBGE) | CD_BAIRRO | Subdistrito | Pop. 2022 (v0001) | Dom. part. ocupados 2022 (v0007) | Dom. total 2022 (v0002) | Vagos (v0009) | Média mor. (v0005) | 0–4 | 5–9 | 10–14 | 15–19 | 0–14 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Jardim Atlântico | 3106200272 | Pampulha | 1.316 | 448 | 544 | 61 | 2,9 | 75 | 69 | 65 | 84 | 209 |
| Copacabana | 3106200266 | Venda Nova | 14.650 | 5.293 | 6.074 | 683 | 2,7 | 777 | 830 | 869 | 886 | 2.476 |
| Santa Amélia | 3106200416 | Pampulha | 20.449 | 7.914 | 8.958 | 844 | 2,6 | 958 | 1.043 | 1.036 | 990 | 3.037 |
| Garças | 3106200268 | Pampulha | 1.228 | 363 | 457 | 49 | 3,3 | 61 | 75 | 80 | 91 | 216 |
| Jardim Leblon | 3106200477 | Venda Nova | 9.018 | 3.367 | 3.851 | 444 | 2,7 | 442 | 555 | 557 | 562 | 1.554 |
| Céu Azul | 3106200190 | Venda Nova | 22.829 | 8.259 | 9.544 | 1.142 | 2,8 | 1.136 | 1.291 | 1.332 | 1.503 | 3.759 |
| Santa Mônica | 3106200418 | Venda Nova | 21.971 | 8.277 | 9.567 | 1.045 | 2,6 | 974 | 1.125 | 1.189 | 1.161 | 3.288 |
| Trevo (ver nota Trevo) | 3106200285 | Pampulha | 9.905 | 3.344 | 3.911 | 452 | 2,9 | 664 | 810 | 709 | 752 | 2.183 |
| Braúnas | 3106200260 | Pampulha | 1.988 | 657 | 854 | 115 | 2,9 | 95 | 84 | 117 | 123 | 296 |
| Santa Branca | 3106200417 | Pampulha | 5.640 | 2.230 | 2.692 | 401 | 2,5 | 242 | 273 | 257 | 263 | 772 |
| Rio Branco | 3106200489 | Venda Nova | 11.836 | 4.324 | 4.968 | 553 | 2,7 | 482 | 602 | 645 | 774 | 1.729 |
| São João Batista | 3106200485 | Venda Nova | 17.668 | 6.885 | 8.021 | 970 | 2,6 | 777 | 902 | 896 | 1.002 | 2.575 |
| Nova Pampulha | 3106200275 | Pampulha | 309 | 108 | 121 | 13 | 2,9 | 11 | 17 | 13 | 20 | 41 |
| Candelária | 3106200469 | Venda Nova | 8.029 | 3.042 | 3.492 | 416 | 2,6 | 383 | 410 | 434 | 479 | 1.227 |
| Piratininga | 3106200488 | Venda Nova | 20.179 | 7.473 | 8.750 | 1.135 | 2,7 | 1.026 | 1.195 | 1.182 | 1.258 | 3.403 |
| Itapoã | 3106200415 | Pampulha | 9.938 | 3.918 | 4.519 | 430 | 2,5 | 375 | 407 | 482 | 482 | 1.264 |
| Planalto | 3106200450 | Norte | 18.501 | 7.082 | 8.157 | 874 | 2,6 | 792 | 866 | 827 | 941 | 2.485 |
| Bandeirantes | 3106200258 | Pampulha | 6.355 | 2.287 | 2.624 | 201 | 2,7 | 243 | 297 | 286 | 332 | 826 |
| São Luíz (grafia IBGE/PBH) | 3106200283 | Pampulha | 4.525 | 1.454 | 1.837 | 241 | 2,8 | 121 | 141 | 177 | 236 | 439 |
| Ouro Preto | 3106200277 | Pampulha | 20.580 | 7.953 | 9.438 | 930 | 2,5 | 961 | 1.066 | 961 | 1.122 | 2.988 |
| **Soma dos 20 bairros** | | | **226.914** | **84.678** | | | | | | | | **34.767** (0–14); 0–19 = 47.828 |

Vilas/anexos com código IBGE próprio, dentro do mesmo entorno (não somadas acima): Vila Copacabana 3106200369 (420 pessoas; 148 DPPO; 0–14 = 86); Vila Jardim Leblon 3106200457 (285; 104; 55); Vila Santa Mônica 1ª Seção 3106200490 (1.548; 539; 353); Vila Santa Mônica 2ª Seção 3106200491 (166; 61; 32); Vila São João Batista 3106200372 (2.270; 762; 457); Vila Piratininga A 3106200373 (265; 93; 45); Novo Ouro Preto 3106200276 (523; 177; 115). ("Vila Piratininga" 3106200298, 1.464 pessoas, fica no Barreiro — não pertence ao entorno; "Vila Bandeirantes" 3106200107 fica no Centro-Sul.)

Observação: V01006 (moradores em DPPO) difere de v0001 em São Luíz (4.500 vs 4.525) e Ouro Preto (20.526 vs 20.580) porque moradores de domicílios coletivos/improvisados não entram no arquivo demografia; nos demais bairros os dois totais coincidem.

#### Tabela B — Faixas escolares 2022 [estimativa] derivadas da Tabela A
Método: divisão uniforme dentro de cada grupo quinquenal: 0–5 = (0–4) + 1/5·(5–9); 6–10 = 4/5·(5–9) + 1/5·(10–14); 11–14 = 4/5·(10–14); 6–14 = 6–10 + 11–14; 15–17 = 3/5·(15–19); 0–17 = soma. Erro típico de alguns por cento por faixa; use como ordem de grandeza.

| Bairro | est. 0–5 | est. 6–10 | est. 11–14 | est. 6–14 | est. 15–17 | est. 0–17 |
|---|---|---|---|---|---|---|
| Jardim Atlântico | 89 | 68 | 52 | 120 | 50 | 259 |
| Copacabana | 943 | 838 | 695 | 1.533 | 532 | 3.008 |
| Santa Amélia | 1.167 | 1.042 | 829 | 1.870 | 594 | 3.631 |
| Garças | 76 | 76 | 64 | 140 | 55 | 271 |
| Jardim Leblon | 553 | 555 | 446 | 1.001 | 337 | 1.891 |
| Céu Azul | 1.394 | 1.299 | 1.066 | 2.365 | 902 | 4.661 |
| Santa Mônica | 1.199 | 1.138 | 951 | 2.089 | 697 | 3.985 |
| Trevo (camada IBGE, ver nota) | 826 | 790 | 567 | 1.357 | 451 | 2.634 |
| Braúnas | 112 | 91 | 94 | 184 | 74 | 370 |
| Santa Branca | 297 | 270 | 206 | 475 | 158 | 930 |
| Rio Branco | 602 | 611 | 516 | 1.127 | 464 | 2.193 |
| São João Batista | 957 | 901 | 717 | 1.618 | 601 | 3.176 |
| Nova Pampulha | 14 | 16 | 10 | 27 | 12 | 53 |
| Candelária | 465 | 415 | 347 | 762 | 287 | 1.514 |
| Piratininga | 1.265 | 1.192 | 946 | 2.138 | 755 | 4.158 |
| Itapoã | 456 | 422 | 386 | 808 | 289 | 1.553 |
| Planalto | 965 | 858 | 662 | 1.520 | 565 | 3.050 |
| Bandeirantes | 302 | 295 | 229 | 524 | 199 | 1.025 |
| São Luíz | 149 | 148 | 142 | 290 | 142 | 581 |
| Ouro Preto | 1.174 | 1.045 | 769 | 1.814 | 673 | 3.661 |
| **Soma 20 bairros** | **≈13.0 mil** | **≈12.1 mil** | **≈9.7 mil** | **≈21.8 mil** | **≈7.8 mil** | **≈42.6 mil** |

### Inferences
- Os 20 bairros somam ~227 mil habitantes (2022) e ~84,7 mil domicílios particulares ocupados; a população de 0 a 17 anos é da ordem de 42–43 mil (18,8% da população), com ~34,8 mil crianças de 0 a 14 (exato, IBGE).
- Os bairros com maior massa de crianças 0–14 em 2022 são Céu Azul (3.759), Piratininga (3.403), Santa Mônica (3.288), Santa Amélia (3.037), Ouro Preto (2.988), São João Batista (2.575), Planalto (2.485) e Copacabana (2.476). Os bairros da orla da Pampulha (Jardim Atlântico, Garças, Braúnas, Nova Pampulha, São Luíz) são pequenos e envelhecidos (São Luíz: 976 pessoas 70+ vs 121 de 0–4).
- Como o IBGE divulga idade só em grupos quinquenais por sigilo, a faixa 6–14 exata não é obtível de nenhum arquivo público do Censo 2022 em nível de bairro ou setor; só os microdados da amostra (áreas de ponderação, bem maiores que bairros) permitiriam idade simples.

### Gaps
- SIDRA: não encontrei nenhuma tabela SIDRA (incl. 4714, 9514, 9606) com recorte "bairro"; os dados por bairro estão apenas nos arquivos CSV/XLSX do FTP acima. "Não encontrado" em SIDRA — [busca](https://sidra.ibge.gov.br) não retornou tabelas de bairro.
- Painel "Panorama" do Censo 2022 (censo2022.ibge.gov.br/panorama) não foi verificado para bairros nesta sessão (limite de chamadas); o produto oficial é o FTP.
- Idade 0–5 / 6–14 / 15–17 exatas: não publicadas (apenas estimadas acima).

## Pergunta 2 — Como obter o recorte etário a partir de "Agregados por setores censitários" e como os limites de bairro foram casados com as unidades do IBGE (IBGE × PBH)?

### Takeaway
A agregação por setores não é necessária para idade (o IBGE já agrega por bairro), mas serve para auditar os limites: o arquivo por setor do IBGE traz `CD_BAIRRO/NM_BAIRRO` e a PBH publica o mesmo conjunto de 5.166 setores de 2022 com o campo `BAIRRO_CONSIDERADO_SETOR`. O cruzamento mostra que **a camada de bairros do IBGE para BH é a camada de "bairros populares" da PBH** (mesmos códigos de regional/TGC, mesmos totais em 459 dos 476 bairros), com diferenças pontuais: a principal, no entorno, é **Trevo**, cujo polígono IBGE (9.905 hab.) inclui os setores que a PBH hoje classifica como Dandara (3.872), Bispo de Maura (282) e Vila Trevo (334); o Trevo "estrito" da PBH tem 5.417 hab.

### Cited Findings
- Arquivo por setor IBGE: `Agregados_por_Setor_csv/Agregados_por_setores_basico_BR_20260520.zip` (15,4 MB zipado; CSV `Agregados_por_setores_basico_BR.csv` de 141 MB; Last-Modified 20/05/2026) e `Agregados_por_setores_demografia_BR.zip` (22,6 MB; Last-Modified 12/11/2024). Colunas do básico por setor: `CD_SETOR;SITUACAO;CD_SIT;CD_TIPO;AREA_KM2;CD_REGIAO;NM_REGIAO;CD_UF;NM_UF;CD_MUN;NM_MUN;CD_DIST;NM_DIST;CD_SUBDIST;NM_SUBDIST;CD_BAIRRO;NM_BAIRRO;CD_NU;NM_NU;CD_FCU;NM_FCU;CD_AGLOM;NM_AGLOM;CD_RGINT;NM_RGINT;CD_RGI;NM_RGI;CD_CONCURB;NM_CONCURB;v0001..v0009`. Filtro `CD_MUN == "3106200"` → 5.166 setores em BH — [IBGE FTP – Agregados_por_Setor_csv](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/Agregados_por_Setor_csv/)
- Procedimento para idade por setor (não executado por desnecessário, mas validado nas colunas): baixar `Agregados_por_setores_demografia_BR.zip`, juntar ao básico por `CD_SETOR`, somar `V01031..V01034` por `CD_BAIRRO` (campo do próprio IBGE) ou por `BAIRRO_CONSIDERADO_SETOR` da PBH (join por `CD_SETOR = COD_SETOR`). Atenção ao sigilo: células "x" (setores com <5 DPP ou frequências 1–2) devem ser tratadas como 0/NA, o que faz a soma por setores ficar ligeiramente abaixo do agregado por bairro publicado pelo IBGE — [Nota metodológica n. 06](https://biblioteca.ibge.gov.br/visualizacao/livros/liv102136.pdf)
- Dataset PBH "Setor Censitário 2022" (`20260101_setor_censitario_2022.csv`, 5.166 linhas): colunas `ID_SETOR_CENSITARIO_2022;COD_SETOR;TIPO_SITUACAO_DENS_OCUPACAO;NOME_SUBDISTRITO;REGIONAL_CONSIDERADA_SETOR;TGC_CONSIDERADA_SETOR;BAIRRO_CONSIDERADO_SETOR;QT_TOT_PESSOAS_RES_DOMC;QT_TOT_DOMC_OCUP;GEOMETRIA` (EPSG 31983) — [dados.pbh.gov.br – setor-censitario-2022](https://dados.pbh.gov.br/dataset/setor-censitario-2022); CSV: https://ckan.pbh.gov.br/dataset/c258fdc2-c14e-4a03-8770-cad282f5ef3a/resource/255fc2f5-f1b5-4b4c-94b1-670ebdeebb0e/download/20260101_setor_censitario_2022.csv
- Cruzamento IBGE×PBH (feito nesta sessão): todos os 5.166 `CD_SETOR` do IBGE existem em `COD_SETOR` da PBH. Para o bairro IBGE "Trevo" (18 setores): 11 setores são "Trevo" na PBH (5.417 hab.), 5 são "Dandara" (3.872), 1 "Bispo de Maura" (282) e 1 "Vila Trevo" (334) → total 9.905. Para Jardim Leblon, Copacabana, Céu Azul, Garças e Braúnas, 100% dos setores IBGE coincidem com o mesmo nome PBH — [IBGE setores básico](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/Agregados_por_Setor_csv/Agregados_por_setores_basico_BR_20260520.zip) × [PBH setor 2022](https://dados.pbh.gov.br/dataset/setor-censitario-2022)
- Dataset PBH "População e Domicílio por Bairro 2022" (`20250801_populacao_domicilio_bairro_2022.csv`, 493 bairros; colunas `ID_POP_DOMIC_BAIRRO_2022;NUM_BAIRRO;BAIRRO;AREA_KM;POPULACAO;DOMICILIOS;GEOMETRIA;DENSIDADE_DEMOGRAFICA`). Dicionário: "Processamento realizado a partir dos dados do censo 2022 do IBGE por setor censitário, tendo sido realizada proporção espacial dos setores censitários em relação aos bairros populares do município"; "Fonte do dado: IBGE, 2025" — [dados.pbh.gov.br – populacao-e-domicilio-por-bairro-2021 (título "2022")](https://dados.pbh.gov.br/dataset/populacao-e-domicilio-por-bairro-2021); CSV: https://ckan.pbh.gov.br/dataset/a6bfc464-a88b-4b50-a653-05f7975d5208/resource/4f51b598-374a-482b-a7b3-a7b4ce1beda8/download/20250801_populacao_domicilio_bairro_2022.csv ; dicionário PDF: https://ckan.pbh.gov.br/dataset/a6bfc464-a88b-4b50-a653-05f7975d5208/resource/cd4ceba2-b246-4b41-be9e-d0585f9633a4/download/ide-bhgeo-populacao-bairros-2022.pdf
- Comparação das camadas: IBGE (476 bairros) e PBH 2022 (493 bairros) somam ambas 2.315.560; 459 nomes coincidem e em 27 deles a população difere. No entorno: Trevo (IBGE 9.905 vs PBH 5.417 + Vila Trevo 334) e Jardim Leblon (IBGE 9.018 vs PBH 9.265 — a PBH atribui 26 setores, o IBGE 25). Vila Santa Mônica: IBGE separa 1ª Seção (1.548) e 2ª Seção (166) = PBH "Vila Santa Mônica" 1.714. "Vila Piratininga A" (IBGE, 265) = "Vila Piratininga Venda Nova" (PBH, 265). Bairros só na PBH (novos bairros populares, Lei 11.490/2023): Dandara, Bispo de Maura, Vila Trevo, Camilo Torres, Eliana Silva, Irmã Dorothy etc. — processamento desta sessão sobre os dois arquivos acima.
- Regionais/TGC segundo a PBH (campo `REGIONAL_CONSIDERADA_SETOR`/`TGC_CONSIDERADA_SETOR` dos setores de cada bairro): Jardim Atlântico, Santa Amélia, Garças, Trevo, Braúnas, Santa Branca, Nova Pampulha, Itapoã → Pampulha/P1; Bandeirantes, São Luíz, Ouro Preto → Pampulha/P2; Jardim Leblon, Piratininga → Venda Nova/VN4; Rio Branco, São João Batista, Candelária → Venda Nova/VN3; Planalto → Norte/N3; **Copacabana e Céu Azul têm setores em Pampulha (P1) e Venda Nova (VN4)**; **Santa Mônica em Pampulha (P1) e Venda Nova (VN3)** — [PBH setor 2022](https://dados.pbh.gov.br/dataset/setor-censitario-2022). O IBGE, por sua vez, vincula cada bairro a um só subdistrito: Copacabana, Céu Azul e Santa Mônica → "Venda Nova" (NM_SUBDIST) — IBGE bairros básico.
- Bairros pedidos que **não existem** nas camadas populacionais (IBGE e PBH): **"Enseada das Garças"** — não é bairro oficial; é denominação imobiliária/condominial dentro do bairro Garças (orla da Pampulha), e há também um "Residencial Enseada das Garças" em Copacabana — [Loft – Residencial Enseada das Garças, Copacabana](https://loft.com.br/condominio/residencial-enseada-das-garcas-copacabana-belo-horizonte-mg/3ywayo); [Loft – casa "Enseada das Garças", bairro Garças](https://loft.com.br/imovel/casa-rua-reginaldo-cunha-balaguer-garcas-belo-horizonte-4-quartos-518m2/aav0wydi). **"Sinimbu"** existe como *bairro oficial* (registrado em cartório) na camada PBH "Bairro Oficial" (código 916, 0,466 km²), mas não na camada de bairros populares usada para população; seu polígono fica ~76% dentro do bairro popular **Rio Branco** e ~15% em Santa Mônica (overlay desta sessão) → sua população está contida em Rio Branco/Santa Mônica — [dados.pbh.gov.br – bairro-oficial](https://dados.pbh.gov.br/dataset/bairro-oficial). "São Luís": grafia oficial PBH/IBGE é **São Luíz**; o bairro oficial (8,742 km²) inclui campus UFMG, aeroporto e lagoa, enquanto o bairro popular/IBGE tem 2,77 km² — mesmo dataset.

### Inferences
- Para fins do entorno escolar, o número do IBGE para "Trevo" (9.905) superestima o bairro Trevo tal como a PBH o entende hoje; recomenda-se usar 5.417 hab. (PBH 2022, soma de setores) + informar que a ocupação Dandara (3.872 hab., 2022) é contígua. Como as idades do IBGE para Trevo incluem Dandara, a faixa 0–14 do Trevo "estrito" só pode ser obtida somando V01031–V01033 dos 11 setores (não feito nesta sessão; método acima).
- A boa coincidência (459/476) indica que o IBGE adotou a camada de bairros (populares) enviada pela PBH para a malha 2022, atualizada antes da inclusão dos bairros criados pela Lei 11.490/2023.

### Gaps
- Não foi baixado o arquivo `Agregados_por_setores_demografia_BR.zip` (22,6 MB) — portanto não há faixas etárias para Trevo estrito/Dandara; o caminho e as colunas estão documentados acima.
- Metadado oficial da Malha de Bairros 2022 (geonetwork IBGE) e a notícia da Agência IBGE "O Censo na sua rua" retornaram HTTP 403 neste ambiente; a data exata da primeira divulgação dos agregados por bairro não foi confirmada (Last-Modified dos arquivos demografia = 12/11/2024; nota metodológica cita acesso em março/2024).

## Pergunta 3 — Censo 2010 por bairro (PBH) e crescimento 2010→2022

### Takeaway
A PBH publica população e domicílios por bairro de 2010 (`20220601_populacao_domicilio_bairro_2010.csv`, 487 bairros) e de 2022 (493 bairros), ambas na mesma camada de bairros populares, o que permite crescimento consistente. No entorno, os 20 bairros passaram de 214.803 (2010) para 222.673 (2022, camada PBH; 226.914 na camada IBGE por causa do Trevo) hab., +3,7%, enquanto os domicílios ocupados cresceram de 68.839 para 83.289 (+21,0%) — forte redução do tamanho médio das famílias. Crescimento populacional concentrado em Garças (+27%), Trevo (+26%), Ouro Preto (+19%), Bandeirantes (+17%), Santa Amélia (+12%), Planalto e Copacabana (+10%); perdas em Nova Pampulha (−12%), Jardim Atlântico (−10%), Santa Mônica (−8%), Rio Branco (−7%).

### Cited Findings
- Dataset PBH 2010: "Identificação do número de habitantes, domicílios e densidade populacional delimitados por bairro em Belo Horizonte de acordo com dados do censo demográfico 2010"; colunas `ID_POP_DMC,NUM_BAIRRO,NOME_BAIRRO,POPULACAO,DOMICILIO,HAB_DOM,HAB_KM2,AREA_KM2,GEOMETRIA`; 487 bairros; soma = 2.375.151 — [dados.pbh.gov.br – populacao-e-domicilio-por-bairros](https://dados.pbh.gov.br/dataset/populacao-e-domicilio-por-bairros); CSV: https://ckan.pbh.gov.br/dataset/a5305a65-6b64-41cb-9cd8-1e245b3c00fe/resource/3e60a1cf-3aae-4ba0-914a-a2b7d7d1c862/download/20220601_populacao_domicilio_bairro_2010.csv
- Versão impressa PBH 2010 "População Residente e Densidade Demográfica por Bairro, Território de Gestão Compartilhada e Regional" — [PBH PDF bairros_pop_dens_bh_2010](https://prefeitura-ds.pbh.gov.br/sites/default/files/noticia/corpo/bairros_pop_dens_bh_2010%20(3).pdf)
- Belo Horizonte: 2.315.560 hab. em 2022, queda de 2,5% (IBGE) frente a 2010 — [Itatiaia](https://www.itatiaia.com.br/brasil/sudeste/mg/censo-2022-saiba-qual-e-a-regional-mais-populosa-de-bh/); [Diário do Comércio](https://diariodocomercio.com.br/economia/censo-minas-segundo-estado-mais-populoso/)

#### Tabela C — 2010 vs 2022 por bairro [camada bairro PBH; NUM_BAIRRO idêntico nos dois anos]
Fontes: PBH 2010 (`POPULACAO`, `DOMICILIO`) e PBH 2022 (`POPULACAO`, `DOMICILIOS`; 2022 = soma de setores IBGE por proporção espacial). Variação calculada nesta sessão.

| Bairro | NUM_BAIRRO PBH | Pop. 2010 | Dom. 2010 | Pop. 2022 (PBH) | Dom. 2022 (PBH) | Var. pop. 2010→22 | Var. dom. 2010→22 |
|---|---|---|---|---|---|---|---|
| Jardim Atlântico | 653 | 1.459 | 462 | 1.316 | 448 | −9,8% | −3,0% |
| Copacabana | 828 | 13.333 | 4.202 | 14.650 | 5.293 | +9,9% | +26,0% |
| Santa Amélia | 762 | 18.188 | 5.789 | 20.449 | 7.914 | +12,4% | +36,7% |
| Garças | 807 | 966 | 291 | 1.228 | 363 | +27,1% | +24,7% |
| Jardim Leblon | 1493 | 9.460 | 2.961 | 9.265 | 3.448 | −2,1% | +16,4% |
| Céu Azul | 643 | 23.817 | 7.218 | 22.829 | 8.259 | −4,1% | +14,4% |
| Santa Mônica | 772 | 23.883 | 7.623 | 21.971 | 8.277 | −8,0% | +8,6% |
| Trevo (PBH estrito) | 827 | 4.311 | 1.238 | 5.417 | 1.874 | +25,7% | +51,4% |
| Braúnas | 652 | 2.031 | 664 | 1.988 | 657 | −2,1% | −1,1% |
| Santa Branca | 829 | 5.355 | 1.772 | 5.640 | 2.230 | +5,3% | +25,8% |
| Rio Branco | 818 | 12.768 | 3.944 | 11.836 | 4.324 | −7,3% | +9,6% |
| São João Batista | 785 | 16.503 | 5.463 | 17.668 | 6.885 | +7,1% | +26,0% |
| Nova Pampulha | 733 | 350 | 103 | 309 | 108 | −11,7% | +4,9% |
| Candelária | 1299 | 7.495 | 2.397 | 8.029 | 3.042 | +7,1% | +26,9% |
| Piratininga | 790 | 21.149 | 6.531 | 20.179 | 7.473 | −4,6% | +14,4% |
| Itapoã | 699 | 9.476 | 3.126 | 9.938 | 3.918 | +4,9% | +25,3% |
| Planalto | 750 | 16.814 | 5.653 | 18.501 | 7.082 | +10,0% | +25,3% |
| Bandeirantes | 742 | 5.428 | 1.835 | 6.355 | 2.287 | +17,1% | +24,6% |
| São Luíz | 641 | 4.762 | 1.533 | 4.525 | 1.454 | −5,0% | −5,2% |
| Ouro Preto | 738 | 17.255 | 6.034 | 20.580 | 7.953 | +19,3% | +31,8% |
| **Soma 20 bairros** | | **214.803** | **68.839** | **222.673** | **83.289** | **+3,7%** | **+21,0%** |

Vilas do entorno (PBH): Vila Copacabana 1.348→420 (−68,8%; provável reclassificação de setores); Vila Jardim Leblon 225→285; Vila Santa Mônica 2.132→1.714; Vila São João Batista 2.486→2.270; Novo Ouro Preto 502→523; Vila Trevo e Dandara não existiam na camada 2010 (Dandara 3.872 hab. em 2022).

### Inferences
- O entorno cresceu levemente (+3,7%) enquanto BH caiu 2,5%; o crescimento é maior nos bairros da regional Pampulha com verticalização recente (Ouro Preto, Santa Amélia, Bandeirantes) e nos pequenos bairros da orla (Garças, Trevo). Os bairros consolidados de Venda Nova (Santa Mônica, Rio Branco, Piratininga, Céu Azul) perdem população mesmo ganhando domicílios, sinal de envelhecimento e famílias menores.
- Como "domicílios" 2010 (PBH) são domicílios recenseados ocupados e 2022 (PBH) = `QT_TOT_DOMC_OCUP` (= v0007 IBGE, particulares ocupados), a comparação de domicílios é aproximadamente homogênea, mas não idêntica em definição.

### Gaps
- Faixas etárias de 2010 por bairro: não levantadas (fora do escopo pedido); obteníveis em IBGE "Agregados por Setores Censitários 2010" (arquivos `Pessoa11/12/13_MG.csv`, idade simples) cruzados com a camada PBH "Setor Censitário 2010" (dataset `setor-censitario-2010`, https://dados.pbh.gov.br/dataset/setor-censitario-2010) ou "Área de Ponderação Censo 2010".
- A página "Estatísticas e Indicadores" da PBH (https://prefeitura.pbh.gov.br/estatisticas-e-indicadores) hoje lista apenas Estatísticas dos serviços municipais, Indicadores ODS, IQVU-BH e IVJ-BH; a série "População por bairro" migrou para dados.pbh.gov.br — [PBH Estatísticas e Indicadores](https://prefeitura.pbh.gov.br/estatisticas-e-indicadores).

## Pergunta 4 — Em qual Unidade de Planejamento (UP) da PBH está cada bairro?

### Takeaway
As 80 UPs da PBH (camada `20220601_unidade_planejamento`) não seguem exatamente os limites de bairro; o overlay dos polígonos de bairro (PBH 2022) com os polígonos de UP (feito nesta sessão, por centroide e por fração do perímetro) indica a UP predominante de cada bairro, listada abaixo. O IQVU-BH é publicado por UP (1994–2016), mas **não encontrei indicadores demográficos (população por idade) publicados por UP** para 2022.

### Cited Findings
- Dataset PBH "Unidade de Planejamento": "Delimitação do município de Belo Horizonte em regiões subdivididas para fins de planejamento"; 80 UPs; colunas `ID_UNID_PLANEJAMENTO,COD_UNID_PLANEJAMENTO,NOME_UNID_PLANEJAMENTO,GEOMETRIA` (EPSG 31983) — [dados.pbh.gov.br – unidade-de-planejamento](https://dados.pbh.gov.br/dataset/unidade-de-planejamento); CSV: https://ckan.pbh.gov.br/dataset/2f581df7-3d64-4d41-8862-f1560db04776/resource/6b143f44-2839-4124-bd5a-2024e8715506/download/20220601_unidade_planejamento.csv
- UPs existentes no entorno (nomes exatos da camada): Pampulha, Santa Amélia, Copacabana, Garças/Braúnas, Céu Azul, Piratininga, São João Batista, Venda Nova, Planalto, São Bernardo, Ouro Preto, Jaraguá, Jardim Montanhês, Sarandi, UFMG — mesmo dataset.
- IQVU por UP: "Arquivo de texto com os dados utilizados do IQVU tendo por objetos as Unidades de Planejamento (UP) de Belo Horizonte (MG) e por atributos os indicadores" (`bd_iqvu_1994_2016.csv`) — [dados.pbh.gov.br – IQVU](https://dados.pbh.gov.br/dataset/indice-de-qualidade-de-vida-urbana-iqvu)
- Território de Gestão Compartilhada (TGC): "territórios constituídos pelo agrupamento de bairros dentro de uma mesma regional (...) apenas para efeito de planejamento" — [dados.pbh.gov.br – TGC](https://dados.pbh.gov.br/dataset/territorio-de-gestao-compartilhada)

#### Tabela D — Bairro → UP predominante [proxy geométrico, desta sessão]
"Fração" = parte dos vértices do contorno do bairro (PBH 2022) que cai em cada UP (proxy de área; não é área exata). "Centroide" = UP que contém o centroide do bairro.

| Bairro | UP do centroide | Frações por UP (perímetro) | Regional/TGC (PBH setores) |
|---|---|---|---|
| Jardim Atlântico | Santa Amélia | Pampulha 58%, Santa Amélia 41% (dividido) | Pampulha / P1 |
| Copacabana | Copacabana | Copacabana 65%, Santa Amélia 22%, Pampulha 6% | Pampulha P1 + Venda Nova VN4 |
| Santa Amélia | Santa Amélia | Santa Amélia 65%, Copacabana 23%, Pampulha 12% | Pampulha / P1 |
| Garças | Garças/Braúnas | Garças/Braúnas 81%, Pampulha 18% | Pampulha / P1 |
| Jardim Leblon | Copacabana | Copacabana 94%, Céu Azul 6% | Venda Nova / VN4 |
| Céu Azul | Céu Azul | Céu Azul 92%, Garças/Braúnas 5% | Pampulha P1 + Venda Nova VN4 |
| Santa Mônica | Copacabana | Copacabana 78%, Santa Amélia 12%, São João Batista 10% | Pampulha P1 + Venda Nova VN3 |
| Trevo | Garças/Braúnas | Garças/Braúnas 92%, Céu Azul 8% | Pampulha / P1 |
| Braúnas | Garças/Braúnas | Garças/Braúnas 54%, Pampulha 46% (dividido) | Pampulha / P1 |
| Santa Branca | Santa Amélia | Santa Amélia 87%, São João Batista 8% | Pampulha / P1 |
| Sinimbu (oficial) | Copacabana | contido em Rio Branco (76%) / Santa Mônica (15%) | Venda Nova |
| Rio Branco | Piratininga | Copacabana 67%, Piratininga 23%, Venda Nova 9% | Venda Nova / VN3 |
| São João Batista | São João Batista | São João Batista 50%, Venda Nova 38%, Copacabana 7% | Venda Nova / VN3 |
| Nova Pampulha | (centroide fora de UP; polígono minúsculo) | Garças/Braúnas 100% | Pampulha / P1 |
| Candelária | Venda Nova | Venda Nova 66%, Piratininga 12%, São João Batista 10% | Venda Nova / VN3 |
| Piratininga | Piratininga | Piratininga 76%, Copacabana 12%, Céu Azul 11% | Venda Nova / VN4 |
| Itapoã | Santa Amélia | Santa Amélia 77%, Planalto 16% | Pampulha / P1 |
| Planalto | Planalto | São Bernardo 57%, Planalto 28%, Venda Nova 6% (dividido; verificar com GIS) | Norte / N3 |
| Bandeirantes | Pampulha | Pampulha 82%, Sarandi 11%, Ouro Preto 5% | Pampulha / P2 |
| São Luíz | Pampulha | Pampulha 69%, Jaraguá 24%, Ouro Preto 6% | Pampulha / P2 |
| Ouro Preto | Ouro Preto | Ouro Preto 64%, Pampulha 20%, Jardim Montanhês 15% | Pampulha / P2 |

### Inferences
- As UPs relevantes para o entorno são, em ordem de peso populacional provável: Copacabana (Copacabana, Jardim Leblon, Santa Mônica, parte de Rio Branco), Santa Amélia (Santa Amélia, Santa Branca, Itapoã, parte de Jardim Atlântico), Céu Azul, Piratininga, São João Batista, Venda Nova (Candelária), Garças/Braúnas (Garças, Trevo, Braúnas, Nova Pampulha), Pampulha (Bandeirantes, São Luíz), Ouro Preto e Planalto/São Bernardo.
- Dado que vários bairros se repartem entre UPs e entre as regionais Pampulha e Venda Nova, um recorte por UP seria apenas um proxy grosseiro; o nível bairro (IBGE/PBH) é mais fiel para o entorno escolar.

### Gaps
- Não encontrei publicação da PBH com população por idade por UP para 2022 ("não encontrado"); o IQVU por UP cobre 1994–2016. Um recorte etário por UP pode ser montado somando os setores IBGE 2022 (demografia) por UP via overlay espacial (PBH setor 2022 × UP, ambos EPSG 31983).
- As frações da Tabela D são por perímetro, não por área nem por população; para uso oficial, refazer com GIS (interseção de áreas ou soma de setores por UP).
