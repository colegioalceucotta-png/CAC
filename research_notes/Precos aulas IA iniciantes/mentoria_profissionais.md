# Mentoria individual de IA, guias de preço e páginas próprias de professores

Consulta em 11/11/2026. Arquivo de dados: `mentoria_profissionais.jsonl` (26 registros).
Evidências brutas (HTML e texto de cada página): `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/mentoria/`.
Cada trecho do campo `evidencia` foi conferido por script contra o texto salvo da página (`_build_jsonl.py` na mesma pasta).

## (a) Quantos registros

| Categoria | Registros | O que são |
|---|---|---|
| 1. Aula particular de informática básica | 6 | Só guias de preço do GetNinjas (3 faixas, mínimo e máximo de cada). Nenhuma oferta individual. |
| 2. Aula particular de IA/ChatGPT | 0 | Nenhuma página própria com preço encontrada. |
| 3. Mentoria individual de IA | 20 | 18 profissionais ou marcas (um deles com 3 pacotes): 10 em site próprio, 8 na Hotmart. |

| Nível geográfico | Registros |
|---|---|
| Cidade do Rio de Janeiro | 2 (faixa do GetNinjas para o Rio; categoria 1) |
| Restante do estado do RJ | 0 |
| Restante do Sudeste | 3 (Belo Horizonte, MG; categoria 3, mesmo profissional) |
| Restante do Brasil | 2 (Florianópolis, SC; Fortaleza, CE; categoria 3) |
| Sem cidade informada | 19 (4 da categoria 1, faixas nacionais; 15 da categoria 3, todas online ou sem canal declarado) |

Categoria 3, páginas abertas: cerca de 51 tentativas, 47 carregaram, 36 mostravam algum preço em R$. Dessas 36, 18 eram mentoria individual de IA e foram registradas (viraram 20 registros, porque uma página tem 3 pacotes). As outras 18 estão na seção (d).

Leitura dos 20 registros da categoria 3:
- Mais parecidos com o serviço do usuário: os três pacotes de Belo Horizonte (1 encontro R$ 250; 4 encontros de 1h30 R$ 800; 5 encontros de IA R$ 897, com 1h30 cada segundo o link de pagamento).
- Sessão avulsa de cerca de 1h: R$ 49,90 (promocional, de R$ 297), R$ 97, R$ 159,90 (45 min + guia), R$ 197 (duração não informada), R$ 250, R$ 450 (cobrança mensal), R$ 997.
- Pacotes de 3 a 6 encontros: R$ 597, R$ 800, R$ 897, R$ 1.297, R$ 1.997 (dois casos), R$ 2.850, R$ 7.500, R$ 9.997.
- Programas de 8 a 16 horas: R$ 3.468 (só parcelado), R$ 3.997, R$ 4.000.
- Dois registros têm aderência fraca e estão marcados na `observacao` ("ADERÊNCIA FRACA"): sessão sobre como vender agentes de IA (R$ 97) e sessão sobre projeto de software feito com IA (R$ 159,90).
- A maior parte é voltada a negócio, carreira ou nicho profissional (advogados, peritos, médicos, fotógrafos, professores). Mentoria individual de IA para iniciante leigo, com preço publicado, só apareceu em Belo Horizonte.

## (b) Como coletei

**GetNinjas (Parte B).** `curl` direto nas páginas, HTML salvo. Páginas com faixa de preço:
- `https://www.getninjas.com.br/aulas/informatica` (texto "Quanto custa em média uma aula de informática?": R$ 50 a R$ 200 por hora).
- `https://www.getninjas.com.br/aulas/informatica/rj/rio-de-janeiro` (R$ 50 a R$ 150 por hora).
- `https://www.getninjas.com.br/aulas/informatica/preco/curso-de-informatica-basica-online` (menor R$ 120, médio R$ 200, maior R$ 250, "valor de uma aula").
- Abertas e sem faixa de preço: `/aulas/informatica/rj`, `/rj/niteroi`, `/rj/duque-de-caxias`, `/rj/sao-goncalo`, `/sp/sao-paulo`, `/mg/belo-horizonte`, `/informatica-basica`, `/informatica-basica/rj/rio-de-janeiro`, `/powerpoint`, `/dispositivos-eletronicos`, `/softwares`, `/navegadores`, `/outros/presencial`.
- A única outra página de preço da categoria é `/preco/professor-particular-de-excel` (R$ 25 a R$ 150), fora do escopo.
- Ressalva: no cartão da página da categoria os rótulos do "curso de informática básica online" aparecem trocados (médio R$ 120, menor R$ 200) em relação à página de preço. Usei a página de preço. Nenhuma dessas páginas tem data visível.

