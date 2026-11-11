# Categoria 1: aula particular de informática básica para adultos (plataformas de professores)

Consulta feita em 11/11/2026. Arquivo de dados: `tutores_cat1_informatica.jsonl` (76 linhas).

## Aviso principal

O Superprof, que era a fonte principal pedida, **bloqueou todo acesso automatizado** (proteção DataDome, HTTP 403 com captcha em curl e em Playwright; HTTP 405 no WebFetch). O Profes (profes.com.br) hoje **redireciona para o Superprof** (301 para superprof.com.br), portanto ficou igualmente inacessível. Nenhum preço do Superprof ou do Profes foi registrado, porque nenhum foi visto em página aberta.

Todos os 68 registros individuais vêm de uma única plataforma, **Suas Aulas Particulares** (suasaulasparticulares.com.br, a versão brasileira do grupo Tus Clases Particulares), que respondeu normalmente a curl.

## (a) Quantos registros

Categoria 1: 76 registros (68 ofertas individuais + 8 médias de plataforma). Nenhuma outra categoria.

| Nível geográfico | Ofertas individuais | Faixa de preço publicada | Com numeração antiga (ver ressalva 1) |
|---|---|---|---|
| Cidade do Rio de Janeiro | 12 | R$ 20/h a R$ 150/h | 7 |
| Restante do estado do RJ | 12 | R$ 20/h a R$ 70/h | 7 |
| Restante do Sudeste (SP, MG, ES) | 12 | R$ 20/h a R$ 100/h | 4 |
| Restante do Brasil | 12 | R$ 20/h a R$ 70/h | 3 |
| Sem cidade informada (anúncios só online) | 20 | R$ 20/h a R$ 100/h | 0 |
| **Total** | **68** | | **21** |

Canal das 68 ofertas: 37 presencial, 22 online, 9 ambos.

Médias de plataforma (8 linhas, `titulo` começa por "MÉDIA DA PLATAFORMA"): 7 do Suas Aulas Particulares (Brasil R$41/h, online R$40/h, Rio de Janeiro R$41/h, São Paulo R$45/h, Belo Horizonte R$35/h, Vitória R$31/h, "Informática para escritório" R$38/h) e 1 do GetNinjas (faixa "entre R$ 50 e R$ 200 por hora", sem valor único, `preco_valor_rs` null).

### Ressalvas que afetam o uso dos números

1. **Nenhuma página mostra data de publicação do anúncio.** `data_oferta` está null em todas as linhas. Os anúncios estavam ativos na listagem em 11/11/2026, mas não é possível provar que o preço foi definido em 2025/2026. A listagem nacional aparece aproximadamente em ordem decrescente de número do anúncio (a primeira página traz nº 2,45 a 2,47 milhões; as últimas, nº 1,4 a 1,7 milhão). Marquei com "Numeração antiga" em `observacao` as 21 ofertas com nº abaixo de 2.000.000. Não há como converter número em data: é só um indício de antiguidade. Quem quiser ser estrito com a regra "2025 ou 2026" deve filtrar essas 21 linhas; sobram 47 ofertas (5 na cidade do Rio, 5 no restante do RJ, 8 no restante do Sudeste, 9 no restante do Brasil, 20 online).
2. **R$ 20/h aparece em 26 das 68 ofertas** e em quase todos os anúncios antigos. Parece ser um valor mínimo ou padrão do cadastro da plataforma, não necessariamente um preço pensado pelo professor. Isso puxa para baixo qualquer média, sobretudo nos blocos do RJ.
3. As médias "da plataforma" são de toda a matéria Informática (inclui programação, concursos, hardware), não só informática básica. As páginas de Rio de Janeiro, Niterói, Nova Iguaçu, Duque de Caxias, São Gonçalo, Petrópolis e Volta Redonda mostram todas R$41/h, igual à página nacional, o que indica que esse número não é específico da cidade.
4. Os anúncios da seção online não informam a cidade do professor (cidade e uf null). Um deles diz no texto que atende presencialmente no Rio de Janeiro e foi contado no bloco da cidade do Rio.
5. Em quatro anúncios a plataforma classifica a cidade como "Rio de Janeiro", mas o campo "Geralmente ensinadas em" lista apenas municípios da Baixada Fluminense (Nova Iguaçu, Nilópolis, Queimados). Registrei a cidade onde a aula é dada e expliquei em `observacao`.
6. Tema: mantive anúncios cujo título ou descrição fala em informática básica, iniciantes, idosos/terceira idade, inclusão digital, uso de computador/celular/internet, Windows ou Office. Vários professores também citam outros temas no mesmo anúncio (concursos, manutenção, design); isso está anotado em `observacao`. Descartei anúncios centrados em programação, redes, hardware, concursos ou crianças.

