# Renda, IDHM (Atlas Brasil/UDH), IQVU (PBH/UP) e vulnerabilidade – bairros do entorno do Alceu Cotta (Pampulha / Venda Nova / Norte, Belo Horizonte)

Bairros pesquisados: Jardim Atlântico, Copacabana, Santa Amélia, Garças (IBGE não tem "Enseada das Garças"), Jardim Leblon, Céu Azul, Santa Mônica, Trevo, Braúnas, Santa Branca, Sinimbu, Rio Branco, São João Batista, Nova Pampulha, Candelária, Piratininga, Itapoã, Planalto, Bandeirantes, São Luiz (grafia IBGE 2022: "São Luíz"), Ouro Preto, (Castelo incluído como referência de UP vizinha; Belvedere e Lourdes como referência de topo da cidade).

Convenções: SM 2010 = R$ 510 (ago/2010); SM 2022 = R$ 1.212. "Exato" = recorte coincide com o bairro oficial; "proxy" = UDH ou UP, que não coincidem com o bairro. Valores nominais do ano indicado, salvo indicação.

Arquivos de trabalho (não versionados; recomputáveis a partir das fontes citadas): `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/dl/ibge2010/bairros2010_table.txt`, `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/dl/ibge2022/renda_resp_2022.txt`, `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/dl/udh_table.txt`.

---

## Q1. O IBGE já divulgou renda do Censo 2022 por setor censitário / bairro? Qual tabela? E o que o Censo 2010 diz por bairro?

### Takeaway
Sim – desde 08/05/2026 o IBGE disponibiliza, no FTP do Censo 2022, "Agregados por Setores Censitários – Rendimento do Responsável" por setor, **bairro**, distrito, subdistrito e município (variáveis V06001–V06006: nº de responsáveis, moradores, rendimento **médio** e **mediano** dos responsáveis com rendimento). É a única renda do universo 2022 abaixo do município; não há renda per capita nem classes de rendimento por setor/bairro. Para esses indicadores (per capita, distribuição por classes, % pobres) a referência continua sendo o Censo 2010 (Agregados por setores – Básico, DomicilioRenda, ResponsavelRenda), que para Belo Horizonte traz o campo `Nome_do_bairro` (bairro oficial PBH), permitindo soma exata setor→bairro. Em 2022 os bairros com maior renda do responsável no grupo são São Luíz (média R$ 10.834; mediana R$ 7.000), Garças (R$ 8.689), Castelo (R$ 8.640) e Bandeirantes (R$ 8.168); Jardim Atlântico (R$ 6.073; mediana R$ 3.900), Santa Amélia (R$ 6.135) e Itapoã (R$ 6.100) ficam acima da média municipal (R$ 4.770), enquanto Copacabana (R$ 3.319; mediana R$ 2.100), Céu Azul (R$ 2.650), Jardim Leblon (R$ 2.261) e Piratininga (R$ 2.189) ficam abaixo.

### Cited Findings

