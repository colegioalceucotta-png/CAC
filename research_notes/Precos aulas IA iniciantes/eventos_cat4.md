# Categoria 4: oficinas, workshops e aulas ao vivo em grupo sobre IA (plataformas de eventos)

Consulta em 11/11/2026. Arquivo de dados: `eventos_cat4.jsonl` (51 registros, um por evento).
Evidências brutas (texto renderizado de cada página, JSON de evento e de ingressos, páginas de busca):
`/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/eventos/`
(scripts usados em `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/scripts_eventos/`).

## (a) Quantos registros

Todos os 51 registros são categoria 4 (grupo, preço por pessoa). Nenhum registro de categoria 3: não encontrei mentoria individual de IA com preço nessas plataformas (ver seção c).

| Nível geográfico | Pagos | Gratuitos (`gratuito`: true) |
|---|---|---|
| Cidade do Rio de Janeiro | 2 | 1 |
| Restante do estado do RJ (Petrópolis, Teresópolis, Niterói x2, Maricá) | 5 | 0 |
| Restante do Sudeste (SP, MG, ES) | 13 | 2 |
| Restante do Brasil (RS, PR, CE, PE, MS, MT, GO) | 13 | 1 |
| Sem cidade informada (online) | 11 | 3 |
| **Total** | **44** | **7** |

Por fonte: Sympla 48, Doity 1, Even3 1, Eventbrite 1 (gratuito). Meetup: nenhum.

Datas dos eventos: 41 pagos com data entre 11/11/2026 e 15/12/2026 (ingresso lido no bloco de ingressos da página) e 3 pagos já realizados em 2026 cujo preço está escrito na descrição (25/04, 15/04 e 16/09/2026). Nenhum registro de 2025: as páginas de eventos encerrados do Sympla não exibem mais os ingressos.

### Convenções usadas nos campos (ler antes de calcular R$/hora)

- `preco_valor_rs` é o preço do ingresso como exibido, **sem** a taxa da plataforma. Quando a página mostra a taxa à parte (ex.: "R$ 399,00 (+39,90 taxa)"), a taxa e o total estão em `observacao`. Quando não há taxa à parte na página, `observacao` diz isso (não significa que a página afirme "taxa incluída").
- Havendo lotes, usei o lote vigente na consulta; os demais estão em `observacao`. Em 3 registros de eventos com data 11/11/2026 (Porto Alegre, Ribeirão Preto e o festival do Rio) o lote já constava encerrado na consulta; em 2 (um online pago e um gratuito) as vendas ainda não tinham começado. Isso está em `observacao`.
- `evidencia` é texto literal da página renderizada; as quebras de linha entre o nome do ingresso, o preço e a data-limite foram trocadas por espaço.
- `duracao_horas`: para evento de um dia, diferença entre início e fim exibidos na página (frase "De ... até ..." citada em `duracao_texto`). Quando a descrição declara carga horária ou horários diferentes do cabeçalho, usei a carga declarada e citei as duas coisas. Para eventos de vários dias só preenchi quando a página dá os horários de cada encontro ou a carga total. Os tempos incluem intervalos/coffee/happy hour quando a página não separa.
- Online: `cidade` null, salvo quando a página dá a cidade do organizador (2 casos: São Paulo e Ribeirão Preto, contados em "restante do Sudeste").
- Vários registros são de "IA para negócios/empresários" ou de uma ferramenta específica (Claude, ChatGPT). Mantive os que são abertos ao público, sem exigir programação; ressalvas de público estão em `observacao`.

### Registros mais próximos do serviço que será precificado

- Porto Alegre, "Curso de Inteligência Artificial do zero, para quem tem mais de 40 anos": 3 encontros, 6h45, até 10 pessoas, R$ 437,00 (+43,70 taxa).
- Online, "Criação de Slide com Inteligência Artificial": 3h ao vivo, R$ 80,00 (+8,00 taxa).
- Rio de Janeiro, "Workshop - Inteligência Artificial Descomplicada": 1 dia (6h de aula), R$ 399,00 (+39,90 taxa).
- Belo Horizonte, "Inteligência Artificial para Todos": 1 dia (8h), R$ 788,00 (+78,80 taxa).
- São Paulo, "Oficina de IA | Claude Iniciante": manhã (3h30), R$ 420,00.

## (b) Como coletei em cada fonte

