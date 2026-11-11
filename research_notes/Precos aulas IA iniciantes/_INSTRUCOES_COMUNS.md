# Instruções comuns aos pesquisadores (ler inteiro antes de começar)

## Para que serve
O usuário vai precificar um serviço real: acompanhamento individual, online (Zoom), 3 encontros de 1h30 (4h30 no total), para um adulto iniciante em tecnologia que quer usar IA no dia a dia e criar slides com IA. Não é mentoria para empresas nem curso de programação. Ele precisa de PREÇOS PUBLICADOS no Brasil, com link, de 2025 e 2026. Data de hoje: 11/11/2026.

## As cinco categorias (não misturar)
1. Aula particular de informática básica para adultos
2. Aula particular de IA ou ChatGPT para iniciantes
3. Mentoria individual de IA para profissionais autônomos
4. Oficina ou aula ao vivo em grupo sobre IA (preço por pessoa)
5. Curso gravado de IA para iniciantes ou de criação de slides com IA

## Regra de ouro
- Só registre um preço que você VIU na página que abriu (HTML baixado, página renderizada ou resultado de WebFetch). Nunca registre preço vindo só de resumo de busca, de memória ou de dedução.
- Cada registro precisa de um trecho LITERAL da página que contenha o preço (campo `evidencia`). Sem trecho literal, não registre.
- Não estime, não complete, não converta. Se a duração não estiver na página, deixe `duracao_horas` como null. As conversões para R$/hora serão feitas depois por outra pessoa.
- Se a página pedir login, bloquear (403, captcha) ou não mostrar preço ("sob consulta", "peça orçamento"), anote isso na seção "Não encontrado / bloqueado" e siga em frente.
- Um registro por oferta (um professor, um evento, um curso). Não repita a mesma oferta.
- Preços de 2025 ou 2026 apenas. Se a página tiver data (do evento, da publicação), registre. Evento já realizado em 2025/2026 vale, marcando a data.
- Linguagem neutra. Nada de dados pessoais além do que a página pública de oferta mostra (primeiro nome do professor basta; não registre telefone nem e-mail).

## Ferramentas
WebSearch, WebFetch, curl e, para páginas que dependem de JavaScript, Playwright em Node (`require('playwright')`, `chromium.launch()` sem opções; não rode "playwright install"). Guarde o HTML ou texto bruto das páginas de onde saiu cada preço em `/tmp/claude-0/-home-user-CAC/1394b4b1-661e-52d9-bbb6-f0c86e5d4e35/scratchpad/precos/<seu_arquivo>/` para auditoria.

## O que entregar (dois arquivos, na pasta `/home/user/CAC/research_notes/Precos aulas IA iniciantes/`)
1. `<nome>.jsonl`: uma linha JSON por preço, com EXATAMENTE estas chaves:
   - `categoria` (1 a 5)
   - `fonte` (ex.: "Superprof", "Sympla", "Senac RJ")
   - `titulo` (nome da oferta ou "Prof. Fulano – informática básica")
   - `cidade` (cidade do professor/evento; null se não informada)
   - `uf` (sigla; null se não informada)
   - `modalidade` ("individual" ou "grupo")
   - `canal` ("online", "presencial" ou "ambos")
   - `duracao_horas` (número total de horas a que o preço se refere; para preço "por hora" use 1; null se a página não disser)
   - `duracao_texto` (como a página descreve, ex.: "3 encontros de 2h", "por hora", "curso de 20h")
   - `preco_publicado` (texto como aparece, ex.: "R$ 80/h", "R$ 297,00", "12x de R$ 29,70")
   - `preco_valor_rs` (número em reais do preço cheio à vista a que `duracao_horas` se refere; se só houver parcelado, o total das parcelas e diga isso em `observacao`)
   - `unidade_preco` ("por hora", "por aula", "pacote", "curso", "ingresso", "mensalidade")
   - `gratuito` (true/false)
   - `publico_alvo` (como a página descreve; null se não disser)
   - `url` (link direto da página onde o preço aparece)
   - `data_consulta` ("2026-11-11")
   - `data_oferta` (data do evento/publicação se visível; senão null)
   - `evidencia` (trecho literal da página com o preço, até 200 caracteres)
   - `observacao` (qualquer ressalva: preço promocional, taxa extra, primeira aula grátis, pacote etc.)
2. `<nome>.md`: resumo curto com (a) quantos registros por categoria e por nível geográfico (cidade do Rio, restante do estado do RJ, restante do Sudeste, restante do Brasil, sem cidade informada), (b) como você coletou em cada fonte (URLs de listagem, método), (c) lista "Procurei e não encontrei / bloqueado", com as buscas feitas e as URLs tentadas.

Ao terminar, responda com um resumo de até 15 linhas: quantos registros, por categoria e nível geográfico, e o que ficou sem dado. Não invente para preencher cota: poucos registros verificados valem mais que muitos duvidosos.