## (b) Como coletei

**Suas Aulas Particulares** (curl com user agent de navegador, intervalo de 1,2 s entre requisições)
- Listagem nacional de Informática, páginas 1 a 55 (1.100 anúncios): `https://www.suasaulasparticulares.com.br/aulas-tecnologia/informatica?pagina=N`
- Listagem de "Informática para escritório", páginas 1 a 9 (163 anúncios): `https://www.suasaulasparticulares.com.br/aulas-tecnologia/informatica-para-escritorio`
- Páginas de cidade e online, só a primeira página, para a média e para conferir cobertura: `/professores-informatica/rio-de-janeiro`, `/sao-paulo`, `/belo-horizonte`, `/vitoria`, `/niteroi`, `/nova-iguacu`, `/duque-de-caxias`, `/sao-goncalo`, `/petropolis`, `/volta-redonda`, e `/online/informatica`.
- Dos 1.100 cartões, filtrei por palavras do título e do resumo, li a lista à mão e abri 111 páginas de anúncio. Em cada uma li o bloco "Preço" (valor por hora, "Primeira aula grátis", "Extra de deslocamento", "Geralmente ensinadas em"), a cidade, os níveis de aula e a descrição completa. Escolhi até 12 por bloco geográfico, dando preferência aos anúncios mais novos e de tema mais explícito, mais 20 anúncios só online.
- Um registro por professor: quando o mesmo professor tem vários anúncios, registrei um e citei os outros em `observacao` (dois casos têm preços diferentes entre anúncios: Leo, R$ 20/h e R$ 50/h; Jules, R$ 20/h e R$ 100/h).
- `url` é o link do anúncio. `evidencia` reproduz as linhas de texto do bloco "Preço" da página, na ordem em que aparecem; o separador " | " marca quebra de linha. Um script conferiu que cada evidência e cada citação entre aspas existe literalmente no texto salvo.
- `canal`: anúncios da seção `/online/` = online; anúncios de cidade = presencial (o perfil do professor rotula esses anúncios como "Aula Presencial"), ou "ambos" quando o texto do próprio anúncio diz que também atende online.
- `duracao_horas` = 1 porque o preço é publicado "/h". Um anúncio (Willian, R$ 30/h) diz na descrição "Aulas com duração entre 01:00 e 01:30. Valor R$ 30,00 por aula"; está em `observacao`.

**GetNinjas** (curl): `https://www.getninjas.com.br/aulas/informatica` traz só o texto de faixa média; a página de informática básica no RJ (`/aulas/informatica/informatica-basica/rj`) não mostra preço nem profissionais com preço.

**Evidências brutas**: `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/tutores_cat1/` (subpastas `sap_listings/` com as 75 páginas de listagem e `sap_ads/` com HTML e texto das 111 páginas de anúncio; arquivos `getninjas_*`, `superprof_*`, `preply_*`). Scripts usados: `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/scripts_cat1/`.

## (c) Procurei e não encontrei / bloqueado