**Sympla**
- A busca do site (`https://www.sympla.com.br/eventos/rio-de-janeiro-rj?s=inteligencia%20artificial` e equivalentes) não funcionou neste ambiente: os resultados vêm de uma API interna de busca (Algolia) e a chamada da própria página voltou 404 ("Path not supported by Algolia REST API") no Playwright; a tentativa de consultar essa API diretamente foi bloqueada pela política de permissões da sessão e não insisti. Portanto **não usei o filtro de cidade do Sympla**.
- Alternativa 1 (principal): sitemap público `https://www.sympla.com.br/sitemap-eventos.xml` (24.346 eventos publicados). Filtrei os endereços por palavras-chave (ia, inteligencia-artificial, chatgpt, gpt, prompt, gemini, copilot, claude, canva, slides, apresentacao, automacao, agentes, produtividade etc.): 585 candidatos. Baixei a página de cada um (curl) para ler cidade/UF, datas, pago/gratuito e encerrado/aberto (`sympla_meta.jsonl`), e assim identifiquei todos os candidatos do estado do RJ.
- Alternativa 2: WebSearch restrito a sympla.com.br (cerca de 20 consultas: "inteligência artificial", "ChatGPT", "IA para iniciantes", "imersão em IA", "oficina de prompts", "apresentações com IA", "Gamma/Canva/NotebookLM", com Rio de Janeiro, Niterói, Petrópolis e outras cidades do RJ, São Paulo, Belo Horizonte, online, 2025 e 2026). Serviu só para achar endereços; nenhum preço veio do resumo de busca.
- Leitura do preço: abri 161 páginas de evento com Playwright (chromium) e salvei o texto renderizado (`sympla_<id>.txt`), o JSON do evento (`sympla_<id>_event.json`) e o JSON de ingressos carregado pela própria página (`sympla_<id>_tickets.json`). Li a descrição de cada candidato antes de incluir.

**Eventbrite**
- 60 páginas de busca baixadas por curl: `https://www.eventbrite.com.br/d/<local>/<termo>/` com locais brazil--rio-de-janeiro, brazil--niterói, brazil--são-paulo, brazil--belo-horizonte, brazil e online, e termos inteligencia-artificial, chatgpt, ia-para-iniciantes, workshop-ia, inteligencia-artificial-para-iniciantes, oficina-de-ia, curso-de-ia, ia-na-pratica, prompts, apresentacoes-com-ia (pasta `eb_search/`, 255 eventos distintos em `eb_search_results.json`).
- Resultado: nenhum evento pago de IA para iniciantes no Brasil. Os resultados em português com tema de IA são de Portugal (eventbrite.pt) ou gratuitos. Registrei 1 gratuito (Founder Institute, online, em português).

**Doity**
- Busca do site por curl: `https://doity.com.br/eventos?q=<termo>&page=1..3` com inteligencia+artificial, chatgpt, IA, ia+na+pratica, workshop+ia, oficina+ia, prompt, ia+para+iniciantes (pasta `doity_search/`). Abri 6 páginas de evento com Playwright.
- 1 registro pago (São Paulo). Os demais eram gratuitos de público restrito, de setor público/acadêmico ou com data em 2027.

**Even3**
- A página de busca não aplica o termo pelo endereço; usei as listas públicas que a própria página carrega (`even3_home_lista.json`, 144 eventos; `even3_lista_todos.json`) e WebSearch restrito a even3.com.br. Abri 4 páginas com Playwright.
- 1 registro pago (Olinda/PE). Os demais são acadêmicos (IA na pesquisa/escrita científica).

**Meetup**
- 17 buscas por curl: `https://www.meetup.com/pt-BR/find/?keywords=<termo>&location=<cidade>&source=EVENTS` (Rio de Janeiro, São Paulo, Belo Horizonte, Niterói; termos inteligência artificial, chatgpt, IA para iniciantes, workshop IA), pasta `meetup_search/`. 58 eventos distintos; os de IA são encontros técnicos de comunidades, sem taxa. Nenhum registro.

## (c) Procurei e não encontrei / bloqueado

