# Categoria 5 – cursos gravados de IA para iniciantes e de slides com IA

Consulta em 11/11/2026. Arquivo de dados: `cursos_gravados_cat5.jsonl` (63 linhas, todas categoria 5).
Evidências brutas (HTML e texto de cada página): `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/gravados/` (subpastas `hotmart/`, `hotmart_search/`, `outros/`, `buzzero/`).

## (a) Quantos registros

| Recorte | Registros |
|---|---|
| Categoria 5, total | 63 |
| Subgrupo "IA iniciantes" (ChatGPT, IA no dia a dia, prompts, Copilot, Gemini) | 45 |
| Subgrupo "Slides com IA" (Gamma, PowerPoint + IA, apresentações com ChatGPT) | 17 |
| Assinatura que cobre os dois (Alura) | 1 |

O subgrupo está no início do campo `observacao`, entre colchetes, porque o esquema não tem chave própria para isso.

Por nível geográfico: cidade do Rio 0, restante do RJ 0, restante do Sudeste 0, restante do Brasil 0, **sem cidade informada 63** (cursos gravados online; nenhuma página informa cidade).

Por fonte: Hotmart 54, Descomplica 3, Alura 1, Rocketseat 1, Conquer 1, EBAC 1, Hashtag Treinamentos 1, Unova Cursos 1.

Por tipo de preço:

| Subgrupo | Curso avulso pago | Assinatura anual | Gratuito |
|---|---|---|---|
| IA iniciantes (45) | 39, de R$ 9,99 a R$ 1.499, mediana R$ 99 | 4 (R$ 59,90, R$ 97, R$ 659,10 e R$ 2.268) | 2 |
| Slides com IA (17) | 13, de R$ 15 a R$ 597, mediana R$ 67 | 4 (R$ 69,90, R$ 97, R$ 397 e R$ 778,20) | 0 |
| Alura (os dois) | – | 1 (12 x R$ 122 = R$ 1.464 de tabela; 12 x R$ 85,40 na promoção) | – |

Só 13 dos 63 registros têm `duracao_horas` preenchida; os demais ficam `null` porque a página não informa carga horária.

## Ressalvas que afetam a leitura dos números

- **Hotmart domina a amostra (54 de 63).** São cursos de produtores pequenos, a maioria sem avaliações exibidas. Isso puxa a mediana para baixo. Os preços de escolas conhecidas (Hashtag, EBAC, Descomplica, Conquer, Alura, Rocketseat) ficam entre R$ 448 e R$ 2.268.
- **Preço da Hotmart lido no checkout, não na vitrine.** O acesso saiu de IP dos EUA e a vitrine mostrava US$. Em cada produto abri `pay.hotmart.com/<código>?off=<oferta>` e escolhi Brasil no seletor "Alterar país" da própria página; o valor em R$ é o que o checkout exibiu. Nenhum checkout mostrou "de/por", então registrei como preço de lista.
- **"Cursos Online" na Hotmart não garante vídeo.** Descartei os que a descrição revela serem e-book ou ao vivo, mas em vários a descrição é curta e não confirma o formato.
- **`modalidade` = "individual" em todos**, no sentido de estudo individual no próprio ritmo (o esquema só admite "individual" ou "grupo").
- **`unidade_preco` = "anual"** nas assinaturas de 12 meses (Alura, Rocketseat, Conquer e 6 ofertas da Hotmart com "/ ano"). Não usei "mensalidade" porque nenhuma página vende mês avulso.
- **Preço cheio e promocional:** `preco_valor_rs` traz o preço cheio de tabela quando a página mostra os dois (Hashtag, Alura). Na Rocketseat a página só mostra o promocional, e é ele que está em `preco_valor_rs`; isso está dito em `preco_publicado` e em `observacao`.
- **Totais de parcelas:** em Alura e Descomplica não há valor à vista; `preco_valor_rs` é o total das parcelas (na Descomplica o total aparece escrito na própria página).
- **Nomes:** no `titulo` reduzi produtores pessoa física ao primeiro nome e tirei a linha "Autor:" da `evidencia`.

## (b) Como coletei em cada fonte