| Fonte | O que tentei | Resultado |
|---|---|---|
| Superprof | `https://www.superprof.com.br/aulas/informatica-basica/rio-de-janeiro/`, `https://www.superprof.com.br/aulas/informatica/rio-de-janeiro/` e um perfil de professor, via curl, Playwright (Chromium padrão) e WebFetch | Bloqueado: HTTP 403 com captcha DataDome ("Please enable JS and disable any ad blocker") em curl e Playwright; HTTP 405 no WebFetch. Não tentei contornar a proteção. |
| Profes | `https://profes.com.br/professores/informatica-basica/`, `https://profes.com.br/aulas-particulares/informatica/` | Redireciona (301) para superprof.com.br, que bloqueia. |
| Preply | `https://preply.com/pt/online/professores-informatica`, `https://preply.com/pt/online/aulas-de-informatica`, perfis `https://preply.com/pt/professor/57833` e `/40620` (curl e Playwright) | HTTP 404 em todos ("página não encontrada"). Não achei listagem em português de professores de informática básica. |
| Tus Clases Particulares Brasil | `https://www.tusclasesparticulares.com.br/` | Host inacessível (502 no proxy). A versão brasileira ativa é suasaulasparticulares.com.br, usada acima. |
| Clasf | `https://www.clasf.com.br/q/aulas-informatica-idosos/` | Host inacessível (502 no proxy). |
| OLX | `https://www.olx.com.br/servicos/cursos-e-aulas?q=aula de informatica para idosos` | HTTP 403. |
| Apprentus | `https://www.apprentus.com.br/` (não resolve), `https://www.apprentus.com/pt-br` (404) | Sem versão brasileira acessível. |
| Classgap | `https://www.classgap.com/pt-br` (redireciona para a versão em inglês), `https://www.classgap.com/br/professores-particulares/informatica` (404) | Sem listagem brasileira de informática. |
| Cronoshare | Índice do guia de preços `https://www.cronoshare.com.br/quanto-custa/...` | Não há guia de preço para aulas de informática (só assistência técnica). |
| Beved | `https://beved.com.br/` | O site hoje é um blog, sem ofertas de aula. |
| GetNinjas | `https://www.getninjas.com.br/aulas/informatica/informatica-basica/rj` | Sem preço por profissional (modelo de pedido de orçamento). |
| Encontre um Professor, Fixando Brasil | `https://www.encontreumprofessor.com.br/`, `https://www.fixando.com.br/aulas-de-informatica` | Hosts inacessíveis (502 no proxy). |

Buscas feitas (WebSearch): "aulas particulares informática básica adultos idosos professor preço por hora Rio de Janeiro"; "aula particular de informática básica para adultos e idosos 'por hora' professor particular preço 2026" (excluindo superprof.com.br); "aulas particulares informática para idosos professor R$ hora encontresuaaula OR apprentus OR classgap"; "preply professores particulares de informática básica em português"; "preply.com/pt/online professores de informática online".

### Pistas para conferência manual (sem preço registrado)

As buscas devolveram perfis do Superprof que tratam exatamente do tema. Os resumos da busca sugerem que essas páginas exibem tarifa por hora, pacotes de 5h/10h e uma média por cidade, mas **não abri nenhuma delas e não registrei nenhum valor**. Uma pessoa com navegador comum consegue abrir:
- Listagem do Rio: https://www.superprof.com.br/aulas/informatica/rio-de-janeiro/
- https://www.superprof.com.br/tecnologia-sem-complicacao-para-adultos-idosos-computador-celular-internet-chatgpt-suporte-digital-com-paciencia.html (Rio de Janeiro)
- https://www.superprof.com.br/advogada-aulas-informatica-para-idosos-rio-janeiro.html (Rio de Janeiro)
- https://www.superprof.com.br/aulas-particulares-informatica-casa-para-adultos-idosos-aprenda-celular-smartphone-tablet-computador-notebook-muito.html (São Gonçalo)
- https://www.superprof.com.br/adultos-idosos-aulas-praticas-informatica-domicilio-home.html (São Paulo)
- https://www.superprof.com.br/informatica-para-idosos-jovens-acima-aprenda-mexer-celular-computador.html (São Paulo)
- https://www.superprof.com.br/adultos-idosos-agora-conectados-rede-aulas-iniciacao-informatica.html (Belo Horizonte)
- https://www.superprof.com.br/aulas-informatica-para-idosos-aprenda-usar-celular-whatsapp-internet-aplicativos-com-paciencia-seu-ritmo.html (Florianópolis)
- https://www.superprof.com.br/aulas-informatica-uso-celulares-domicilio-para-idosos-porto-alegre.html (Porto Alegre)

Observação para as outras frentes: o Suas Aulas Particulares também tem a matéria "Inteligência artificial" (`https://www.suasaulasparticulares.com.br/aulas-tecnologia/inteligencia-artificial`), no mesmo formato de preço por hora por professor. Não coletei porque é categoria 2.