**Cronoshare.** `curl` em `https://www.cronoshare.com.br/quanto-custa` (índice dos guias) e em `/servicos/aulas-de-informatica`. O índice lista guias de dezenas de aulas (violão, inglês, xadrez etc.), mas nenhum de aula de informática; as URLs `/quanto-custa/aulas-de-informatica`, `/aulas-informatica` e `/aula-de-informatica` caem no índice. A página de serviços não mostra preço.

**Sites próprios de mentores (Parte A).** WebSearch (cerca de 35 buscas, lista em (c)) e `curl` de cada candidato; Playwright quando a página dependia de JavaScript. Para cada preço guardei HTML e texto.

**Hotmart (Parte A).** Busca interna do marketplace com Playwright (`https://hotmart.com/pt-br/marketplace/produtos?q=...`, 14 termos, 158 produtos distintos listados, 25 com IA no título). A página do produto não mostra preço; o preço foi lido no checkout público `https://pay.hotmart.com/<código>`, trocando o país para Brasil (o checkout abria em dólar). 20 produtos abertos, 8 registrados.

**Asaas.** Dois links de pagamento públicos achados por busca; um deles confirma a duração (1h30) e o uso de Zoom do pacote de IA de Belo Horizonte.

## (c) Procurei e não encontrei / bloqueado

**Parte B**
- GetNinjas não tem página nem faixa de preço para aula de IA ou ChatGPT: `/aulas/informatica/inteligencia-artificial` e `/aulas/informatica/chatgpt` dão 404; 8 variações de `/aulas/informatica/preco/<termo>` dão 404.
- Cronoshare: sem guia de preço de aula de informática (ver acima).
- Habitissimo: `https://www.habitissimo.com.br/` inacessível (o proxy não conseguiu conectar ao host).
- Fixando: só apareceu a versão de Portugal, em euros; não usada.

**Parte C (páginas próprias de professores, categorias 1 e 2): nenhum registro.**
As buscas devolvem quase só marketplaces (Superprof, Profes, Suas Aulas Particulares), que não eram desta frente. Três páginas próprias com preço no resumo da busca não puderam ser abertas, então não foram registradas:
- `https://www.professoraparticularinformaticarj.com/` (Copacabana, Rio; o resumo da busca citava R$ 50 a hora e pacote de 4 aulas por R$ 140). Host não resolve. A última cópia arquivada é de 2020, fora do período.
- `https://www.netodealuguelrj.com.br/` (Rio, Duque de Caxias, São João de Meriti). Host não conecta. Última cópia arquivada de 2022.
- `http://professoradeinformatica.com/professora-aula-particular-informatica-idosos-joao-pessoa.html` (João Pessoa; resumo citava R$ 40 a hora). Host não resolve.
- OLX: `https://www.olx.com.br/servicos/estado-rj?q=aula de informática` devolve 403 (bloqueio) por `curl` e por Playwright.
- Google Sites, Wix, Blogspot, Instagram com link público: nenhuma página com preço apareceu nas buscas.

