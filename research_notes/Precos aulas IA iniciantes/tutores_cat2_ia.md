# Categoria 2 – aula particular de IA/ChatGPT para iniciantes (plataformas de professores)

Consulta: 11/11/2026. Arquivo de dados: `tutores_cat2_ia.jsonl` (38 linhas, todas `categoria` 2).
Evidências brutas: `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/tutores_cat2/` (scripts em `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/scripts_cat2/`).

**Resultado principal:** não há nenhum preço verificado de professor na cidade do Rio nem no restante do estado do RJ. O Superprof, onde esses anúncios existem, bloqueou todo acesso automático; a única plataforma aberta com a matéria (Suas Aulas Particulares) não tem anúncio de IA no estado.

## (a) Contagem

| Tipo de registro | Cidade do Rio | Restante do RJ | Restante do Sudeste | Restante do Brasil | Sem cidade (só online) | Total |
|---|---|---|---|---|---|---|
| Ofertas individuais dentro do escopo | 0 | 0 | 2 | 5 | 19 | 26 |
| Referência "FORA DO ESCOPO (IA técnica)" | 0 | 0 | 1 | 1 | 6 | 8 |
| "MÉDIA DA PLATAFORMA" (não é oferta) | 1* | 0 | 1 | 0 | 2 | 4 |

\* A média marcada como Rio vem de uma página sem nenhum anúncio (ver ressalva na `observacao` do registro); não conta como preço do Rio.

- Das 26 ofertas no escopo, 24 são da Suas Aulas Particulares e 2 do Preply.
- Suas Aulas Particulares (24 ofertas, preço por hora): de R$ 20/h a R$ 100/h, mediana R$ 50/h. Seis delas estão em R$ 20/h, que parece ser o valor padrão de cadastro (1.603 dos 4.028 anúncios de tecnologia vistos nas listagens estavam em R$ 20/h).
- Preply (2 ofertas, preço por aula de 50 minutos): R$ 112 e R$ 251. Uma delas é de professor venezuelano que fala português; está marcada como "PROFESSOR ESTRANGEIRO".
- 9 das 26 ofertas têm `observacao` começando por "LIMÍTROFE": anúncio genérico ou de informática geral em que IA é só um dos temas. Dá para filtrar por esse prefixo.
- Anúncios mais próximos do serviço do usuário (leigos ou iniciantes, uso no dia a dia): Jaqueline (R$ 80/h, MA), Kris (R$ 52/h, online), Marcos (R$ 50/h, online), João (R$ 40/h, online), Caroline (R$ 20/h, online) e Priscila (R$ 20/h, online). Só 1 anúncio cita apresentações com IA (Luiz Nelson, R$ 70/h, PI). Nenhum cita Gamma.

## (b) Como coletei

**Suas Aulas Particulares** (suasaulasparticulares.com.br, versão brasileira do Tus Clases Particulares) – curl simples, sem bloqueio.
- Listagens da matéria: `/aulas-tecnologia/inteligencia-artificial` (22 anúncios, 2 páginas) e `/online/inteligencia-artificial` (15 anúncios).
- Busca por palavra dentro de tecnologia e de aulas online: `/aulas-tecnologia/<palavra>` e `/online/<palavra>` com chatgpt, chat-gpt, gpt, gemini, copilot, claude, prompt, prompts, ias, artificial, ia-generativa, inteligencia-artificial-generativa, midjourney, notebooklm, gamma, canva, slides, apresentacoes, produtividade (perplexity, openai, deepseek e llm não devolveram nada).
- Categoria inteira de informática e tecnologia: `/aulas-tecnologia/ia` (a palavra "ia" é ignorada pelo site e devolve os 2.011 anúncios; 101 páginas).
- Por cidade: `/professores-inteligencia-artificial/<cidade>` para o Rio, 24 outras cidades do RJ e 18 cidades grandes de outros estados; `/professores-informatica/<cidade>` e `/professores-tecnologia-assunto/<cidade>` para o Rio e as mesmas 24 cidades do RJ; `/professores-informatica-para-escritorio/rio-de-janeiro`.
- Total: 425 páginas de listagem (138 listagens distintas), 4.028 anúncios distintos vistos em cartão, 314 perfis abertos e lidos por inteiro.
- Cada registro usa o link do perfil, e preço, tema e cidade foram lidos no perfil. O script `build_cat2.py` confere cada trecho de `evidencia` contra o HTML salvo.
- **Estado do RJ:** as páginas da matéria IA no Rio e nas 24 cidades testadas respondem "Não encontramos Aulas particulares e professores particulares de Inteligência articial em ...". Abri os 133 anúncios de tecnologia do estado (75 na capital): nenhum oferece aula de uso de IA. A única menção a IA é de um professor de programação de Petrópolis que pesquisa visão computacional.
- Ressalvas da fonte: anúncios sem data; anúncios da seção "Aulas online" não mostram a cidade do professor; para anúncios cadastrados em cidade a página não diz se há aula online (registrei "presencial" e anotei).

