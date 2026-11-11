# Instituições de ensino: preços publicados (consulta em 11/11/2026)

Arquivo de dados: `instituicoes.jsonl` (23 registros). Evidências brutas (HTML, texto renderizado e JSON dos serviços das próprias páginas) em
`/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/instituicoes/`; scripts de coleta em `.../scratchpad/precos/inst_scripts/`.

## (a) Contagem

| Categoria | Registros | Pagos | Gratuitos |
|---|---|---|---|
| 4 – aula ao vivo em grupo sobre IA | 14 | 6 | 8 |
| 5 – curso gravado/EAD de IA | 5 | 0 | 5 |
| 1 – referência em grupo de informática básica (não é aula particular) | 4 | 1 | 3 |
| 2 e 3 | 0 | – | – |
| **Total** | **23** | **7** | **16** |

| Nível geográfico | Registros |
|---|---|
| Cidade do Rio de Janeiro | 3 (Sebrae RJ Méier, Sebrae RJ Centro, PUC-Rio CCE online com sede no Rio) |
| Restante do estado do RJ | 1 (Sebrae RJ, Macaé) |
| Restante do Sudeste | 13 (SP 5, MG 5, ES 3) |
| Restante do Brasil | 0 |
| Sem cidade informada (online) | 6 (Senac RJ online, Sebrae RJ por WhatsApp, SENAI SP online, Sebrae nacional x2, Descomplica) |

Preços pagos encontrados (preço cheio):
- PUC-Rio CCE, IA e Aprendizagem, 30 h online ao vivo: R$ 1.011,00 (só parcelado: 3 x R$ 337,00).
- Senac SP, IA: conceitos e práticas, 20 h presencial: R$ 392.
- Senac SP, IA Aplicada aos Pequenos Negócios, 20 h: R$ 484. IA Aplicada a Vendas, 20 h: R$ 484.
- Senac ES, IA: Soluções Práticas, 20 h: R$ 212,00. Automação de Tarefas e Processos com IA, 20 h: R$ 199,00.
- Referência cat. 1: Senac SP, Informática Essencial: Windows e Office, 80 h: R$ 903.

Tudo o que Sebrae (RJ, SP, MG, ES e loja nacional), Senac MG, SENAI SP online e Descomplica publicam sobre IA para iniciantes saiu como gratuito.

## (b) Como coletei em cada fonte

- **Senac SP** (`www.sp.senac.br`): o Chromium headless recebe "Access Denied"; com `curl` a página abre. O preço não está no HTML (o "R$ 414,40" que aparece no código é texto de modelo, não preço). A página busca as turmas em dois serviços próprios, que consultei direto: `/o/senac-content-services/cursosInfoDetalhe/20125/<articleId>` (unidades) e `/o/senac-oferta-services/ofertasPorCategoryIds/20125?...` (ofertas com `precoVendaOferta`, parcelas, datas). Lista de cursos por tema: `/o/senac-curso-services/cursosPorCategoryIds/20125?categoryIds=89054919` (Inteligência Artificial) e `40417` (TI). Carga horária lida no HTML do curso. Nos registros, `evidencia` traz os campos literais do retorno do serviço.
- **Sebrae** (`loja.sebrae.com.br` e subdomínios `rj.`, `sp.`, `mg.`, `es.`): busca renderizada com Playwright (`/catalogsearch/result/?q=inteligência artificial` e `?q=chatgpt`, páginas 1 a 3) e páginas de produto. No RJ a busca devolveu 31 itens; os únicos pagos eram turmas do Empretec (R$ 1.200,00), fora do tema.
- **Senac ES** (`es.senac.br/cursos?busca=...`): HTML estático com `curl`; o preço fica no atributo `data-turmas` e aparece na tela ao escolher a localidade (conferido com Playwright).
- **Senac MG** (`mg.senac.br/catalogo-de-cursos#/cursos/<id>`): Playwright, mais os serviços `listar-cursos-inscricoes-abertas-v2` (varri as 37 unidades) e `turmas-v2`. A página mostra só "CURSO GRATUITO" com o programa (PSG ou SENAC+); o campo `valorTurma` da API não é exibido e não foi usado como preço (está citado em `observacao`).
- **SENAI SP** (`www.sp.senai.br/cursos/0/0?pesquisa=inteligência artificial`): Playwright, abrindo o modal de turmas de cada curso.
- **PUC-Rio CCE** (`ccec.puc-rio.br/site/Cursos?nInst=cce`): `curl` no catálogo e nas 33 páginas de cursos com IA/AI/ChatGPT no título.
- **Senac RJ**: site oficial bloqueado; usei uma matéria jornalística (Hardware.com.br, 02/10/2026), marcada no registro como fonte secundária.
- **Descomplica**: página do curso renderizada com Playwright.

## (c) Procurei e não encontrei / bloqueado