**Parte A, sem preço publicado ("sob consulta", "sob medida" ou nada)**
- `https://josephlynch.com.br/` (IA sem Mistério, mentoria para iniciantes, individual ou em grupo): "INVESTIMENTO SOB MEDIDA / Proposta personalizada".
- `https://cleberbarbosa.com.br/consultor-de-inteligencia-artificial/` (hora avulsa e pacotes de 4h/8h/12h): "Investimento: sob consulta".
- `https://kolodigital.com.br/mentoria-de-ia/` (Curitiba, mentoria individual "no seu ritmo"): sem preço.
- `https://augusto.ia.br/` (Goiânia, sessões avulsas): sem preço.
- `http://iapartner.com.br/`, `https://rwia.com.br/`, `https://hibra.ai/` (redireciona de acessarlink.com.br/M30D), `https://luizrangel.com/mentoria-ia/`, `https://propetec.com.br/`: sem preço na página.
- `https://sigmoidal.ai/mentoria/`: preço só em dólar ("a partir de US$ 150"), não registrado.
- Hotmart, produto Y96151901J (aula/consultoria individual de IA): checkout responde "Não há lote disponível para a oferta".

**Parte A, inacessíveis**
- `https://mentorian8n.com/`, `https://www.rfneural.com.br/consultoria.html`, `https://www.prismind.com.br/`: o proxy não conseguiu conectar.
- `https://www.ia2you.com.br/faca-sua-ia`: 404 hoje (o resumo da busca citava R$ 971 e 4 horas).
- Tentei abrir cópias arquivadas (Wayback Machine) de `mentorian8n.com` (captura de 07/11/2025) e de `ia2you.com.br/faca-sua-ia` (captura de 11/06/2026); a ação foi bloqueada pelo ambiente e não insisti. Se interessar, essas duas cópias podem ser conferidas à mão.
- Sympla: a busca interna (`/eventos?s=mentoria individual IA` e 3 variações) não carregou resultados no Playwright.
- Topmate, Superpeer, Calendly, Cal.com: as buscas só trouxeram mentores de outros países (rúpias, dólares); nenhum brasileiro com preço em R$.
- Workana e 99Freelas: só apareceu pedido de cliente ("consultoria com especialista em chatgpt por hora"), não oferta com preço fixo.
- GetNinjas não tem categoria de mentoria de IA.

**Buscas feitas (WebSearch), resumidas**
- Guias: "cronoshare quanto custa uma aula de informática"; "getninjas quanto custa aula de informática tabela de preços"; "fixando aulas de informática preços".
- Categoria 3: combinações de "mentoria individual" / "mentoria 1:1" / "consultoria individual" / "sessão avulsa" / "hora de consultoria" com "inteligência artificial", "ChatGPT", "IA para o seu negócio", "autônomos", "pequenos negócios", "MEI", "profissionais liberais", "empreendedoras", profissões (advogados, psicólogos, nutricionistas, contadores, corretores), e plataformas (Hotmart, Kiwify, Eduzz, Sympla, Topmate, Superpeer, Calendly, Cal.com).
- Categorias 1 e 2 em página própria: "aulas particulares de informática para idosos Rio de Janeiro valor da aula"; variações com Copacabana, Ipanema, Tijuca, Botafogo, Niterói; "neto de aluguel"; "aulas de celular para idosos a domicílio"; "tabela de preços" / "valores das aulas"; "sites.google.com", "wixsite", "blogspot"; "OLX aulas de informática para idosos Rio"; "aula particular de ChatGPT" / "aula individual de IA" / "IA para idosos"; "aulas particulares ChatGPT canva slides adultos iniciantes".

## (d) Preço visto, mas não registrado (fora do escopo desta frente)

Ficam aqui para quem consolidar decidir. Todos os valores foram vistos na página salva.