**Hotmart (54 registros)**
- Listagem: `https://hotmart.com/pt-br/marketplace/produtos?q=<termo>`, com curl, lendo o JSON `__NEXT_DATA__` da página (24 resultados por busca; a página 2 quase sempre repete a 1).
- 57 termos, entre eles: chatgpt para iniciantes, chatgpt do zero, ia para iniciantes, ia no dia a dia, ia para leigos, ia generativa, engenharia de prompt, copilot, gemini, ia descomplicada, ia sem medo, ia melhor idade, slides com ia, apresentações com ia, gamma, gamma app, powerpoint ia, apresentações chatgpt.
- Cerca de 990 produtos distintos nas listagens. Filtrei por título, idioma PT_BR e formato "Cursos Online"; li a descrição e abri o checkout de 85 (2 não carregaram).
- Página do produto (descrição, data de publicação) por curl; checkout por Playwright, como descrito acima.
- Descartados depois de ler a descrição: e-books, pacotes de prompts, cursos de renda extra ou nicho profissional, cursos técnicos, e os ao vivo listados mais abaixo.

**Escolas e assinaturas (9 registros)**
- Alura: `https://www.alura.com.br/planos-cursos-online` com Playwright, clicando na aba "1 Ano". Carga do curso de Gamma em `https://www.alura.com.br/curso-online-gamma-criando-apresentacoes-com-ia`.
- Rocketseat: `https://www.rocketseat.com.br/one`, que redireciona para `/assinatura` (Playwright).
- Conquer: `https://escolaconquer.com.br/conquer-plus` e `https://escolaconquer.com.br/cursos-de-ia` (Playwright).
- EBAC: `https://ebaconline.com.br/letramento-em-ia` (Playwright); lista em `https://ebaconline.com.br/cursos-de-ia`.
- Hashtag Treinamentos: `https://www.hashtagtreinamentos.com/curso-ia` (Playwright).
- Descomplica: `https://descomplica.com.br/cursos-livres/` (curl; tabela de preços no HTML) e `https://descomplica.com.br/faculdade/ia-na-pratica/` (curso gratuito).
- Unova Cursos: `https://www.unovacursos.com.br/curso/chatgpt-para-iniciantes` (Playwright).

## (c) Procurei e não encontrei / bloqueado

- **Udemy: bloqueada, nenhum preço registrado.** Cloudflare devolveu 403 ("Executando verificação de segurança") em curl, em Playwright e no WebFetch. URLs tentadas: `https://www.udemy.com/courses/search/?q=chatgpt+para+iniciantes&lang=pt`, `https://www.udemy.com/pt/topic/chatgpt/`, `https://www.udemy.com/api-2.0/courses/?search=chatgpt&language=pt`, `https://www.udemy.com/course/chat-gpt-/`, `https://www.udemy.com/pt/course/inteligencia-artificial-para-iniciantes/`. A busca achou os cursos em português, mas sem preço: `/course/inteligencia-artificial-para-iniciantes/`, `/course/chatgpt-ia-formacao/`, `/course/chat-gpt-/`, `/course/curso-de-chatgpt-pratico-como-usar-o-chatgpt-corretamente/`, `/course/curso-completo-de-chatgpt-do-zero-ao-um/`, `/course/introducao-aos-prompts-de-chatgpt/`, `/course/chatgpt-mao-na-massa/`, `/course/descomplicando-a-inteligencia-artificial/`, `/course/chatgpt-curso-completo-p-iniciantes-zero-ao-avancado/`. Alguém com navegador no Brasil precisa abrir essas páginas.
- **Domestika: bloqueada.** 403 do CloudFront em curl e Playwright (`https://www.domestika.org/pt/courses/search?query=inteligência+artificial`). O WebFetch abriu a listagem, mas ela não mostra preço.
- **Coursera:** `https://www.coursera.org/learn/generative-ai-for-everyone?lang=pt` abre ("IA generativa para todos", 6 horas), mas só mostra "Inscreva-se gratuitamente", sem preço em reais. edX não foi consultado.
- **Kiwify:** não tem vitrine pública pesquisável; a busca restrita aos domínios kiwify só devolveu páginas institucionais. Nenhuma página de venda encontrada.
- **Eduzz:** a busca achou checkouts (`https://sun.eduzz.com/1767039`, `https://sun.eduzz.com/1529785`), mas um é e-book e o outro é curso técnico de chatbot; além disso o preço apareceu em US$. Nenhum registro.
- **G4:** `https://g4business.com/` não mostra preço de curso de IA.
- **PM3:** `https://pm3.com.br/cursos/` mostra só o Membership ("12X R$ 220,75 SEM JUROS"), voltado a gestão de produto; não há curso de IA para leigos com preço avulso. Não registrado.
- **Senac:** `https://www.sp.senac.br/cursos-livres/curso-de-inteligencia-artificial-descomplicada` devolveu 403 (Access Denied); pela busca é curso presencial de 4 horas, fora desta categoria.
- **Skillshare e LinkedIn Learning:** não consultados (assinaturas sem preço em reais nos resultados de busca).
- **Hotmart, checkout não abriu:** "Engenharia de Prompt" (código F105058573G) e "Curso de CHAT GPT para Iniciantes" (T101824908L) – o seletor de país não carregou; sem preço em R$.
- **Cursos de slides fora da Hotmart:** não achei escola com preço publicado para curso gravado de Gamma, Canva com IA ou Copilot no PowerPoint, além da Alura (por assinatura). Buscas: "slides com IA" / "apresentações com inteligência artificial" + Gamma + Canva + preço; "PowerPoint com IA" / "Copilot no PowerPoint" + "12x".