- **Busca interna do Sympla com filtro de cidade**: bloqueada (detalhe acima). Consequência: a cobertura do Rio depende do sitemap (eventos publicados hoje) e do WebSearch; eventos cujo endereço não contém nenhuma das palavras-chave podem ter ficado de fora.
- **Cidade do Rio de Janeiro**: só 2 eventos pagos dentro do tema. Encontrados e descartados:
  - `https://www.sympla.com.br/evento/curso-presencial-de-trafego-pago-inteligencia-artificial-no-rio-de-janeiro/3547245` (05 e 06/12/2026, lote vigente R$ 549,90): curso de tráfego pago, IA é acessória.
  - `https://www.sympla.com.br/evento/a-marca-que-voce-deixa-lideranca-humana-na-era-da-inteligencia-artificial/3538264` (R$ 697,00 +69,70 taxa): palestra de liderança, não ensina IA.
  - `https://www.sympla.com.br/evento/curso-inteligencia-artificial-para-marketing-digital/3513026` (17/10/2026) e `https://www.sympla.com.br/evento/curso-intensivo-de-inteligencia-artificial-na-pratica-rio-de-janeiro-m2br-academy/3370586` (18/04/2026): encerrados, página não mostra preço.
  - `https://www.sympla.com.br/evento/praia-inovacao-e-ia/3132696` (18/10/2025) e `https://www.sympla.com.br/evento/workshop-gestao-inteligente/3496107` (31/07/2026): encerrados, cadastrados como gratuitos, sem preço na página.
  - IALIC 2026 (congresso de licitações), INOVA IA 2026 (conferência gratuita), IBMR Movimenta (extensão universitária gratuita): fora do escopo.
- **Outras cidades do RJ**: descartados `https://www.sympla.com.br/evento/workshop-e-commerce-inteligente/3633392` (Nova Iguaçu, R$ 997,00; tema é e-commerce), FEST GEMINI 2026 em Cabo Frio (é festa de academia de ginástica, não é IA), `https://www.sympla.com.br/evento/bootcamp-ia-para-negocios-petropolis/3116145` (09/05/2026, encerrado, sem preço), palestras gratuitas da OAB Cabo Frio e do Serratec Petrópolis (jurídico/segurança).
- **Eventos de 2025**: nenhum com preço. Páginas de eventos encerrados do Sympla mostram "O evento já encerrou..." sem ingressos; só 3 eventos encerrados de 2026 tinham o valor escrito na descrição. Exemplos encerrados sem preço: Workshop Prático de IA (13/08/2026), WSP2 Produtividade com IA (17/07/2026), Workshop IA para Professores (26/07/2026), IA & Produtividade (13/04/2026), Imersão IA na Prática em 4h (07/03/2026), "ChatGPT O Essencial sobre Prompts que Vai Mudar Seu Jogo" (16/06/2025, página 2968520), Gerencie seu Negócio com IA (03/09/2026).
- **Slides/apresentações com IA**: só 1 evento ao vivo específico (online, 12/12/2026). Buscas por "apresentações com IA", "slides com IA", Gamma, Canva, NotebookLM no Sympla e Eventbrite não trouxeram outro. O curso de Canva de Niterói entra com ressalva (IA é um tópico).
- **Categoria 3 (mentoria individual de IA)**: nada com preço. "Mentoria IA NA PRÁTICA com Mario Bodnar" (R$ 300,00) é em grupo e foi registrada como categoria 4; "Mentoria IA 360" (`https://www.sympla.com.br/evento/mentoria-ia-360/3562914`) está encerrada e cadastrada como gratuita.
- **Fora do intervalo de datas**: `https://doity.com.br/imersao-em-inteligencia-artificial-e-metodologias-ativas-t1` (online, 20/02/2027, R$ 37,00): preço visto na página, mas o evento é de 2027; não registrado.
- **Descartados por público ou tema** (preço visto, não registrados): Turma VIVO Imersão IA (São Paulo, R$ 690,00, turma na sede de uma empresa), SOS Recuperação com IA (Brasília, R$ 437,00, para alunos de 13+), curso da Univel em Cascavel (exclusivo para alunos), Líder Builder (R$ 4.800,00 +480,00 taxa), 1ª Imersão Eiaye (R$ 3.200,00 +320,00 taxa), IA de verdade para quem decide (João Pessoa, R$ 2.500,00), Imersão IA na Operação (São José do Rio Preto, R$ 1.497,00), DiretorIA (Porto Alegre, R$ 1.499,00), O Novo Jogo dos Negócios (Curitiba, R$ 597,00), Matriz Delta (Blumenau, R$ 900,00 e R$ 1.300,00), AI Festival Uberaba/Uberlândia e AI ao Cubo (festivais/conferências), Produto.Prompt.Copan e cursos de agentes, n8n, RAG, BIM, SAFe e afins (técnicos), além de dezenas de eventos setoriais (jurídico, saúde, condomínios, setor público).
- **Eventbrite, Meetup**: sem eventos pagos de IA para iniciantes no Brasil nas buscas feitas.
- **Even3**: busca por termo não funcionou pelo endereço; cobertura limitada às listas públicas da página e ao WebSearch.