**Preply** (preply.com/pt) – curl com cookie `currency_code=BRL`.
- Listagem `https://preply.com/pt/online/professores--artificial` (895 professores no mundo), filtrada por `?CoB=BR` (12 nascidos no Brasil) e por `?tl=pt` (19 que falam português). Abri 5 perfis e usei 4.
- Quase todos ensinam programação, Python ou ciência de dados. O valor em reais é conversão feita pelo Preply e muda com o câmbio.

**Anúncios limítrofes vistos e deixados fora do JSONL** (preço lido no perfil da Suas Aulas Particulares):
- R$ 39/h – matéria IA, mas o anúncio não descreve conteúdo: `/online/inteligencia-artificial/instrutora-tecnologia-experiencia-aulas-virtuais-criadora-conteudo-educacional-mini-cursos-2160092`
- R$ 40/h – "Professora Especialista em IA", ensino superior, sem dizer se é uso ou técnica: `/online/inteligencia-artificial/professora-especialista-inteligencia-artificial-experiencia-anos-ensino-superior-nome-e-rejane-wronowski-2441993`
- R$ 50/h – informática, TI e IA, com vibe coding e n8n: `/online/inteligencia-artificial/professor-particular-informatica-inteligencia-artificial-2350993`
- R$ 50/h – n8n, Claude, vibe coding: `/online/inteligencia-artificial/aulas-inteligencia-artificialn8n-claude-antigravity-online-2446346`
- R$ 80/h – gestão, liderança, transformação digital e IA: `/online/inteligencia-artificial/aulas-particulares-sobre-assuntos-que-muitos-consideram-complicados-ensinados-uma-forma-muito-simples-objetiva-1627579`
- R$ 20/h – anúncio em espanhol: `/online/inteligencia-artificial/creacion-contenidos-multimedia-online-2439015`
- R$ 40/h – redes, TI, IA e informática: `/online/tecnologia-assunto/aprenda-tecnologia-verdade-aulas-praticas-redes-informatica-2376120`
- R$ 50/h – informática geral com "fundamentos de IA": `/online/informatica/professor-informatica-basico-avancado-windows-office-internet-canva-programacao-2331422`
- R$ 20/h – informática geral em Goiânia, com "Utilizando inteligência artificial" na lista de conteúdos: `/professores-goias/aulas-informatica-acordo-sua-necessidade-1975089`
- R$ 30/h – design no Canva com módulo "Introdução ao design com IA": `/online/desenho-grafico/aulas-design-grafico-canva-crie-artes-profissionais-mesmo-sem-experiencia-2338280`
- R$ 60/h – campanhas para infoprodutos com Canva e ChatGPT: `/online/escritura/aprenda-fazer-campanhas-infoprodutos-faturar-isso-2160568`
- R$ 100/h – aulas de MacBook/iPhone com "Inteligência Artificial no Mac": `/online/informatica/macbook-iphone-aulas-personalizadas-usar-seu-apple-autonomia-basico-avancado-2466561`
- R$ 50/h – Adobe, Canva e IA para imagem e vídeo: `/online/desenho-web/aulas-programas-adobe-photoshop-ilustrator-premiere-after-effects-canva-imagem-video-automacao-desenvolvimento-2400386`
- R$ 300/h – escrita científica com IA (orientação acadêmica): `/online/escritura/orientacao-academica-revisao-critica-padronizacao-abnt-verificacao-plagio-2069078`

(prefixo de todos: `https://www.suasaulasparticulares.com.br`)

## (c) Procurei e não encontrei / bloqueado