## Vistos com preço, mas deixados fora do JSONL

Preços lidos na página, mas a oferta não é curso gravado em vídeo ou o formato é incerto.

| Oferta | Preço visto | Por que ficou fora | URL |
|---|---|---|---|
| FindSkill.ai (196+ cursos de IA, entre eles "IA para Iniciantes" e "IA para fazer slides") | R$ 119 por 3 meses; anual R$ 24,92/mês; vitalício R$ 690 | Aulas parecem ser em texto ("8 aulas · 114 min"); a página não fala em vídeo | `https://findskill.ai/pt/courses/ia-para-iniciantes/` |
| Buzzero, "Curso de CHATGPT" | "Por: R$ 29,90 (Pagamento único)", 4 horas | Curso em slides de texto ("Slide 11 de 40") | `https://www.buzzero.com/administracao-e-negocios-2/tecnologia-da-informacao-11/curso-online-chatgpt-com-certificado-75448` |
| Conquer AI Plus Vitalício | "24x de: R$ 169 /mês ou 4.056 à vista" | Mesma oferta do plano anual já registrado | `https://escolaconquer.com.br/conquer-plus` |
| Prime Cursos, ChatGPT | Curso grátis; a página cita "certificado a partir de R$49,90" em outros cursos | Preço do certificado deste curso não aparece de forma literal | `https://www.primecursos.com.br/chatgpt/` |

## Ofertas AO VIVO encontradas no caminho (servem à categoria 4, não entraram aqui)

| Oferta | Preço visto | Formato na página | URL |
|---|---|---|---|
| Impacta, "IA para Todos" | "De: R$ 1.500 Por: R$ 1.197 à vista ou 12x de R$ 119" | "Curso online ao vivo, 16 horas"; para iniciantes | `https://ofertas.impacta.com.br/ia-para-todos/` |
| Hotmart, "ChatGPT Do Zero" | "3 x de R$ 247,34 / Ou R$ 742,00 à vista" | "8 horas de formação intensiva (5 encontros online ao vivo)" | `https://pay.hotmart.com/L103875412K?off=1sc6kjgd` |
| Hotmart, "Inteligência Artificial para iniciantes" | "3 x de R$ 178,40 / Ou R$ 499,90 à vista" | "Curso VIP e AO VIVO, carga horária de 16h/aula" | `https://pay.hotmart.com/Q105645412T?off=3dgl969q` |
| Hotmart, "Implementação Claude" | "12 x de R$ 72,09 / Ou R$ 697,00 à vista" | 5 aulas com datas marcadas (maio e junho) | `https://pay.hotmart.com/J105543694P?off=uxajd3q0` |

Os três preços da Hotmart acima foram lidos do mesmo modo que os demais (checkout com país Brasil).