- **Senac RJ** (`https://www.rj.senac.br/`, `https://www.rj.senac.br/cursos/`, `https://cursos.rj.senac.br/`): bloqueio do firewall do site em `curl`, Playwright e WebFetch ("A URL solicitada foi rejeitada. Seu ID de suporte é..."). Nenhum preço de curso pago do Senac RJ pôde ser visto. Matérias do Diário do Rio (01/09/2026) e do Hardware.com.br (02/10/2026) falam só de turmas gratuitas online ao vivo de 8 horas (IA na Prática, Canva IA, IA no Excel, Marketing Digital com IA).
- **Senac EAD nacional** (`https://www.ead.senac.br/cursos-livres/`, `/cursos-por-area/tecnologia-da-informacao/`): a página é um modelo Angular sem dados; a API (`/cms/api/cursos/...`) responde 403 "token não encontrado"; Playwright falha na conexão TLS. Não insisti em obter o token. Sem preço.
- **Senac SP, cursos de 4 horas** "Inteligência Artificial Descomplicada" e "Inteligência Artificial: como fazer a pergunta correta" (os mais próximos de uma oficina introdutória): 0 ofertas abertas em 11/11/2026, logo sem preço. Também sem oferta: "IA para Mídias Sociais" e "Produção de Vídeos com IA". Com preço, mas fora do recorte: "Técnicas de Redação com IA" (R$ 982), "IA com Adobe Express" (36 h, R$ 662), "IA com Excel", "PowerPoint: recursos profissionais" (R$ 335, sem IA).
- **Firjan SENAI** (`https://firjansenai.com.br/cursos`, `/modalidade/iniciacao-profissional`, `/area-profissional/ti-software`): 403 em `curl` e Playwright; pelo WebFetch o catálogo (367 cursos) não mostra preços e a busca por texto não filtra. Em Iniciação Profissional de TI só apareceram "Introdução à Lógica de Programação" e "Introdução ao Big Data" (60h, "Curso indisponível no momento", sem preço). Nenhum curso introdutório de IA ou de informática básica com preço.
- **SENAI SP, cursos presenciais** (ex.: "Fundamentos de Inteligência Artificial Generativa - Google Cloud", 20 horas, Mauá/Mogi/Alumínio/Paulínia): o modal mostra datas e "BOLSA / INSCRIÇÃO PRESENCIAL / RESERVE SUA VAGA", sem valor.
- **SENAI MG e SENAI ES**: não consultados (tempo).
- **Senac PR** (`https://www.pr.senac.br/cursos/?uep=37&tc=202600341`, "Descomplicando a Inteligência Artificial: como usar a IA no trabalho e na vida", 8h, Marechal Cândido Rondon, 14/11): a página mostra "Investimento em até 1 x R$ 0,01" e "vagas esgotadas", com textos sobre o PSG. Valor simbólico, não registrado como preço. A busca do site (`/busca/?q=`) não filtra por termo.
- **Senac RS, SC, DF**: busca do RS e de SC não devolveu cursos de IA no texto renderizado; DF respondeu 403. Sem dado.
- **PUC-Rio CCE**: dos 33 cursos com IA no título, 28 estão sem turma ("Receba informações quando novas turmas estiverem em oferecimento") e sem preço, inclusive os introdutórios "AI LAB I (Tudo o que você precisa conhecer sobre IA)" (45 horas), "Inteligência Artificial: Conceitos e Aplicações" (36 horas) e a "Aula aberta: A importância de se fazer boas perguntas para a Inteligência Artificial" (2 horas). Outros com preço são técnicos ou setoriais (IA Generativa & LLMs, 14 parcelas de R$ 829,00; Power BI com IA; IA para a Área da Saúde).
- **FGV Educação Executiva** (`https://educacao-executiva.fgv.br/produto/fundamentos-da-inteligencia-artificial-01tV200000Ji7neIAB`, 30 horas-aula online): Playwright e WebFetch caem na página inicial; no HTML baixado não há "R$". Sem preço visível.
- **Impacta** (`https://www.impacta.com.br/cursos/inteligencia-artificial-para-negocios/`): página de modelo sem carga horária nem valores (só "GANHE R$ 100,00 DE DESCONTO"). Sem preço.
- **Sebrae MG e ES**: nenhuma oficina presencial de IA/ChatGPT na loja; só os cursos online nacionais gratuitos. No ES apareceu uma consultoria para PJ (R$ 4.550,00), fora do recorte.
- **ESPM e Ibmec**: as páginas iniciais respondem, mas não cheguei a localizar curso introdutório de IA com preço (não pesquisados a fundo). **Sesc e Cubo**: não consultados (tempo).
- **Informática básica em grupo no RJ** (Senac RJ, Firjan SENAI): sem dado, pelos bloqueios acima. Senac ES não lista curso de informática básica na busca.

## Ressalvas para quem for usar os números

- Senac SP: o preço vem do serviço de ofertas que a página consulta, não de texto fixo no HTML; o valor à vista tem 8% de desconto (campo `precoDescontoOferta`).
- Senac MG e Senac ES (turmas gratuitas): gratuidade de programa (PSG, Senac+), com critérios de acesso; não equivale a preço zero para qualquer pessoa.
- Várias turmas de Senac MG e Senac ES começam em 2027, mas o preço foi publicado e lido em 11/2026.
- Eventos do Sebrae mostram dia e mês sem o ano.
- PUC-Rio: público do curso é de educação, e o valor é "da última turma oferecida, sujeito a reajuste".