| Oferta | Preço visto | Por que ficou fora |
|---|---|---|
| Mentoria Tok de IA, `https://ia.tokon-line.com/` (contato com DDD 21) | "de R$1.497 por apenas 12x de R$97,00", "Total de R$1.164" | 6 meses de encontros quinzenais em grupo de 2h + 1 encontro individual; imagens do site de 10/2024, sem data de oferta |
| ProgramAI, `https://www.programaai.xyz/` | "R$ 2.500 em cash, pix ou TED", "10 × de R$ 365" | Pacote misto: 12 horas de workshop + 2 horas de mentoria individual |
| IABrokers, `https://www.iabrokers.com.br/` | "em até 12x de R$ 997 no cartão" | Mentoria de marketing imobiliário (IA é só uma parte) |
| Excelênc.IA, `https://excelencia.expandweb.com/` | "3x R$ 560", "À vista: R$1.500 (pix)"; 5 encontros de 1h30 | Em grupo; turmas de 05/12/24 e 06/01/25 |
| Asaas "Mentoria 3" (São Paulo), `https://www.asaas.com/c/238783233884` | "R$ 800,00"; "Cinco sessões de mentoria de E-commerce, Marketing Digital ou Produtividade. Duração de 60 minutos." | Não é de IA; sem data |
| Hotmart J97731328I, Mentoria em Inteligência Artificial | "Ou R$ 3.497,00 à vista" | Mistura encontros individuais e em grupo, sem quantidade nem duração |
| Hotmart V98851911M, Mentoria IA na Prática | "Ou R$ 1.990,00 à vista" | 4 encontros em grupo + 1 sessão individual |
| Hotmart E103178698B, Mentoria Premium IA Aplicada ao Trabalho | "Ou R$ 997,00 à vista" | Aulas gravadas + 2 encontros ao vivo em grupo |
| Hotmart V93697082A, Mentoria IA no Direito | "Ou R$ 760,00 à vista"; "Online com 1:30 horas de duração" | Não diz se é individual |
| Hotmart S97068743R, IA na Advocacia para iniciantes | "Ou R$ 599,99 à vista"; 20/01/25 a 18/02/25 | Em grupo |
| Hotmart B93377320E (R$ 3.327,00), Q94431248E (R$ 5.000,00), N99611955V (R$ 497,00) | valores à vista no checkout | Em grupo |
| Hotmart G107232326B, Mentoria Completa em IA | "Ou R$ 19.000,00 à vista" | Descrição genérica, sem formato |
| Hotmart I87231880I, Consultoria ChatGPT (advogados) | "one-time payment of R$ 9.000,00" | Página fala em 20 aulas/20 horas de conteúdo; parece curso |
| Hotmart D103428933V, Mentoria IA na prática | "R$ 97,00" | Acompanhamento por Telegram ligado a ebook de renda com IA |
| empreende.ai, `https://empreendeai.io/` | "R$97,90/mês" | É software (mentor automático), não pessoa |
| Mentory, `https://mentory.digital/` | R$ 120 a R$ 350 por sessão | Perfis de demonstração (fotos de randomuser.me), nenhum de IA |
| Guias de quanto cobrar: `freelasemcrise.com.br/quanto-cobrar/mentoria-negocios` ("Sessão avulsa de mentoria (1h): R$300–R$800") e `acheioprofissional.com.br/blog/consultoria-em-ia-quanto-cobrar-2026` ("R$ 400-1.500/hora") | faixas de blog | Texto de blog sem fonte, não é preço de oferta nem de plataforma de contratação |
| NandaTV, `https://www.nandare.com.br/post/curso-de-tecnologia-para-idosos` | "O curso completo custa R$ 199" (turma de outubro, 4 semanas) | Curso em grupo ao vivo para idosos: é categoria 4, de outra frente |

## Ressalvas gerais

- Nenhuma página de mentor em site próprio traz data de publicação, salvo onde indicado em `data_oferta`. Os preços são os vigentes na página em 11/11/2026.
- Nos registros da Hotmart o `url` é o checkout (onde o preço aparece); o endereço da descrição está em `observacao`.
- `canal` e `duracao_horas` ficaram `null` sempre que a página não dizia.
- Um registro (D9) só publica preço parcelado; `preco_valor_rs` é o total das parcelas.
- O valor de R$ 49,90 (Vini Ensina) é oferta para quem comprou um ebook; o preço de referência na página é R$ 297,00.