**Superprof (superprof.com.br) – BLOQUEADO, nenhum preço registrado.**
- curl devolve HTTP 403 com página de captcha DataDome ("Please enable JS and disable any ad blocker"); Playwright (Chromium) também recebe 403 com o mesmo captcha; WebFetch devolve HTTP 405. Não tentei contornar o captcha.
- Tentei: `/aulas/inteligencia-artificial/rio-de-janeiro/`, `/aulas/chatgpt/online/`, um perfil individual e `/todas-as-materias.html`.
- Internet Archive e Common Crawl não são alcançáveis deste ambiente (conexão recusada); a API de disponibilidade do Archive só tem cópia de 2021 da listagem de IA do Rio e nenhuma da listagem de ChatGPT online.
- O blog do Superprof abre, mas os 7 artigos sobre IA só mostram professores de reforço escolar, informática e redes sociais, sem cidade nem link de perfil.
- Só `robots.txt` e os sitemaps abrem. Pelo sitemap, estas listagens existem e ficam para conferência manual num navegador:
  - ChatGPT: `/aulas/chatgpt/rio-de-janeiro/`, `/aulas/chatgpt/niteroi-rio-de-janeiro/`, `/aulas/chatgpt/volta-redonda-rio-de-janeiro/`, `/aulas/chatgpt/municipio-rio-de-janeiro/`, `/aulas/chatgpt/online/` (2 páginas), `/aulas/chatgpt/sao-paulo/`, `/aulas/chatgpt/belo-horizonte-minas-gerais/` (47 listagens de ChatGPT no total).
  - Inteligência artificial: `/aulas/inteligencia-artificial/rio-de-janeiro/` (2 páginas), `/aulas/inteligencia-artificial/niteroi-rio-de-janeiro/`, `/aulas/inteligencia-artificial/petropolis-rio-de-janeiro/`, `/aulas/inteligencia-artificial/volta-redonda-rio-de-janeiro/`, `/aulas/inteligencia-artificial/online/` (9 páginas) (238 listagens no total).
  - Perfis que a busca na web devolveu e que parecem ser do Rio ou do RJ (não abertos, não verificados):
    - `https://www.superprof.com.br/especialista-sistemas-analista-implantacao-ensina-como-usar-chatgpt-trabalho-com-metodologia-pratica-focada.html`
    - `https://www.superprof.com.br/ofereco-aulas-praticas-personalizadas-sobre-inteligencia-artificial-para-todos-niveis-chatgpt-claude-perplexity-notebook.html`
    - `https://www.superprof.com.br/aprenda-usar-chatgpt-forma-estrategica-criativa-ensino-personalizar-chat-criar-prompts-incriveis-desbloquear-ideias.html`
    - `https://www.superprof.com.br/professor-tecnologia-ensina-chatgpt-prompt-engineering-com-metodologia-pratica-personalizada.html` (Volta Redonda)
  - NÃO VERIFICADO, não usar como dado: os resumos automáticos da busca citaram média de R$ 88/h para ChatGPT online e para IA no Brasil, R$ 60 em Volta Redonda, e perfis do Rio entre R$ 75/h e R$ 150/h. Nada disso foi visto em página aberta, por isso não está no JSONL.

**Profes (profes.com.br):** redireciona (301) para `www.superprof.com.br`, com o mesmo bloqueio.

**Outras plataformas tentadas sem resultado:**
- TeacherOn (`teacheron.com/tutors-in-rio_de_janeiro`): HTTP 403.
- OLX (`olx.com.br/servicos?q=aula chatgpt`), Workana, Fiverr (`br.fiverr.com/search/gigs?query=aula chatgpt`): HTTP 403.
- Classgap: não tem versão brasileira (`/pt-br` redireciona para `/en`); preços em euro ou dólar.
- Cronoshare: `/quanto-custa/aulas-inteligencia-artificial` cai no índice geral; não há guia de preço para IA nem preço por professor.
- GetNinjas: abre, mas não publica preço por profissional.
- Vintepila (`/servicos/?q=chatgpt`): só serviços (prompts, design), nenhuma aula particular de IA.
- Domínios que não respondem (502 no gateway): `tusclasesparticulares.com.br`, `suaaulaparticular.com.br`, `apprentus.com.br`, `br.amazingtalker.com`, `corujito.com.br`, `buscaprof.com.br`, `encontreumprofessor.com.br`.

**Buscas na web feitas (WebSearch):** "aulas particulares de inteligência artificial ChatGPT para iniciantes professor particular R$/h"; "superprof aulas de ChatGPT Rio de Janeiro professor particular"; "preply professores de inteligência artificial online aulas particulares ChatGPT"; "tusclasesparticulares Brasil aulas particulares inteligência artificial ChatGPT professores preço"; "classgap professores online inteligência artificial ChatGPT"; "teacheron professor particular inteligência artificial ChatGPT Rio de Janeiro"; "aula particular ChatGPT inteligência artificial para leigos idosos valor da aula"; busca restrita a suasaulasparticulares.com.br com "Rio de Janeiro". Fora do Superprof e da Suas Aulas Particulares, nenhuma devolveu anúncio de professor com preço.

**Não encontrado em nenhuma fonte aberta:** professor do Rio ou do estado do RJ com preço; aula particular de criação de slides com IA (Gamma, Canva IA) como oferta principal; preço por pacote (todas as ofertas são por hora ou por aula).