**Situação das divulgações do Censo 2022 (renda)**
- O diretório FTP do Censo 2022 contém a pasta `Agregados_por_Setores_Censitarios_Rendimento_do_Responsavel/` com arquivos `Agregados_por_{setores|bairros|distritos|subdistritos|municipios}_renda_responsavel_BR_20260508_{csv|xlsx}.zip` e o `dicionario_de_dados_renda_responsavel_20260508.xlsx` (data 08/05/2026) — [IBGE FTP](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios_Rendimento_do_Responsavel/)
- Variáveis do dicionário (tema "Renda do Responsável"): V06001 "Pessoas responsáveis em domicílios particulares permanentes ocupados"; V06002 "Moradores em DPPO"; V06003 variância do nº de moradores; **V06004 "Valor do rendimento nominal médio mensal das pessoas responsáveis com rendimentos por DPPO"**; V06005 variância; **V06006 "Valor do rendimento nominal mediano mensal das pessoas responsáveis com rendimentos por DPPO"** — [dicionário IBGE 08/05/2026](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios_Rendimento_do_Responsavel/dicionario_de_dados_renda_responsavel_20260508.xlsx)
- O arquivo de bairros (`Agregados_por_bairros_renda_responsavel_BR_20260508_csv.zip`) tem 17.378 bairros no Brasil, dos quais 471 em Belo Horizonte (CD_BAIRRO iniciado em 3106200) — [IBGE FTP, arquivo citado](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios_Rendimento_do_Responsavel/Agregados_por_bairros_renda_responsavel_BR_20260508_csv.zip)
- Os demais "Agregados por setores censitários" do universo 2022 (temas: básico, características do domicílio 1–3, demografia, alfabetização, cor ou raça, parentesco, óbitos, indígenas, quilombolas; também disponíveis "por bairro") **não contêm nenhuma variável de rendimento**: busca por "rendimento/renda/salário" no dicionário `dicionario_de_dados_agregados_por_setores_censitarios_20260520.xlsx` retorna zero ocorrências (abas: Dicionário Básico, Siglas Básico, Dicionário não PCT, PCT-Indígenas, PCT-Quilombolas) — [IBGE FTP Agregados por Setores](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/) e [dicionário 20/05/2026](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/dicionario_de_dados_agregados_por_setores_censitarios_20260520.xlsx)
- A renda da amostra do Censo 2022 (módulo "Trabalho e Rendimento") foi divulgada em 9/10/2025 para Brasil, UFs e municípios; renda domiciliar per capita média do Brasil R$ 1.638 (2022); Belo Horizonte R$ 2.748,85 e Nova Lima R$ 4.299,91 (maior do país), segundo imprensa que cita o IBGE — [Tribuna de Minas 10/10/2025](https://tribunademinas.com.br/noticias/economia/10-10-2025/renda-per-capita-minas.html?amp=1); [O Fator (tabela MG)](https://ofator.com.br/informacao/as-10-cidades-de-maior-renda-per-capita-em-mg/); [Folha BV](https://www.folhabv.com.br/?p=574884). Observação do IPECE: as médias divulgadas consideram apenas domicílios com rendimento positivo — [IPECE Informe 271, jul/2025](https://www.ipece.ce.gov.br/wp-content/uploads/sites/45/2025/07/ipece_informe_271_21_jul2025.pdf)
- A divulgação dos microdados da amostra e das áreas de ponderação, prevista para 04/12/2025, foi adiada pelo IBGE por "necessidade de adequação a normas de proteção de dados" (aviso "Erramos" 27/11/2025) — [IBGE – Erramos](https://www.ibge.gov.br/novo-portal-erramos/45278-adiamento-das-divulgacoes-censo-demografico-2022-microdados-da-amostra-e-censo-demografico-2022-areas-de-ponderacao.html) (resumo via busca; a página bloqueou o acesso direto). Em 2026 o FTP já mostra as pastas `Microdados_de_acesso_Publico/`, `Areas_de_Ponderacao/` e uma nota "Atualizações – Microdados do Censo Demográfico 2022, data da atualização 14/09/2026" referindo-se a arquivos de dados de pessoas (variável P0115) — [IBGE FTP Microdados](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Microdados_e_Areas_de_Ponderacao/) e [nota de atualização 14/09/2026](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Microdados_e_Areas_de_Ponderacao/1_Atualizacoes_20260914.pdf). As notas metodológicas 02/2026 e 04/2026 descrevem as áreas de ponderação como "o menor recorte geográfico para divulgar os resultados da amostra" — [Nota 02/2026](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Microdados_e_Areas_de_Ponderacao/Documentacao/Notas%20metodol%c3%b3gicas/Notas%20metodol%c3%b3gicas%2002-2026%20-%20Metodologia%20de%20constru%c3%a7%c3%a3o%20das%20%c3%81reas%20de%20Pondera%c3%a7%c3%a3o.pdf)
- Sigilo nos agregados por setor 2022: setores com menos de 5 domicílios têm a maioria das variáveis omitida; evita-se divulgar células com frequência 1 ou 2 — [Agência IBGE Notícias](https://agenciadenoticias.ibge.gov.br/agencia-noticias/2012-agencia-de-noticias/noticias/39533-o-censo-na-sua-rua-ibge-publica-resultados-com-maior-nivel-de-detalhe-territorial)

**Censo 2022 – rendimento do responsável por bairro (EXATO; valores nominais 2022; fonte: arquivo IBGE 08/05/2026 citado acima; cálculo de SM e ranking feitos nesta pesquisa)**

| Bairro (IBGE 2022) | Responsáveis (V06001) | Moradores (V06002) | Renda MÉDIA resp. c/ rend. (V06004) | em SM 2022 | Renda MEDIANA resp. c/ rend. (V06006) | Posição entre 471 bairros de BH (média) |
|---|---|---|---|---|---|---|
| São Luíz | 1.451 | 4.030 | R$ 10.833,78 | 8,9 | R$ 7.000 | 20º |
| Garças | 363 | 1.197 | R$ 8.688,50 | 7,2 | R$ 5.650 | 29º |
| Castelo (ref.) | 11.512 | 28.498 | R$ 8.640,36 | 7,1 | R$ 6.000 | 30º |
| Bandeirantes | 2.287 | 6.074 | R$ 8.168,07 | 6,7 | R$ 5.000 | 31º |
| Ouro Preto | 7.950 | 20.152 | R$ 6.482,28 | 5,3 | R$ 4.500 | 55º |
| Santa Amélia | 7.912 | 20.338 | R$ 6.135,49 | 5,1 | R$ 4.500 | 59º |
| Itapoã | 3.918 | 9.869 | R$ 6.099,56 | 5,0 | R$ 4.200 | 61º |
| Jardim Atlântico | 448 | 1.308 | R$ 6.072,99 | 5,0 | R$ 3.900 | 62º |
| Braúnas | 657 | 1.909 | R$ 5.057,83 | 4,2 | R$ 2.600 | 81º |
| Santa Branca | 2.228 | 5.613 | R$ 4.980,97 | 4,1 | R$ 3.800 | 82º |
| Planalto | 7.080 | 18.232 | R$ 4.475,33 | 3,7 | R$ 3.000 | 91º |
| Santa Mônica | 8.276 | 21.903 | R$ 3.699,32 | 3,1 | R$ 2.500 | 110º |
| São João Batista | 6.883 | 17.646 | R$ 3.429,56 | 2,8 | R$ 2.500 | 126º |
| Candelária | 3.042 | 7.997 | R$ 3.417,94 | 2,8 | R$ 2.500 | 127º |
| Copacabana | 5.281 | 14.451 | R$ 3.318,94 | 2,7 | R$ 2.100 | 132º |
| Trevo | 3.340 | 9.848 | R$ 3.206,24 | 2,6 | R$ 1.800 | 139º |
| Rio Branco | 4.323 | 11.806 | R$ 3.179,61 | 2,6 | R$ 2.400 | 143º |
| Nova Pampulha | 108 | 309 | R$ 3.158,50 | 2,6 | R$ 2.200 | 145º |
| Céu Azul | 8.252 | 22.779 | R$ 2.650,15 | 2,2 | R$ 1.800 | 189º |
| Jardim Leblon | 3.365 | 9.015 | R$ 2.261,07 | 1,9 | R$ 1.500 | 236º (= mediana dos bairros de BH) |
| Piratininga | 7.471 | 20.175 | R$ 2.189,18 | 1,8 | R$ 1.500 | 249º |
| Novo Ouro Preto (vila/bairro à parte) | 177 | 523 | R$ 1.486,49 | 1,2 | R$ 1.212 | 414º |
| Sinimbu | – | – | **não encontrado** (não existe bairro IBGE com esse nome em BH, nem em 2010 nem em 2022) | | | |
| Referências: Belvedere / Lourdes | 3.008 / 8.243 | 7.783 / 17.619 | R$ 21.501,27 / R$ 13.874,97 | 17,7 / 11,4 | R$ 17.000 / R$ 10.000 | 2º / 8º |
| **Belo Horizonte (município)** | 889.554 | 2.306.089 | **R$ 4.770,03** | 3,9 | **R$ 2.500** | – |

Fonte: [IBGE, Agregados por bairros – renda do responsável, 08/05/2026](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios_Rendimento_do_Responsavel/Agregados_por_bairros_renda_responsavel_BR_20260508_csv.zip) e [Agregados por municípios](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios_Rendimento_do_Responsavel/Agregados_por_municipios_renda_responsavel_BR_20260508_csv.zip). Máximo entre bairros de BH: Senhor dos Passos R$ 38.322 (bairro pequeno, valor atípico), Belvedere R$ 21.501, Mangabeiras R$ 18.440; mínimos ≈ R$ 1.134 (Alto das Antenas, Boa União I).

**Censo 2022 – população e domicílios por bairro (EXATO; Agregados por bairros – Básico, 20/05/2026)**

| Bairro | Área km² | Pessoas (v0001) | Dom. particulares ocupados (v0007) | Média moradores (v0005) | Dom. vagos (v0009) |
|---|---|---|---|---|---|
| Jardim Atlântico | 1,13 | 1.316 | 448 | 2,9 | 61 |
| Copacabana | 1,44 | 14.650 | 5.293 | 2,7 | 683 |
| Santa Amélia | 2,23 | 20.449 | 7.914 | 2,6 | 844 |
| Garças | 1,25 | 1.228 | 363 | 3,3 | 49 |
| Jardim Leblon | 0,72 | 9.018 | 3.367 | 2,7 | 444 |
| Céu Azul | 2,75 | 22.829 | 8.259 | 2,8 | 1.142 |
| Santa Mônica | 2,18 | 21.971 | 8.277 | 2,6 | 1.045 |
| Trevo | 1,90 | 9.905 | 3.344 | 2,9 | 452 |
| Braúnas | 2,00 | 1.988 | 657 | 2,9 | 115 |
| Santa Branca | 0,87 | 5.640 | 2.230 | 2,5 | 401 |
| Rio Branco | 1,34 | 11.836 | 4.324 | 2,7 | 553 |
| São João Batista | 1,85 | 17.668 | 6.885 | 2,6 | 970 |
| Nova Pampulha | 0,03 | 309 | 108 | 2,9 | 13 |
| Candelária | 1,02 | 8.029 | 3.042 | 2,6 | 416 |
| Piratininga | 1,70 | 20.179 | 7.473 | 2,7 | 1.135 |
| Itapoã | 1,63 | 9.938 | 3.918 | 2,5 | 430 |
| Planalto | 2,51 | 18.501 | 7.082 | 2,6 | 874 |
| Bandeirantes | 4,78 | 6.355 | 2.287 | 2,7 | 201 |
| São Luíz | 2,75 | 4.525 | 1.454 | 2,8 | 241 |
| Ouro Preto | 2,37 | 20.580 | 7.953 | 2,5 | 930 |
| Castelo (ref.) | 2,41 | 28.551 | 11.516 | 2,5 | 1.101 |

Fonte: [IBGE, Agregados por bairros – Básico BR 20/05/2026](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/Agregados_por_Bairro_csv/Agregados_por_bairros_basico_BR_20260520.zip); variáveis conforme [dicionário 20/05/2026](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2022/Agregados_por_Setores_Censitarios/dicionario_de_dados_agregados_por_setores_censitarios_20260520.xlsx) (v0001 total de pessoas; v0007 DPPO+DPIO; v0005 média de moradores em DPO; v0009 DPP vagos).

**Censo 2010 – renda por bairro, soma exata setor→bairro (EXATO; valores nominais ago/2010)**

Método: arquivos "Base de informações por setor censitário – Censo 2010 – Universo", UF MG (`MG_20260615.zip`), planilhas Basico (campos `Cod_bairro`/`Nome_do_bairro`, V001 DPP, V002 moradores), ResponsavelRenda (V001–V010 responsáveis por classe de SM; V020 responsáveis total; V021 com rendimento; V022 total do rendimento) e DomicilioRenda (V002 total do rendimento nominal dos domicílios; V005–V014 domicílios por classe de renda per capita). Soma dos setores cujo `Nome_do_bairro` é exatamente o nome do bairro (vilas com nomes próprios, p.ex. "Vila Santa Monica 1ª Seção", "Vila Copacabana", "Vila Piratininga", "Vila São João Batista", "Vila Jardim Leblon", "Vila Bandeirantes", **não** foram somadas ao bairro-mãe). Verificação: média ponderada de Basico V005 para Castelo = R$ 3.995,8 vs. R$ 3.992 calculado (diferença por setores com sigilo). Fontes: [IBGE FTP – Agregados por setores 2010 MG](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2010/Resultados_do_Universo/Agregados_por_Setores_Censitarios/MG_20260615.zip) e [documentação](https://ftp.ibge.gov.br/Censos/Censo_Demografico_2010/Resultados_do_Universo/Agregados_por_Setores_Censitarios/Documentacao_Agregado_dos_Setores_2010_20231030.zip).

| Bairro (nome IBGE 2010) | Setores | DPP | Moradores | Renda média do responsável (com e sem rend.) R$ | em SM 2010 | Renda média resp. c/ rend. R$ | Renda domiciliar per capita R$ | % resp. ≤1 SM | % 1–2 | % 2–5 | % 5–10 | % >10 SM | % sem rend. | % dom. c/ renda pc ≤½ SM | % dom. c/ renda pc >5 SM |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| São Luiz | 9 | 1.397 | 4.623 | 6.307 | 12,4 | 6.704 | 3.002 | 2,9 | 5,9 | 17,0 | 31,2 | 37,1 | 5,9 | 1,6 | 46,1 |
| Bandeirantes | 8 | 1.677 | 5.268 | 5.467 | 10,7 | 5.758 | 2.595 | 7,4 | 11,5 | 21,5 | 21,2 | 33,3 | 5,1 | 4,5 | 37,7 |
| Garças | 2 | 255 | 930 | 5.076 | 10,0 | 5.284 | 2.101 | 7,8 | 9,4 | 20,0 | 27,5 | 31,4 | 3,9 | 2,7 | 29,4 |
| Jardim Atlântico | 4 | 451 | 1.439 | 4.341 | 8,5 | 4.702 | 2.017 | 12,3 | 13,8 | 17,8 | 25,3 | 23,1 | 7,7 | 8,0 | 30,6 |
| Castelo (ref.) | 33 | 6.065 | 17.042 | 3.992 | 7,8 | 4.279 | 2.182 | 3,9 | 7,9 | 25,9 | 33,3 | 22,4 | 6,7 | 2,0 | 34,0 |
| Santa Amélia | 22 | 5.784 | 18.183 | 3.080 | 6,0 | 3.306 | 1.565 | 7,5 | 14,3 | 32,7 | 25,4 | 13,3 | 6,8 | 3,5 | 17,6 |
| Ouro Preto | 31 | 5.537 | 16.746 | 2.990 | 5,9 | 3.231 | 1.539 | 12,3 | 17,3 | 25,5 | 21,5 | 15,9 | 7,5 | 7,3 | 22,8 |
| Itapoã | 14 | 3.124 | 9.473 | 2.979 | 5,8 | 3.346 | 1.661 | 6,5 | 14,1 | 30,8 | 23,1 | 14,6 | 11,0 | 2,9 | 20,2 |
| Braúnas | 5 | 577 | 1.944 | 2.926 | 5,7 | 3.273 | 1.251 | 19,9 | 19,9 | 22,5 | 14,5 | 12,7 | 10,6 | 11,7 | 19,2 |
| Santa Branca | 13 | 1.772 | 5.355 | 2.436 | 4,8 | 2.626 | 1.332 | 9,6 | 16,9 | 35,1 | 22,8 | 8,4 | 7,2 | 3,9 | 15,1 |
| Planalto | 27 | 5.421 | 16.581 | 2.163 | 4,2 | 2.346 | 1.178 | 13,9 | 22,1 | 32,5 | 16,4 | 7,2 | 7,8 | 6,6 | 10,6 |
| Nova Pampulha | 1 | 103 | 350 | 1.797 | 3,5 | 1.869 | 958 | 6,8 | 26,2 | 44,7 | 16,5 | 1,9 | 3,9 | 5,8 | 4,9 |
| São João Batista | 24 | 5.441 | 16.479 | 1.793 | 3,5 | 1.999 | 999 | 13,1 | 24,7 | 34,9 | 13,1 | 3,8 | 10,3 | 7,6 | 6,5 |
| Santa Mônica | 33 | 7.561 | 23.816 | 1.630 | 3,2 | 1.767 | 896 | 17,0 | 25,4 | 33,1 | 13,5 | 3,2 | 7,7 | 9,2 | 5,7 |
| Copacabana | 22 | 4.157 | 13.286 | 1.625 | 3,2 | 1.774 | 851 | 16,3 | 27,4 | 31,9 | 12,1 | 3,9 | 8,4 | 10,2 | 5,5 |
| Trevo | 5 | 1.186 | 4.249 | 1.462 | 2,9 | 1.776 | 757 | 25,3 | 24,0 | 18,9 | 9,4 | 4,7 | 17,7 | 23,3 | 5,9 |
| Candelária | 11 | 2.361 | 7.459 | 1.414 | 2,8 | 1.565 | 799 | 18,2 | 28,5 | 31,6 | 10,1 | 2,0 | 9,7 | 10,2 | 3,6 |
| Rio Branco | 18 | 3.943 | 12.767 | 1.388 | 2,7 | 1.487 | 747 | 20,3 | 30,8 | 30,8 | 9,4 | 2,1 | 6,7 | 11,8 | 3,1 |
| Céu Azul | 33 | 7.186 | 23.777 | 1.154 | 2,3 | 1.269 | 622 | 24,4 | 33,6 | 25,7 | 5,9 | 1,4 | 9,0 | 15,8 | 1,7 |
| Jardim Leblon | 25 | 2.919 | 9.349 | 1.015 | 2,0 | 1.185 | 604 | 23,9 | 32,8 | 23,2 | 4,7 | 1,1 | 14,4 | 16,8 | 2,2 |
| Piratininga | 29 | 6.516 | 21.129 | 985 | 1,9 | 1.079 | 534 | 27,5 | 35,2 | 23,8 | 4,1 | 0,6 | 8,7 | 18,6 | 0,9 |
| Novo Ouro Preto | 1 | 132 | 502 | 604 | 1,2 | 670 | 302 | 42,4 | 42,4 | 5,3 | 0 | 0 | 9,8 | 41,7 | 0 |
| Sinimbu | 0 | – | – | **não encontrado** (não há setor com esse nome de bairro) | | | | | | | | | | | |
| Belvedere (ref.) | 12 | 2.912 | 8.828 | 15.812 | 31,0 | 17.888 | 7.119 | 0,7 | 1,1 | 4,8 | 13,8 | 67,9 | 11,6 | 0,4 | 74,3 |
| Lourdes (ref.) | 37 | 7.448 | 18.860 | 8.564 | 16,8 | 9.299 | 4.781 | 1,8 | 3,9 | 13,5 | 21,3 | 51,5 | 7,9 | 0,8 | 66,0 |
| **Belo Horizonte (3.895 setores)** | 3.895 | 762.075 | 2.367.229 | **2.292** | 4,5 | 2.517 | **1.197** | 19,9 | 24,6 | 23,8 | 12,9 | 9,8 | 8,9 | 12,6 | 14,2 |

- Confirmação independente da ordem de grandeza (imprensa, Censo 2010, renda mensal média por domicílio): Belvedere R$ 15 mil, Mangabeiras R$ 13 mil, São Bento R$ 12 mil, Lourdes R$ 9.500; mínimos Distrito Industrial do Jatobá R$ 613, Vila Batik R$ 665 — [Estado de Minas, 16/11/2011](https://www.em.com.br/app/noticia/economia/2011/11/16/internas_economia,262205/renda-mensal-varia-mais-de-2-000-entre-os-bairros-de-bh.shtml)

### Inferences
- Em 2010 e em 2022 o grupo se estratifica em três patamares consistentes: (a) orla/entorno imediato da Lagoa – São Luiz, Bandeirantes, Garças (renda média do responsável 10–12 SM em 2010; 6,7–8,9 SM em 2022, 2–3 vezes a média municipal); (b) Jardim Atlântico, Castelo, Santa Amélia, Itapoã, Ouro Preto, Braúnas, Santa Branca (6–8,5 SM em 2010; 4–5 SM em 2022, acima da média de BH de 4,5 SM em 2010 e 3,9 SM em 2022); (c) Planalto, Santa Mônica, São João Batista, Candelária, Copacabana, Trevo, Rio Branco, Nova Pampulha (2,7–4,2 SM em 2010; 2,6–3,7 SM em 2022, próximo ou abaixo da média municipal) e (d) Céu Azul, Jardim Leblon, Piratininga (≈2 SM em 2010 e 1,8–2,2 SM em 2022, metade da média municipal; medianas 2022 de R$ 1.500–1.800). A queda em SM entre 2010 e 2022 ocorre em toda a cidade (BH: 4,5→3,9 SM) e reflete também a mudança de métrica (2010: média com e sem rendimento; 2022: só com rendimento) e a valorização real do salário mínimo; comparar posições relativas, não valores em SM.
- Jardim Atlântico é bairro pequeno (448 responsáveis em 2022; 4 setores em 2010), com média alta mas mediana bem menor (R$ 6.073 vs R$ 3.900 em 2022; em 2010, 12,3% dos responsáveis com até 1 SM e 23,1% acima de 10 SM): há heterogeneidade interna maior do que em Castelo ou São Luiz (3–4% com até 1 SM). Copacabana, por sua vez, tem perfil homogêneo de renda média-baixa (2022: média R$ 3.319, mediana R$ 2.100; 2010: 5,5% dos domicílios com renda per capita >5 SM).
- A diferença de renda do responsável entre a orla (São Luiz) e Copacabana/Céu Azul/Piratininga é de 3 a 5 vezes em ambos os censos – padrão intra-regional de desigualdade semelhante ao que a imprensa descreveu para a cidade inteira em 2011.

### Gaps
- Renda domiciliar per capita e distribuição por classes **para 2022** por bairro/setor: não divulgadas (só renda do responsável, média e mediana). Virão, se vierem, por áreas de ponderação/microdados da amostra (pastas existentes no FTP em 2026, conteúdo não verificado nesta pesquisa) ou tabelas SIDRA; para BH municipal, consultar SIDRA (Censo 2022 – Trabalho e Rendimento).
- "Sinimbu" e "Enseada das Garças" não existem como bairro IBGE (2010 ou 2022); provavelmente são denominações de loteamento/sub-área dentro de Garças/Braúnas/Bandeirantes. Confirmar na malha de bairros da PBH (dados.pbh.gov.br, dataset "bairro-popular", colunas ID;CODIGO;NOME;AREA_KM2;PERIMETR_M;GEOMETRIA – sem coluna de UP/regional) — [PBH bairro popular CSV 2024](https://ckan.pbh.gov.br/dataset/d890ccf6-d424-43bd-b513-b492306a0957/resource/710e73a6-c0b8-41e5-ad08-b6b9e33564dd/download/20240902_bairro_popular.csv) (arquivo de 1,8 MB; não li as linhas dos bairros).
- Não verifiquei se a malha de bairros IBGE 2022 coincide exatamente com a de 2010 (os códigos CD_BAIRRO 2022 têm 10 dígitos e nomes idênticos aos de 2010; a área 2022 de cada bairro está na tabela acima).

---

## Q2. Quais UDHs do Atlas Brasil cobrem cada bairro e quais seus IDHM, IDHM-Renda, renda per capita 2010 e indicadores de pobreza?

### Takeaway
O Atlas Brasil (RM Belo Horizonte, dados 2000/2010; não há atualização 2013/2021 por UDH – os perfis mostram apenas 2000 e 2010) tem UDHs cujos nomes concatenam bairros. Jardim Atlântico aparece apenas na UDH **1310620008230 "Santa Branca / Jardim Atlântico / Itapoã / Santa Amélia"** (35.222 hab.; IDHM 2010 0,887 "Muito Alto"; IDHM-Renda 0,877; renda per capita R$ 1.875,91 a preços de ago/2010; 1,56% pobres; Gini 0,50). Bandeirantes está na UDH **1310620008227 "Bandeirantes: Campus da Pampulha / Lagoa da Pampulha / Zoológico"** (12.828 hab.; IDHM 0,905; IDHM-Renda 0,946; renda per capita R$ 2.876,27; 0,64% pobres). Copacabana se divide em 6 UDHs com IDHM de 0,617 ("Copacabana: Universo / Vila do Índio", renda pc R$ 396,67) a 0,830 ("Copacabana Renovação", R$ 1.147,50); Céu Azul em 3 UDHs (0,685–0,808); Planalto tem UDH própria (IDHM 0,894; renda pc R$ 2.116,95). São Luiz, Braúnas e Sinimbu não aparecem em nome de UDH alguma de BH (não encontrado). Atenção: várias UDHs distintas exibem exatamente os mesmos valores (ex.: 8226 Castelo/Paquetá = 8227 Bandeirantes), o que indica que o Atlas estima indicadores para agrupamentos de UDHs – tratar como proxy, não como medida do bairro.

### Cited Findings
- Perfis de UDH do Atlas Brasil informam que "as informações do Perfil das unidades de desenvolvimento humano são extraídas do Censo Demográfico do IBGE" e trazem IDHM 2000 e 2010, população 2010, renda per capita 2000/2010 "a preços de agosto de 2010 (para convertê-los a preços de fevereiro de 2020, multiplicar por 1,71765)", % pobres (renda dom. pc < R$ 140), % vulneráveis à pobreza (< R$ 255), Gini, taxa de desocupação e grau de formalização — exemplo: [UDH 1310620008230](https://www.atlasbrasil.org.br/perfil/udh/1310620008230) (seções carregadas de `https://www.atlasbrasil.org.br/perfil/udh/idhm/<cod>` e `.../renda_trabalho/<cod>`).
- Busca de UDHs pelo endpoint `api/buscaTerritorios` do site (territorialidade 6 = UDH; sigla "RM - Belo Horizonte"; códigos 131062000xxxx = município de BH; grupo 0008 ≈ regional Pampulha, 0009 ≈ Venda Nova, 0006 ≈ Norte) — [Atlas Brasil – Consulta](https://www.atlasbrasil.org.br/consulta).

**Tabela – UDHs relevantes (2010 salvo indicação; renda per capita a preços de ago/2010). PROXY: a UDH não coincide com o bairro.**

| Cód. UDH | Nome da UDH (Atlas) | Bairros do grupo cobertos | IDHM 2000 | IDHM 2010 (faixa) | IDHM-R / -L / -E 2010 | Pop. 2010 | Renda pc 2000 → 2010 (R$) | % pobres 2010 | % vulneráveis (<R$255) 2010 | Gini 2010 | Desocup. 2010 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1310620008230 | Santa Branca / Jardim Atlântico / Itapoã / Santa Amélia | Jardim Atlântico, Santa Branca, Itapoã, Santa Amélia | 0,833 | 0,887 (Muito Alto) | 0,877 / 0,915 / 0,869 | 35.222 | 1.601,73 → 1.875,91 | 1,56% | 3,37% | 0,50 | 6,08% |
| 1310620008256 | Santa Mônica / Santa Amélia | Santa Mônica (parte), Santa Amélia (parte) | 0,735 | 0,808 (Muito Alto) | 0,779 / 0,893 / 0,758 | 2.151 | 770,22 → 1.017,52 | 2,30% | 14,30% | 0,49 | 7,28% |
| 1310620008227 | Bandeirantes: Campus da Pampulha / Lagoa da Pampulha / Zoológico | Bandeirantes (orla) | 0,834 | 0,905 (Muito Alto) | 0,946 / 0,929 / 0,843 | 12.828 | 1.836,65 → 2.876,27 | 0,64% | 2,81% | 0,48 | 3,68% |
| 1310620008226 | Castelo / Paquetá | Castelo (ref.) | 0,834 | 0,905 (Muito Alto) | 0,946 / 0,929 / 0,843 | 19.821 | 1.836,65 → 2.876,27 | 0,64% | 2,81% | 0,48 | 3,68% |
| 1310620008251 | Castelo / Paquetá (2ª UDH homônima) | Castelo (parte) | 0,759 | 0,832 (Muito Alto) | 0,812 / 0,903 / 0,786 | 1.240 | 1.028,10 → 1.255,14 | 2,12% | 6,77% | 0,46 | 4,04% |
| 1310620008231 | Garças / Trevo | Garças, Trevo (parte) | 0,834 | 0,879 (Muito Alto) | 0,881 / 0,916 / 0,843 | 4.333 | 1.836,65 → 1.919,92 | 1,14% | 4,65% | 0,47 | 5,59% |
| 1310620008245 | Conjunto São Francisco / Trevo | Trevo (parte, conjunto) | 0,540 | 0,661 (Médio) | 0,648 / 0,784 / 0,569 | 2.270 | 281,63 → 452,05 | 11,14% | 32,14% | 0,39 | 7,51% |
| 1310620008257 | Xangri-lá: Trevo / Nova Pampulha / Xangrilá Especial | Trevo (parte), Nova Pampulha | 0,694 | 0,808 (Muito Alto) | 0,779 / 0,893 / 0,758 | 1.134 | 717,18 → 1.017,52 | 2,30% | 14,30% | 0,49 | 7,28% |
| 1310620008229 | Paquetá / Engenho Nogueira / Ouro Preto | Ouro Preto (parte) | 0,834 | 0,879 (Muito Alto) | 0,881 / 0,916 / 0,843 | 16.604 | 1.836,65 → 1.919,92 | 1,14% | 4,65% | 0,47 | 5,59% |
| 1310620008236 | Ouro Preto: Novo Ouro Preto | Novo Ouro Preto (vila) | 0,572 | 0,661 (Médio) | 0,648 / 0,784 / 0,569 | 2.876 | 318,10 → 452,05 | 11,14% | 32,14% | 0,39 | 7,51% |
| 1310620008252 | Novo Ouro Preto: Ouro Preto | Ouro Preto (parte) | 0,694 | 0,808 (Muito Alto) | 0,779 / 0,893 / 0,758 | 2.027 | 717,18 → 1.017,52 | 2,30% | 14,30% | 0,49 | 7,28% |
| 1310620008255 | Copacabana | Copacabana (parte, lado Pampulha) | 0,694 | 0,808 (Muito Alto) | 0,779 / 0,893 / 0,758 | 742 | 717,18 → 1.017,52 | 2,30% | 14,30% | 0,49 | 7,28% |
| 1310620009290 | Copacabana / Jardim Leblon | Copacabana, Jardim Leblon | 0,649 | 0,771 (Alto) | 0,742 / 0,870 / 0,710 | 13.484 | 504,36 → 808,98 | 4,43% | 13,07% | 0,44 | 6,79% |
| 1310620009294 | Copacabana Renovação | Copacabana (parte) | 0,751 | 0,830 (Muito Alto) | 0,798 / 0,897 / 0,798 | 5.330 | 992,14 → 1.147,50 | 1,17% | 7,49% | 0,47 | 7,94% |
| 1310620009296 | Copacabana C | Copacabana (parte) | 0,759 | 0,832 (Muito Alto) | 0,812 / 0,903 / 0,786 | 1.550 | 1.028,10 → 1.255,14 | 2,12% | 6,77% | 0,46 | 4,04% |
| 1310620009265 | Copacabana / Vila Copacabana | Copacabana (vila) | 0,642 | 0,685 (Médio) | 0,674 / 0,823 / 0,580 | 1.455 | 439,67 → 529,29 | 7,41% | 24,57% | 0,39 | 7,31% |
| 1310620009264 | Copacabana: Universo / Vila do Índio | Copacabana (vila) | 0,531 | 0,617 (Médio) | 0,627 / 0,748 / 0,501 | 3.214 | 250,12 → 396,67 | 12,37% | 41,19% | 0,40 | 9,39% |
| 1310620009268 | Apolônia / Jardim Leblon | Jardim Leblon (parte) | 0,546 | 0,617 (Médio) | 0,627 / 0,748 / 0,501 | 6.883 | 305,00 → 396,67 | 12,37% | 41,19% | 0,40 | 9,39% |
| 1310620009284 | Jardim Leblon / Vila Jardim Leblon | Jardim Leblon (vila) | 0,582 | 0,685 (Médio) | 0,674 / 0,823 / 0,580 | 1.005 | 352,96 → 529,29 | 7,41% | 24,57% | 0,39 | 7,31% |
| 1310620009285 | Santa Monica: Jardim Leblon / Várzea da Palma | Santa Mônica/Jardim Leblon (parte) | 0,582 | 0,685 (Médio) | 0,674 / 0,823 / 0,580 | 1.905 | 352,96 → 529,29 | 7,41% | 24,57% | 0,39 | 7,31% |
| 1310620009302 | Céu Azul: Céu Azul Transição | Céu Azul (parte) | 0,676 | 0,808 (Muito Alto) | 0,779 / 0,893 / 0,758 | 8.880 | 572,83 → 1.017,52 | 2,30% | 14,30% | 0,49 | 7,28% |
| 1310620009291 | Céu Azul / Lagoa B | Céu Azul (parte) | 0,648 | 0,749 (Alto) | 0,720 / 0,842 / 0,693 | 17.482 | 441,13 → 704,01 | 1,87% | 12,85% | 0,40 | 6,83% |
| 1310620009281 | Céu Azul / Lagoa A | Céu Azul (parte) | 0,586 | 0,685 (Médio) | 0,674 / 0,823 / 0,580 | 3.937 | 332,83 → 529,29 | 7,41% | 24,57% | 0,39 | 7,31% |
| 1310620009304 | Santa Mônica / Rio Branco | Santa Mônica, Rio Branco | 0,733 | 0,830 (Muito Alto) | 0,798 / 0,897 / 0,798 | 20.942 | 840,60 → 1.147,50 | 1,17% | 7,49% | 0,47 | 7,94% |
| 1310620009303 | São João Batista / Santa Mônica | São João Batista, Santa Mônica (parte) | 0,783 | 0,866 (Muito Alto) | 0,846 / 0,911 / 0,844 | 6.262 | 1.212,31 → 1.544,29 | 1,35% | 5,17% | 0,50 | 4,35% |
| 1310620009271 | Piratininga: Vila Santa Mônica 1ª Seção | vila em Santa Mônica/Piratininga | 0,577 | 0,685 (Médio) | 0,674 / 0,823 / 0,580 | 1.789 | 353,50 → 529,29 | 7,41% | 24,57% | 0,39 | 7,31% |
| 1310620009299 | Rio Branco / Letícia | Rio Branco (parte) | 0,681 | 0,771 (Alto) | 0,742 / 0,870 / 0,710 | 15.247 | 615,12 → 808,98 | 4,43% | 13,07% | 0,44 | 6,79% |
| 1310620009295 | São João Batista: São João Batista / Candelária | São João Batista, Candelária | 0,741 | 0,830 (Muito Alto) | 0,798 / 0,897 / 0,798 | 12.005 | 732,75 → 1.147,50 | 1,17% | 7,49% | 0,47 | 7,94% |
| 1310620009305 | Candelária | Candelária | 0,741 | 0,808 (Muito Alto) | 0,779 / 0,893 / 0,758 | 5.261 | 732,75 → 1.017,52 | 2,30% | 14,30% | 0,49 | 7,28% |
| 1310620009266 | São João Batista: Vila São João Batista | vila | 0,546 | 0,650 (Médio) | 0,642 / 0,781 / 0,547 | 2.486 | 305,00 → 435,23 | 13,17% | 39,78% | 0,42 | 8,18% |
| 1310620009306 | São João Batista Renovado | São João Batista (parte) | – | **não obtido** (perfil retornou erro 500 no servidor) | | | | | | | |
| 1310620009292 | Piratininga / Lagoinha Leblon | Piratininga (maior parte) | 0,636 | 0,748 (Alto) | 0,718 / 0,841 / 0,692 | 27.704 | 484,32 → 697,80 | 5,67% | 18,93% | 0,47 | 7,64% |
| 1310620009286 | Piratininga | Piratininga (parte) | 0,582 | 0,685 (Médio) | 0,674 / 0,823 / 0,580 | 636 | 352,96 → 529,29 | 7,41% | 24,57% | 0,39 | 7,31% |
| 1310620006172 | Planalto | Planalto | 0,823 | 0,894 (Muito Alto) | 0,896 / 0,922 / 0,865 | 9.703 | 1.545,50 → 2.116,95 | 0,69% | 2,56% | 0,49 | 5,23% |
| 1310620006183 | São Bernardo / Planalto | Planalto (parte) | 0,731 | 0,832 (Muito Alto) | 0,812 / 0,903 / 0,786 | 5.931 | 878,35 → 1.255,14 | 2,12% | 6,77% | 0,46 | 4,04% |
| 1310620006171 | Biquinhas: São Bernardo / Planalto | Planalto (parte/vila) | 0,669 | 0,725 (Alto) | 0,712 / 0,838 / 0,639 | 2.523 | 555,10 → 672,29 | 2,56% | 19,64% | 0,42 | 6,90% |
| 1310620006184 | Planalto: Biquinhas | vila | 0,546 | 0,664 (Médio) | 0,640 / 0,778 / 0,589 | 1.671 | 305,00 → 429,58 | 11,14% | 35,73% | 0,38 | 8,95% |
| 1310620008228 | Jaraguá: Indaiá / Aeroporto (ref. UP Jaraguá) | – | 0,845 | 0,914 (Muito Alto) | 0,918 / 0,925 / 0,900 | 28.386 | 1.743,92 → 2.424,64 | 0,19% | 1,09% | 0,49 | 4,72% |

Fonte de cada linha: perfil de UDH do Atlas Brasil, `https://www.atlasbrasil.org.br/perfil/udh/<código>` (seções idhm e renda_trabalho), acessado em 25/10/2026; valores de IDHM-R/L/E extraídos do JSON embutido na seção IDHM (siglas IDHM_R, IDHM_L, IDHM_E, ano 2010).

- Contexto RMBH (mesma edição): IDHM da RMBH 0,682 (2000) → 0,774 (2010), 4ª RM do país; IDHM-Renda RMBH 0,737 → 0,788; UDHs com maior IDHM em 2010: Santo Agostinho/Lourdes 0,965, Savassi: Boa Viagem/Funcionários 0,954, Belvedere 0,951; 13 UDHs da Centro-Sul de BH com IDHM-Renda 1,000; menores IDHM 0,597 (vilas) — [Estado de Minas, 25/11/2014, sobre o Atlas do Desenvolvimento Humano nas RMs (Ipea/FJP/PNUD)](https://www.em.com.br/app/noticia/gerais/2014/11/25/interna_gerais,593370/grande-bh-melhora-desenvolvimento-humano-mas-ainda-apresenta-desigual.shtml)
- Belo Horizonte (município) ocupava a 17ª posição nacional no IDHM-Renda, com 0,841 (Atlas 2013, dados 2010) — [Ipea – Sobre o IDHM](https://www.ipea.gov.br/sites/en-GB/22-idhm/50-sobre-o-idhm)

### Inferences
- Valores idênticos em UDHs diferentes (ex.: 8226 Castelo/Paquetá e 8227 Bandeirantes; 8231 Garças/Trevo e 8229 Paquetá/Engenho Nogueira/Ouro Preto; 8255, 8256, 8257, 8252, 9302, 9305 todas com renda pc R$ 1.017,52) mostram que o Atlas RM atribui a mesma estimativa (derivada de áreas de ponderação da amostra do Censo) a vários polígonos de UDH. Portanto a renda per capita de "Bandeirantes" na UDH 8227 (R$ 2.876) é a mesma de Castelo/Paquetá, e não um valor próprio da orla; o Censo 2010 por setor (Q1) dá R$ 2.595 para Bandeirantes e R$ 3.002 para São Luiz – ordem de grandeza compatível.
- O conjunto Jardim Atlântico + Santa Branca + Itapoã + Santa Amélia forma uma única UDH de IDHM "Muito Alto" (0,887) e renda pc R$ 1.876 (2010) – ligeiramente abaixo da UDH Planalto (0,894; R$ 2.117) e acima de todas as UDHs de Copacabana (máx. 0,832), Céu Azul (máx. 0,808) e Piratininga (máx. 0,748). As UDHs de Copacabana/Jardim Leblon/Céu Azul concentram os maiores percentuais de vulneráveis à pobreza do grupo (13–41%).
- Para São Luiz, Braúnas e Sinimbu, a UDH mais provável é 1310620008227 (Bandeirantes: Campus / Lagoa / Zoológico) ou 1310620008231 (Garças / Trevo), por contiguidade, mas isso não pôde ser confirmado (não há mapa de UDH acessível por API).

### Gaps
- Não há no Atlas Brasil atualização 2013 ou 2021 por UDH: os perfis de UDH consultados exibem só 2000 e 2010; atualizações posteriores do Atlas são municipais/estaduais.
- "% da população por classe de renda" por UDH não aparece no perfil (apenas % extremamente pobres, pobres, vulneráveis e Gini). Se necessário, usar a planilha completa do Atlas RM (consulta/planilha do site, download via `api/dadosgridDowload`), não extraída aqui.
- UDH 1310620009306 (São João Batista Renovado): servidor retornou erro.
- Delimitação exata das UDHs (quais quarteirões de Copacabana/Céu Azul estão em cada UDH) só via mapa interativo do Atlas (consulta/map) – não recuperado.

---

## Q3. A que UP (Unidade de Planejamento) pertence cada bairro e qual o IQVU da UP (última edição) e sua posição entre as ~80 UPs?

### Takeaway
A última edição do IQVU-BH é **2016** (séries 1994–2016; "Nova Série" 2006–2016 com 10 variáveis/36 indicadores; escala 0–1; 80 UPs). No arquivo aberto da PBH há 79 UPs com valor (a UP 2508 "UFMG" não consta). Em 2016 (Nova Série), as UPs do grupo: **Pampulha 0,798 (7ª/79)**, Planalto 0,762 (17ª), São Francisco 0,762 (18ª), **Santa Amélia 0,747 (22ª)**, Venda Nova 0,747 (23ª), **Ouro Preto 0,743 (24ª)**, Jaraguá 0,737 (28ª), São João Batista 0,725 (32ª), **Garças/Braúnas 0,687 (43ª)**, Piratininga 0,644 (52ª), **Céu Azul 0,643 (53ª)**, **Copacabana 0,636 (55ª)**, **Castelo 0,595 (71ª)**; média das 79 UPs 0,689; máximo Francisco Sales 0,869; mínimo Furquim Werneck 0,464. A correspondência bairro→UP só é direta pelo nome (UP Pampulha, Santa Amélia, Garças/Braúnas, Castelo, Ouro Preto, Céu Azul, Copacabana, Piratininga, Planalto, São João Batista); a tabela oficial bairro→UP da PBH não pôde ser obtida (portal de dados bloqueou o acesso; relatório IQVU 2016 é PDF de imagem).

### Cited Findings
- A PBH descreve o IQVU como índice intraurbano que "mede a oferta e o acesso a bens e serviços urbanos", calculado para **80 Unidades de Planejamento**, com Série Histórica (1994, 2000, 2006, 2010, 2012, 2014, 2016; 9 variáveis/33 indicadores) e Nova Série (2006, 2010, 2012, 2014, 2016; 10 variáveis/36 indicadores), escala 0 a 1 (1 = acesso pleno); relatório metodológico "Relatório Geral sobre o Cálculo do IQVU-BH para 2016" — [PBH – IQVU](https://prefeitura.pbh.gov.br/estatisticas-e-indicadores/indice-de-qualidade-de-vida-urbana); [Relatório IQVU 2016 (PDF, 91 páginas, apenas imagem)](https://prefeitura.pbh.gov.br/sites/default/files/estrutura-de-governo/planejamento/relatorio_iqvu_2016_publicacao_versaoweb-1_0.pdf); [notícia PBH sobre o painel](https://prefeitura.pbh.gov.br/noticias/prefeitura-disponibiliza-novo-canal-para-acessar-indice-de-qualidade-de-vida)
- Base de dados aberta "1994-2016 Banco de Dados IQVU" (CSV; colunas SERIE;ANO;CODUP;NOMEUP;…;IQVU), SMPOG, criada 08/08/2019, atualizada 10/06/2026, licença ODbL — [dados.pbh.gov.br – IQVU](https://dados.pbh.gov.br/dataset/indice-de-qualidade-de-vida-urbana-iqvu); [CSV](https://ckan.pbh.gov.br/dataset/a167194d-f308-47d6-b040-109f7fb44490/resource/d9732b34-697d-49d4-84d1-9cd498807239/download/bd_iqvu_1994_2016.csv)

**IQVU por UP – valores extraídos do CSV da PBH (ranking entre as 79 UPs com valor em 2016 calculado nesta pesquisa; PROXY: UP ≠ bairro)**

| CODUP | UP | Regional (pelo prefixo do código: 25 = Pampulha, 26 = Venda Nova, 23 = Norte) | IQVU 2016 Nova Série | Posição 2016 (79 UPs) | IQVU 2014 Nova Série | IQVU 2016 Série Histórica | IQVU 2006 Nova Série |
|---|---|---|---|---|---|---|---|
| 2503 | Pampulha | Pampulha | 0,798 | 7ª | 0,781 | 0,777 | 0,798 |
| 2304 | Planalto | Norte | 0,762 | 17ª | 0,763 | 0,735 | 0,697 |
| 2509 | São Francisco | Pampulha | 0,762 | 18ª | – | 0,727 | 0,725 |
| 2502 | Santa Amélia | Pampulha | 0,747 | 22ª | 0,754 | 0,684 | 0,703 |
| 2605 | Venda Nova | Venda Nova | 0,747 | 23ª | 0,735 | 0,710 | 0,733 |
| 2507 | Ouro Preto | Pampulha | 0,743 | 24ª | 0,752 | 0,712 | 0,707 |
| 2504 | Jaraguá | Pampulha | 0,737 | 28ª | 0,745 | 0,680 | 0,714 |
| 2608 | São João Batista | Venda Nova | 0,725 | 32ª | 0,711 | 0,617 | 0,661 |
| 2604 | Jardim Europa | Venda Nova | 0,700 | 38ª | 0,655 | 0,636 | 0,617 |
| 2505 | Sarandi | Pampulha | 0,691 | 42ª | – | 0,633 | 0,623 |
| 2501 | Garças/Braúnas | Pampulha | 0,687 | 43ª | 0,623 | 0,576 | 0,607 |
| 2602 | Serra Verde | Venda Nova | 0,651 | 51ª | 0,656 | 0,558 | 0,628 |
| 2603 | Piratininga | Venda Nova | 0,644 | 52ª | 0,624 | 0,549 | 0,538 |
| 2606 | Céu Azul | Venda Nova | 0,643 | 53ª | 0,626 | 0,581 | 0,599 |
| 2607 | Copacabana | Venda Nova | 0,636 | 55ª | 0,652 | 0,576 | 0,579 |
| 2601 | Mantiqueira/Sesc | Venda Nova | 0,609 | 66ª | 0,609 | 0,527 | 0,552 |
| 2510 | Confisco | Pampulha | 0,605 | 68ª | – | 0,427 | 0,515 |
| 2506 | Castelo | Pampulha | 0,595 | 71ª | 0,675 | 0,573 | 0,650 |
| – | Média / mediana das 79 UPs (2016, Nova Série) | – | 0,689 / 0,694 | – | – | – | – |
| 1903 / 2303 | Máx. Francisco Sales / Mín. Furquim Werneck | Centro-Sul / Norte | 0,869 / 0,464 | 1ª / 79ª | – | – | – |

Fonte: [bd_iqvu_1994_2016.csv (PBH)](https://ckan.pbh.gov.br/dataset/a167194d-f308-47d6-b040-109f7fb44490/resource/d9732b34-697d-49d4-84d1-9cd498807239/download/bd_iqvu_1994_2016.csv), lido em 25/10/2026; IQVU = última coluna. Observação: no CSV não há linha para CODUP 2508 (UFMG) e, na Série Histórica, não há 2303.

- Dataset "Unidade de Planejamento" da PBH tem apenas ID_UNID_PLANEJAMENTO, COD_UNID_PLANEJAMENTO, NOME_UNID_PLANEJAMENTO e GEOMETRIA (atualizado jun/2022) – não lista bairros — [dados.pbh.gov.br – unidade-de-planejamento](https://dados.pbh.gov.br/dataset/unidade-de-planejamento/resource/6b143f44-2839-4124-bd5a-2024e8715506)
- Indícios indiretos de agrupamento territorial: a Apresentação Síntese do Plano Diretor Regional (PDR) Pampulha (PBH, 2018) organiza as "intenções para a estrutura urbana" em áreas: "1) Trevo e Xangrilá – concentração de lotes vagos…"; "2) Garças e Braúnas – região predominantemente residencial de alta renda onde a ocupação deve ser compatível com as restrições ambientais"; "3) Santa Amélia, Santa Branca e Santa Mônica – potencial de adensamento associado ao sistema viário principal"; "5) Conjunto Histórico Cultural da Lagoa da Pampulha – perímetro de proteção com parâmetros especiais"; "7) Castelo e Manacás – área com ocupação consolidada em processo recente de adensamento" — [PBH, Apresentação PDR Regional Pampulha (2018)](https://prefeitura.pbh.gov.br/sites/default/files/estrutura-de-governo/politica-urbana/2018/planejamento-urbano/apresentacao_pdr_pampulha.pdf). A versão de Venda Nova traz "13 – Copacabana: ocupação moderada com incentivo à formação de centralidades nas avenidas Central e Universo… respeito às definições do Plano Global Específico" e "14 – Santa Mônica / Rio Branco: possibilidade de adensamento… boa infraestrutura instalada… articulação com a Regional Pampulha" — [PBH, Apresentação PDR Regional Venda Nova (2018)](https://prefeitura.pbh.gov.br/sites/default/files/estrutura-de-governo/politica-urbana/2018/planejamento-urbano/apresentacao_pdr_vendanova.pdf). Diagnósticos completos (Vol. 1 e 2) estão em links do Google Drive listados em [PBH – Planos Diretores Regionais](https://prefeitura.pbh.gov.br/politica-urbana/planejamento-urbano/plano-diretor/regionais).
- Regional Pampulha: "41 bairros e 16 vilas agrupados em quatro territórios"; população 148.370 (Censo 2010) — [PBH – Regional Pampulha](https://prefeitura.pbh.gov.br/pampulha). Regional Venda Nova: 262.183 habitantes (Censo 2010); "mais de 50 bairros e vilas"; "a média salarial é de, aproximadamente, 2 salários mínimos" (sem ano/fonte) — [PBH – Regional Venda Nova](https://prefeitura.pbh.gov.br/venda-nova)
- O Centro de Saúde Santa Amélia (Rua Antero de Quental, Santa Branca, Regional Pampulha) atende "Santa Branca, Santa Amélia, Santa Mônica, Itapoã, Atlântico, Jardim Atlântico e Copacabana" — [PBH/SMSA, Acontece Saúde nº 234, 15/02/2023](https://prefeitura.pbh.gov.br/sites/default/files/estrutura-de-governo/saude/2023/Acontece-Saude-234-15-02-2023.pdf)

### Inferences
- Pela nomenclatura e contiguidade, a atribuição provável é: UP Pampulha (2503) ↔ Bandeirantes, São Luiz, São José (orla); UP Santa Amélia (2502) ↔ Santa Amélia, Santa Branca, Itapoã, Jardim Atlântico, Santa Mônica (parte Pampulha); UP Garças/Braúnas (2501) ↔ Garças, Braúnas, Trevo, Nova Pampulha, (Sinimbu?); UP Castelo (2506) ↔ Castelo; UP Ouro Preto (2507) ↔ Ouro Preto/Novo Ouro Preto; UP Copacabana (2607) ↔ Copacabana e Jardim Leblon; UP Céu Azul (2606) ↔ Céu Azul; UP Piratininga (2603) ↔ Piratininga; UP São João Batista (2608) ↔ São João Batista, Candelária, Rio Branco, Santa Mônica (parte Venda Nova); UP Planalto (2304) ↔ Planalto. **Isto é inferência não confirmada** – verificar na malha de UP (dados.pbh.gov.br) sobreposta à de bairros.
- O IQVU mede oferta/acesso a serviços, não renda: Castelo (bairro de renda alta, 7,1 SM em 2022) tem IQVU baixo (71ª), enquanto São João Batista e Venda Nova (renda média-baixa) ficam no terço superior; portanto IQVU e renda não devem ser lidos como sinônimos de "nível socioeconômico".
- Entre 2014 e 2016 (Nova Série) Garças/Braúnas subiu de 0,623 para 0,687 e Castelo caiu de 0,675 para 0,595; Santa Amélia, Ouro Preto e Copacabana recuaram levemente.

### Gaps
- Tabela oficial bairro→UP: não obtida (portal dados.pbh.gov.br/ckan bloqueou downloads via linha de comando – "Acesso Bloqueado/GoCache"; o relatório IQVU 2016 é PDF de imagem, 91 p., sem camada de texto; OCR não disponível no ambiente). Obter em: dataset "unidade-de-planejamento" + "bairro-popular" (sobreposição espacial) ou BHMap (bhmap.pbh.gov.br).
- Não há edição do IQVU posterior a 2016 (página PBH atualizada em 30/04/2026 lista 2016 como último ano).
- UP 2508 (UFMG) ausente do CSV; o ranking foi feito com 79 UPs.

---

## Q4. O "IPEAD/UFMG publica faixas de renda por bairro"? E existe "Índice de Vulnerabilidade Social" da PBH por UP?

### Takeaway
Não encontrei nenhum dataset de renda por bairro produzido pelo IPEAD. O que o IPEAD publica é a Pesquisa do Mercado Imobiliário de BH (boletins mensais de preços de venda/aluguel e "construção"), na qual os bairros são **classificados em quatro classes** (Popular <5 SM; Médio 5–8,5 SM; Alto 8,5–14,5 SM; Luxo ≥14,5 SM) segundo a renda média mensal dos chefes de domicílio do **Censo Demográfico 2000** (IBGE), conforme nota técnica "Classes_Bairros_BH_com_mapa.pdf"; a classe serve para agregar preços de imóveis, não para divulgar renda. Quanto ao "IVS por UP": a PBH não tem um Índice de Vulnerabilidade Social oficial por UP localizável hoje; o que existe é o **Índice de Vulnerabilidade da Saúde (IVS) da SMSA-BH**, edição 2012, por **setor censitário** (3.830 setores, Censo 2010, 4 categorias: baixo, médio, elevado, muito elevado), e o Índice de Vulnerabilidade Juvenil (IVJ-BH). O IVS 2012 inclui renda (rendimento médio do responsável invertido; % domicílios com renda per capita até ½ SM) e cor/raça entre seus indicadores.

### Cited Findings
**IPEAD/UFMG**
- Boletins IPEAD (Pesquisa de Construção/Aluguéis, 2015–2016): "Na apresentação dos resultados, os bairros de Belo Horizonte foram classificados de acordo com a renda média mensal dos chefes de domicílio obtida no Censo Demográfico de 2000"; "Classe 1 – Popular: representada pelos bairros em que a renda dos chefes dos domicílios é inferior a 5 salários mínimos (SMs)"; Classe 2 – Médio: 5 a <8,5 SM; Classe 3 – Alto: ≥8,5 e <14,5 SM; "Classe 4 – Luxo: representada pelos bairros em que a renda dos chefes dos domicílios é maior ou igual a 14,5 SMs"; detalhes na Nota Técnica "Classes_Bairros_BH_com_mapa.pdf" — [IPEAD, Pesquisa Aluguéis fev/2015](https://www.ipead.face.ufmg.br/site/publicacoes/download/imobiliario_alugueis-2015/02_2015_alugueis/pdf); [IPEAD, Construção jan/2016](https://ipead.face.ufmg.br:6443/wp-content/uploads/2023/10/01_2016_construcao.pdf); [IPEAD, Aluguéis mar/2016](https://ipead.face.ufmg.br:6443/wp-content/uploads/2023/10/03_2016_alugueis.pdf) (trechos obtidos via resultados de busca; o site do IPEAD respondeu 503/conexão recusada em 25/10/2026)
- Os mesmos boletins distinguem essa classificação por renda (IPEAD/Censo 2000) da classificação P1–P5 da PBH "que leva em consideração características construtivas do imóvel" — [IPEAD, Construção nov/2015](https://ipead.face.ufmg.br:6443/wp-content/uploads/2023/10/11_2015_construcao.pdf)
- Nenhum resultado de busca ("IPEAD renda por bairro", "Classes_Bairros_BH") apontou base de renda por bairro do IPEAD; todos remetem a tabelas de preços de imóveis por classe de bairro — [IPEAD, Construção dez/2018](https://ipead.face.ufmg.br/mercadoimobiliario/arquivos/Pesquisa%20Constru%C3%A7%C3%A3o%2012-2018_b%C3%A1sico%20comercial.pdf) (não aberto; 503)

**Vulnerabilidade – PBH**
- IVS 2012 (SMSA-BH, out/2012): "Dados do Censo Demográfico 2010 – IBGE; Unidade de análise: o setor censitário (SC)… Total de 3936 SC; 106 foram excluídos (2,7%)… SC analisados: 3830". Indicadores selecionados: dimensão Saneamento (% DPP com abastecimento de água inadequado; % esgotamento inadequado; % destino do lixo inadequado; razão de moradores por domicílio) e dimensão Socioeconômica (% pessoas analfabetas; "% de domicílios particulares com rendimento per capita até ½ SM"; "rendimento nominal mensal médio das pessoas responsáveis (invertido)"; "% de pessoas de raça/cor preta, parda e indígena"). Ponderação por método participativo "já adotado na construção do IQVU e do ISA". Categorias: IVS médio = média ± 0,5 DP; baixo < médio; elevado até +1,5 DP; muito elevado acima. Limitação: "toda a área terá o mesmo valor do IVS". Antecedentes: IVS 1998 (renda média dos chefes, Censo 91, peso 2,00) e IVS 2003 (renda média do chefe invertida, % chefes com até 2 SM) — [SMSA-BH, IVS 2012 (apresentação PDF)](https://prefeitura.pbh.gov.br/sites/default/files/estrutura-de-governo/obras-e-infraestrutura/2016-09set-27_smsa_ivs-2012.pdf). O IVS 2012 é descrito na literatura como "terceira atualização (IVS 1998, 2003 e 2012)" por setor censitário — [REME/UFMG, hanseníase e IVS](https://periodicos.ufmg.br/index.php/reme/article/view/49896); [Cad. Saúde Pública 2010 sobre o IVS da SMS-BH](https://scielosp.org/pdf/csp/2010.v26n12/2307-2315/pt)
- Índice de Vulnerabilidade Juvenil (IVJ-BH): desenvolvido pela PBH com apoio do CRISP-UFMG, "composto por sete indicadores… varia entre 0 e 100", base no Portal de Dados Abertos — [PBH – IVJ-BH](https://prefeitura.pbh.gov.br/estatisticas-e-indicadores/indice-de-vulnerabilidade-juvenil-de-belo-horizonte)
- Página "Estatísticas e Indicadores" da PBH lista IQVU, IVJ-BH, indicadores ODS e estatísticas de serviços – **não** lista um "Índice de Vulnerabilidade Social" por UP — [PBH – Estatísticas e indicadores](https://prefeitura.pbh.gov.br/estatisticas-e-indicadores)
- Estudo acadêmico "Índice de vulnerabilidade das políticas sociais (IVPS) para o município de Belo Horizonte" (Revista GEOgrafias, UFMG, 2019) usa geoprocessamento para identificar áreas vulneráveis – não é índice oficial — [GEOgrafias v.15 n.1](https://periodicos.ufmg.br/index.php/geografias/article/view/19739)
- Áreas de alta vulnerabilidade por renda domiciliar "alcançam 31,3% da área municipal" e concentram-se nas zonas de ocupação periférica (Ferreira, Geoingá, 2019) — [Geoingá 2019](https://periodicos.uem.br/ojs/index.php/Geoinga/article/download/49431/751375149079)

### Inferences
- A afirmação "IPEAD/UFMG publica faixas de renda por bairro" é parcialmente verdadeira apenas no sentido de que o IPEAD **rotula** bairros em 4 classes de renda (dados do Censo 2000, i.e., com 25+ anos), como variável de agregação de preços imobiliários; a fonte primária da renda é o IBGE, não o IPEAD. Para o estudo, a referência deve ser o IBGE 2010/2022 (Q1), citando o IPEAD apenas como classificação de mercado imobiliário.
- O "Índice de Vulnerabilidade Social por UP" da PBH provavelmente se refere ao IVS da Saúde (que é por setor censitário, não por UP) ou a trabalhos antigos da SMPL/Nahas (anos 1990–2000) sobre exclusão social por UP, dos quais não encontrei publicação acessível.

### Gaps
- Não consegui abrir a Nota Técnica "Classes_Bairros_BH_com_mapa.pdf" (site do IPEAD indisponível), logo não sei em qual classe cada bairro do grupo foi enquadrado. Obter em ipead.face.ufmg.br (Mercado Imobiliário → notas técnicas).
- Resultados do IVS 2012 por regional/bairro (gráficos de "população por distrito sanitário segundo IVS") estão em imagens na apresentação; a lista de setores por categoria é publicada pela SMSA (portal da saúde PBH, "IVS 2012") e permitiria tabular % da população de cada bairro por categoria de risco – não feito.
- Não localizei um IVS/“mapa da exclusão social” da PBH por UP (edições 2000) em formato acessível.

---

## Q5. Fontes secundárias (FJP, Observatório do Milênio, diagnósticos regionais PBH, teses UFMG) sobre o perfil socioeconômico da orla da Pampulha versus Jardim Atlântico / Copacabana / Santa Amélia

### Takeaway
Não encontrei estudo acadêmico ou relatório oficial que compare, com números, a orla da Pampulha com Jardim Atlântico/Copacabana/Santa Amélia. As menções localizadas são qualitativas (PDR Pampulha 2018: "Garças e Braúnas – região predominantemente residencial de alta renda"; geógrafo citado pela imprensa: orla com "um dos metros quadrados mais caros" e comunidades "frágeis" nos afluentes). A comparação quantitativa fica, portanto, apoiada nos dados primários da Q1 (Censo 2010/2022 por bairro) e Q2 (UDH): em 2022 a renda média do responsável em São Luiz (R$ 10.834) e Bandeirantes (R$ 8.168) é 1,3–1,8 vez a de Jardim Atlântico (R$ 6.073) e Santa Amélia (R$ 6.135) e 2,5–3,3 vezes a de Copacabana (R$ 3.319).

### Cited Findings
- PDR Pampulha (PBH, 2018): "2) Garças e Braúnas – Região predominantemente Residencial de Alta Renda onde a ocupação deve ser compatível com as restrições ambientais"; "3) Santa Amélia, Santa Branca e Santa Mônica – Potencial de Adensamento associado ao sistema viário principal"; "10) Confisco, Urca e Itatiaia – Bairros com ocupação popular polarizados pelo município de Contagem"; "1) Trevo e Xangrilá – concentração de lotes vagos… possibilidade de implantação de HIS" — [PBH, apresentação PDR Pampulha](https://prefeitura.pbh.gov.br/sites/default/files/estrutura-de-governo/politica-urbana/2018/planejamento-urbano/apresentacao_pdr_pampulha.pdf)
- Reportagem (Outras Palavras, 2013) cita geógrafo: a orla da Pampulha tem "um dos metros quadrados mais caros de Belo Horizonte", mas as comunidades no entorno dos afluentes são "frágeis do ponto de vista social"; "enquanto parte das ocupações foi feita com construções de qualidade por pessoas de classe mais alta, muitas foram absolutamente desordenadas" — [Outras Palavras – Lagoa da Pampulha: revitalizar ou maquiar para a Copa?](https://outraspalavras.net/outrasmidias/lagoa-da-pampulha-revitalizar-ou-maquiar-para-a-copa/)
- Artigo (UNESP/Formação) sobre a Pampulha: o plano original foi "diferenciado… a serviço da burguesia industrial emergente", com lotes e afastamentos maiores que o restante da cidade — [Revista Formação (UNESP)](https://revista.fct.unesp.br/index.php/formacao/article/download/1061/1066/3004)
- Texto do repositório UFMG (2008, citando Wikipédia – baixa confiabilidade) atribui à Região Administrativa Pampulha Gini 0,56 e renda per capita R$ 680,15, e nota o contraste entre "mansões na orla e em áreas nobres como Bandeirantes e São Luiz" e áreas de risco — [repositorio.ufmg.br (bitstream)](https://repositorio.ufmg.br//bitstreams/0b0d2ad7-e53f-4e9a-91e9-d1cb7bc55f37/download)
- Estudo de clusters de renda por setor censitário na RMBH (Cadernos do Leste, 2020, Censo 2010) encontra "forte concentração de renda… principalmente no Centro de Belo Horizonte, no seu entorno e no município de Nova Lima" – sem recorte Pampulha — [Cadernos do Leste 2020](https://periodicos.ufmg.br/index.php/caderleste/article/download/19177/27361/100455)
- Observatório do Milênio de BH (PBH/FJP/universidades, criado 2008) publicou relatório ODM 2010 sem recorte por bairro identificado nos resultados — [PBH – Observatório do Milênio](https://prefeitura.pbh.gov.br/planejamento/observatorio-do-milenio); [Relatório ODM (PDF)](https://prefeitura.pbh.gov.br/sites/default/files/estrutura-de-governo/planejamento/2019/relatorio_odm_corrigido.pdf)
- O documento UFMG "Região da Pampulha – representação do espaço" (Centro Pedagógico/UFMG) trata de relevo, fauna e flora da Lagoa, sem dados socioeconômicos — [repositorio.ufmg.br](https://repositorio.ufmg.br/bitstream/1843/42830/2/Regi%c3%a3o%20da%20pampulha_%20representa%c3%a7%c3%a3o%20do%20espa%c3%a7o.pdf)

### Inferences
- Síntese quantitativa possível com os dados primários (Q1/Q2): (i) orla (São Luiz, Bandeirantes, Garças) – responsáveis com renda média 10–12 SM em 2010 e 6,7–8,9 SM em 2022, 30–37% dos responsáveis acima de 10 SM em 2010, ≤4,5% dos domicílios com renda per capita ≤½ SM; (ii) Jardim Atlântico/Santa Amélia/Itapoã/Santa Branca – 4,8–8,5 SM em 2010 e 4,1–5,1 SM em 2022, UDH única de IDHM 0,887; (iii) Copacabana/Santa Mônica/São João Batista/Candelária/Rio Branco/Trevo – 2,7–3,5 SM em 2010 e 2,6–3,1 SM em 2022, UDHs entre 0,617 e 0,866; (iv) Céu Azul/Jardim Leblon/Piratininga – ~2 SM em ambos os censos, 16–19% dos domicílios com renda per capita ≤½ SM em 2010. A desigualdade intra-regional é da ordem de 3 a 5 vezes entre (i) e (iv).
- O IQVU (acesso a serviços) atenua essa gradação: UP Santa Amélia (22ª) e Ouro Preto (24ª) ficam perto de Venda Nova (23ª), e Castelo (71ª) abaixo de Copacabana (55ª); logo, para descrever "perfil socioeconômico" o indicador adequado é renda (IBGE) e IDHM-Renda (Atlas), não o IQVU.

### Gaps
- Nenhuma tese/dissertação UFMG localizada que trate especificamente de renda na orla vs. bairros interiores da Pampulha (buscas no repositório via web retornaram trabalhos sobre pescadores, biodiversidade e segregação em escala metropolitana). Sugestão: busca direta em repositorio.ufmg.br por "Pampulha" + "setor censitário"/"renda" e nos Diagnósticos Vol. 1/2 dos PDRs Pampulha e Venda Nova (links Google Drive na página PBH), que provavelmente contêm renda por UP (Censo 2010) – não abertos nesta pesquisa.
- Fundação João Pinheiro: nenhum produto específico sobre Pampulha localizado; a FJP é coautora do Atlas RM (Q2).
