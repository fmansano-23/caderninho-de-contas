# PRD: Caderninho de Contas

App web de treino de matemática para crianças, inspirado no método Kumon.
Versão do documento: 0.1 (baseada no protótipo `index.html`)

---

## 1. Resumo

O Caderninho de Contas é um app em HTML, pensado para celular, que treina soma, subtração e multiplicação por meio de folhas de 10 contas medidas por **acerto e tempo**. A criança só avança de fase quando acerta tudo dentro de um tempo-meta. O app nunca diz "você errou": ele mostra quantas contas estão certas, destaca as que precisam de revisão e deixa a criança corrigir até acertar tudo. O progresso é salvo no próprio aparelho, com backup por código.

## 2. Problema e oportunidade

- A criança está consolidando soma, tem alguma dificuldade em subtração e acabou de ser introduzida à multiplicação (tabuadas do 1 ao 5).
- Falta um treino curto, repetível e progressivo, que meça fluência (precisão + velocidade) e não apenas "fazer a conta".
- Apps de matemática comuns costumam depender de feedback de erro ("errado!"), pontuação por volume e distrações. O objetivo aqui é o oposto: foco, domínio e confiança.

## 3. Público e contexto de uso

| Item | Descrição |
|---|---|
| Usuário principal | Criança em alfabetização matemática (perfil de referência: soma fácil, subtração com alguma dificuldade, multiplicação sendo introduzida) |
| Usuário secundário | Pais/responsáveis (acompanham a evolução, ajustam fases, fazem backup) |
| Dispositivo | Celular (mobile-first); deve funcionar também em tablet e desktop |
| Contexto | Sessões curtas (2 a 7 min por folha), em casa, com ou sem supervisão |
| Idioma | Português do Brasil |

## 4. Objetivos e métricas de sucesso

**Objetivos**
1. Treinar fluência em soma, subtração e multiplicação com progressão por domínio.
2. Manter a criança motivada sem usar mensagens negativas.
3. Dar aos pais visibilidade simples da evolução.
4. Funcionar sem conta, sem servidor e sem dados pessoais.

**Métricas (a medir com uso real)**
- Folhas concluídas por semana.
- Tempo total médio por folha por fase, em queda ao longo das repetições.
- Taxa de acertos na 1ª entrega, em alta ao longo das repetições.
- Fases vencidas por semana.
- Taxa de abandono de folha (saída no meio).

## 5. Fora de escopo (v1)

- Contas de login, nuvem, sincronização entre aparelhos.
- Ranking ou competição entre crianças (a competição é só do aluno consigo mesmo).
- Divisão, frações, problemas de texto.
- Anúncios, compras no app, coleta de dados pessoais.
- Múltiplos perfis (candidato à v2).

## 6. Princípios de produto

1. **Domínio antes de avanço:** 100% de acertos dentro do tempo-meta.
2. **Nunca dizer "errou":** feedback sempre positivo e orientado à ação. Palavras proibidas na interface: *errou, errado, erro, incorreto, falhou, perdeu*. Cor de revisão: âmbar (nunca vermelho).
3. **Competir consigo mesmo:** recordes de tempo próprio, sem comparação com terceiros.
4. **Pouca distração:** visual limpo, estilo folha de caderno, sem personagens ou animações excessivas.
5. **Pais no controle:** ajustes de fase e backup ficam na Área dos pais.

## 7. Trilhas e fases

Cada folha tem **10 contas**. O tempo-meta vale para o **tempo total** (incluindo correções).

### Soma
| Fase | Conteúdo | Meta |
|---|---|---|
| 1 | Soma até 5 | 2:00 |
| 2 | Soma até 10 | 2:30 |
| 3 | Soma até 20 (resultado de 11 a 20) | 3:30 |
| 4 | Soma até 50 | 5:00 |
| 5 | Soma até 100 | 6:00 |

### Subtração
| Fase | Conteúdo | Meta |
|---|---|---|
| 1 | Subtração até 5 | 2:30 |
| 2 | Subtração até 10 | 3:00 |
| 3 | Subtração até 20 | 4:00 |
| 4 | Subtração até 50 | 5:30 |
| 5 | Subtração até 100 | 6:30 |

### Multiplicação
| Fase | Conteúdo | Meta |
|---|---|---|
| 1 | Tabuadas do 1 e do 2 | 2:30 |
| 2 | Tabuadas do 3 e do 4 (+ revisão 1 e 2) | 3:00 |
| 3 | Tabuada do 5 (+ revisão 1 a 4) | 3:30 |
| 4 | Tabuadas do 6 e do 7 (+ revisão 1 a 5) | 4:00 |
| 5 | Tabuadas do 8, 9 e 10 (+ revisão 1 a 7) | 4:30 |
| 6 | Todas as tabuadas misturadas | 5:00 |

Observações:
- As metas são estimativas iniciais e devem ser calibradas com uso real. Todas ficam abaixo de 10 min.
- Nas fases com revisão, cerca de 70% das contas são do conteúdo novo e 30% das fases anteriores.
- Na multiplicação, a ordem dos fatores é sorteada (3 × 4 ou 4 × 3). As duas ordens podem aparecer na mesma folha (reforça a ideia de que a ordem não muda o resultado), mas a mesma conta idêntica nunca se repete. A repetição que constrói fluência acontece entre folhas: a criança refaz a fase, com contas sorteadas de novo, até dominar.
- Quando a trilha é concluída, a criança pode **treinar** a última fase (sem pontos e sem avanço).

## 8. Fluxos principais

### 8.1 Folha de exercícios
1. A criança toca em "Começar" (ou "Treinar") em uma trilha. O cronômetro inicia.
2. A tela mostra 10 contas em formato de folha de caderno e um teclado numérico próprio (evita o teclado do sistema cobrindo as contas). Respostas aceitam até 3 dígitos.
3. Ao preencher todas, o botão **Entregar** é habilitado.
4. O app avalia e mostra: "Você acertou X de 10!" (ou "Vamos juntos!" se 0). O cronômetro pausa durante a mensagem.
5. Contas corretas ficam travadas com ✓. As demais ficam em âmbar com ✎, sem revelar a resposta certa.
6. A criança altera apenas as contas destacadas e toca em **Conferir**. O app reavalia **todas** as contas. Repete até 10/10.
7. Ao fechar a folha, o app registra o histórico e exibe o resultado (ver 8.3).

Detalhes de interação:
- Tocar numa conta selecionada e digitar substitui o valor anterior (não concatena).
- O botão ✓ do teclado avança para a próxima conta pendente.
- O cronômetro pausa quando a aba/app vai para segundo plano.
- Botão **Sair** pede confirmação e descarta a folha (nada é salvo).
- O relógio muda para tom âmbar suave ao passar do tempo-meta (sem alerta sonoro, sem mensagem).

### 8.2 Teste de nível (placement)
1. Disponível no primeiro uso (banner na tela inicial) e depois como "Refazer teste de nível".
2. Para cada trilha, em ordem (Soma, Subtração, Multiplicação), o teste apresenta etapas de **4 contas**, uma por vez, da fase 1 em diante.
3. A etapa é aprovada se houver **≥ 3 acertos** e tempo ≤ **50% do tempo-meta** da fase.
4. Aprovou: vai para a etapa seguinte. Não aprovou: a trilha começa nessa fase e o teste passa para a próxima trilha. Se aprovou todas, a trilha fica concluída.
5. "Pular" conta como não respondida. Não há feedback de certo/errado durante o teste, e o cronômetro não aparece na tela.
6. "Parar" salva as trilhas já testadas e mantém as demais como estavam.
7. A tela final lista o ponto de partida de cada trilha.
8. Os pais podem sobrescrever qualquer fase na Área dos pais.

### 8.3 Resultado da folha
| Situação | Mensagem | Efeito |
|---|---|---|
| 10/10 dentro da meta | "Você subiu de fase!" | Avança a fase, ganha pontos |
| 10/10 fora da meta | "Mais uma rodadinha para ficar bem rápido e a gente sobe de fase" | Fica na fase |
| Modo treino (trilha concluída) | "Treino concluído!" | Sem pontos |

A tela de resultado mostra: estrelas, 1ª entrega (acertos e tempo), tempo total, meta da fase, selo de recorde (quando houver) e pontos ganhos.

### 8.4 Área dos pais
- Resumo: folhas feitas, fases vencidas, pontos.
- Apelido da criança (opcional, até 20 caracteres).
- Ajuste manual da fase de cada trilha.
- Últimas 12 folhas (data, fase, acertos e tempo da 1ª entrega, tempo total, estrelas, indicador de avanço).
- Backup: gerar código, copiar, importar (com confirmação).
- Apagar tudo (com confirmação).

## 9. Regras de pontuação

- **Pontos só ao avançar de fase:** 100 base + 10 por estrela acima de 1 + 20 se bateu o recorde de tempo naquela fase.
- **Estrelas por folha concluída:**
  - 3: 10/10 na 1ª entrega e total dentro da meta
  - 2: total dentro da meta, mas com correções
  - 1: concluiu fora da meta
- **Recorde:** tempo total menor que o melhor anterior da mesma fase (só conta se já havia um tempo registrado).
- **Tempo da 1ª entrega** é registrado para mostrar evolução, mas **o critério de avanço usa o tempo total**.

## 10. Requisitos funcionais

| ID | Requisito | Prioridade |
|---|---|---|
| RF-01 | Gerar 10 contas aleatórias por folha, conforme a fase, sem conta idêntica repetida (3 × 4 e 4 × 3 podem aparecer juntas) | Alta |
| RF-02 | Teclado numérico próprio, com apagar e confirmar | Alta |
| RF-03 | Cronômetro com pausa em segundo plano e no feedback | Alta |
| RF-04 | Avaliação de todas as contas a cada conferência | Alta |
| RF-05 | Destaque das contas a revisar sem revelar a resposta | Alta |
| RF-06 | Regra de avanço: 100% de acertos e tempo total ≤ meta | Alta |
| RF-07 | Pontos, estrelas e recorde de tempo | Alta |
| RF-08 | Histórico de folhas (últimas 300) | Alta |
| RF-09 | Salvamento local e restauração ao abrir | Alta |
| RF-10 | Teste de nível por trilha | Alta |
| RF-11 | Backup por código (exportar/importar) com validação | Alta |
| RF-12 | Ajuste manual de fase pelos pais | Média |
| RF-13 | Modo treino em trilha concluída | Média |
| RF-14 | Suporte a teclado físico (desktop) | Baixa |
| RF-15 | Tema claro e escuro automáticos | Baixa |

## 11. Requisitos não funcionais

- **Plataforma:** arquivo HTML único, sem build, sem backend.
- **Responsivo:** mobile-first (largura de referência 360 a 430 px), com suporte a *safe areas* (notch e barra inferior).
- **Acessibilidade:** alvos de toque ≥ 46 px, foco visível, contraste adequado, respeito a `prefers-reduced-motion`, rótulos nos botões só com ícone.
- **Desempenho:** carregamento rápido, sem dependências externas. A fonte Andika é servida localmente (`fonts/`, cerca de 0,9 MB), com fallback.
- **Robustez de armazenamento:** toda leitura/escrita em `localStorage` dentro de `try/catch`; se falhar, o app funciona na sessão e avisa os pais para usar o backup.
- **Offline:** funciona offline após carregar (a fonte é local e tem fallback). PWA é candidato à v2.

## 12. Experiência e visual

- Estilo **folha de caderno**: papel claro, linhas azuis suaves, margem rosada discreta.
- Paleta clean: azul como cor principal, verde para acerto, âmbar para revisão. Sem vermelho.
- Tipografia: **Andika** (desenhada para leitura infantil, com dígitos bem distinguíveis), hospedada junto do app em `fonts/` (licença SIL OFL), com fallback para fontes do sistema.
- Sem personagens, sons ou animações decorativas.
- Todos os textos usam apóstrofo e aspas tipográficos (’ “ ”) e os símbolos − e × nas contas.

### Guia de tom de voz (copy)
- Sempre positivo e orientado à próxima ação: "Vamos olhar essas 2 contas?", "Falta só 1 conta".
- Nunca usar: *errou, errado, erro, incorreto, falhou, perdeu*.
- Frases curtas e simples, sem ironia.

## 13. Modelo de dados

Armazenado em `localStorage`, chave `caderninho-contas-v1`.

```json
{
  "v": 1,
  "name": "apelido",
  "points": 0,
  "placed": false,
  "lv": { "add": 0, "sub": 0, "mul": 0 },
  "best": { "add2": 140 },
  "hist": [
    { "d": 1760000000000, "t": "add", "L": 2, "f": 8, "ft": 130, "tt": 185, "r": 2, "s": 2, "a": 1, "p": 110 }
  ]
}
```

| Campo | Significado |
|---|---|
| `lv[trilha]` | Índice da fase atual (0 a N-1). Valor igual a N = trilha concluída |
| `best["<trilha><fase>"]` | Melhor tempo total (s) naquela fase |
| `hist[].d` | Timestamp |
| `hist[].t` / `L` | Trilha (`add`, `sub`, `mul`) e fase (índice) |
| `hist[].f` / `ft` | Acertos e tempo (s) na 1ª entrega |
| `hist[].tt` | Tempo total (s) |
| `hist[].r` | Número de entregas/conferências na folha |
| `hist[].s` | Estrelas (1 a 3) |
| `hist[].a` | 1 se avançou de fase |
| `hist[].p` | Pontos ganhos |

**Backup:** `CADERNINHO1:` + Base64 do JSON (UTF-8). A importação valida o prefixo e passa o conteúdo por `sanitize()` (tipos, limites de fase, tamanho do histórico e faixas numéricas de cada campo: estrelas 1 a 3, acertos 0 a 10, tempos até 24 h, pontos por folha até 1000).

## 14. Privacidade e segurança (LGPD)

- Nenhum dado sai do aparelho: sem servidor, sem analytics, sem cookies de terceiros e sem chamadas a serviços externos (a fonte é hospedada localmente, para o navegador não enviar IP a terceiros).
- Único dado pessoal opcional: **apelido**. Orientar os pais a **não usar nome completo, sobrenome ou dados de identificação**.
- O código de backup contém o apelido: avisar para guardá-lo em local seguro.
- Importação trata o código como entrada não confiável (validação e normalização).
- Todo texto vindo do usuário (apelido) é escapado antes de ir para o HTML.
- Como o público é infantil, qualquer evolução futura que envolva conta, nuvem ou analytics exige revisão de privacidade e consentimento dos responsáveis antes de implementar.

## 15. Estado atual (protótipo)

Arquivo: `index.html` (HTML, CSS e JS em um único arquivo).

Implementado:
- Início com as 3 trilhas, progresso por fase e pontos.
- Folha de 10 contas, teclado próprio, cronômetro, fluxo de entrega e correção.
- Regras de avanço, estrelas, pontos e recorde.
- Teste de nível adaptativo.
- Área dos pais (resumo, apelido, ajuste de fase, histórico, backup, reset).
- Tema claro/escuro.

Limitações conhecidas:
- **Ainda não foi validado em aparelho real** com a criança.
- Metas de tempo ainda não calibradas.
- Um único perfil.
- Backup somente por texto (sem arquivo).
- Sem testes automatizados.

## 16. Pontos em aberto

1. Calibração das metas de tempo com uso real.
2. Exibir o cronômetro grande ou discreto/escondido (possível pressão sobre a criança).
3. Tamanho da folha (10 contas) e variação de formato (vertical, como o Kumon impresso).
4. Critério do teste de nível (≥ 3 de 4 e 50% do tempo-meta): ajustar após testes.
5. Necessidade de múltiplos perfis (irmãos).
6. Regras para evitar "forçar" resposta por tentativa e erro nas correções (ex.: limite de tentativas ou dica após N conferências).
7. Pontos por consistência (ex.: dias seguidos), sem punir ausência.

## 17. Roadmap sugerido

**v0.2: validação e ajustes**
- Testar com a criança, coletar tempos reais e recalibrar metas.
- Ajustes de UX conforme observação (tamanho de toque, legibilidade, ritmo).

**v0.3: robustez**
- Testes automatizados da lógica (geração de contas, avanço, teste de nível, import/export).
- Separar o código em módulos (dados das fases, lógica, UI).
- PWA: instalável e offline.

**v1.0**
- Múltiplos perfis.
- Gráfico de evolução na Área dos pais (tempo por fase ao longo do tempo).
- Exportação/importação por arquivo.
- Novos conteúdos (divisão, contas com dois fatores, etc.).

**Futuro (exige revisão de privacidade)**
- Sincronização em nuvem e relatórios para os pais.

## 18. Critérios de aceite (v1)

- [ ] Uma folha gera 10 contas válidas, sem conta idêntica repetida, dentro do domínio da fase.
- [ ] Nenhum texto da interface usa as palavras proibidas do guia de tom.
- [ ] A conta marcada para revisão nunca exibe a resposta correta.
- [ ] O avanço só ocorre com 10/10 e tempo total ≤ meta.
- [ ] Os pontos são concedidos uma única vez por avanço.
- [ ] O progresso persiste após fechar e reabrir o app.
- [ ] Exportar e importar em outro aparelho restaura pontos, fases e histórico.
- [ ] O teste de nível define as fases iniciais e permite ajuste manual.
- [ ] O teclado próprio nunca cobre a conta selecionada.
- [ ] A interface funciona em 360 px de largura, em modo claro e escuro.
- [ ] Sem falhas se o `localStorage` estiver indisponível (aviso e backup).

## 19. Plano de testes

**Lógica (automatizável)**
- Geradores: quantidade, faixa de valores, ausência de contas idênticas repetidas, `ans` coerente com a operação.
- Subtração nunca gera resultado negativo.
- Regra de avanço: combinações de acertos e tempo (dentro/fora da meta; 1ª entrega perfeita ou não).
- Cálculo de estrelas, pontos e recorde.
- Teste de nível: passa tudo, falha na primeira etapa, falha no meio, pular, parar no meio.
- Importação: código válido, prefixo inválido, JSON corrompido, valores fora de faixa.

**Manual (aparelho real)**
- Fluxo completo de uma folha com correções.
- Fuso de safe area (iPhone com notch, Android com barra de gestos).
- Troca de app no meio da folha (pausa do cronômetro).
- Tema escuro.
- Fechar e reabrir o navegador para checar persistência.

## 20. Notas para continuar na IDE

- O protótipo está em arquivo único para facilitar a validação. Ao migrar, sugere-se separar: `data/levels.js` (trilhas, fases e metas), `core/` (geradores, avaliação, pontuação, teste de nível), `storage.js` (persistência, backup e sanitização) e `ui/` (telas).
- As metas de tempo e as faixas de cada fase estão centralizadas no array `TRACKS`; é o primeiro lugar a ajustar durante a calibração.
- A lógica de avanço está em `finishSheet()`, o teste de nível em `answerQ()`/`endTest()` e a sanitização em `sanitize()`.
- Manter a regra de copy (seção 12) como lint: um teste simples que procura as palavras proibidas nos textos da interface.
- Se evoluir para framework (React, Vue, Svelte), manter a persistência com a mesma chave e o mesmo formato para não perder backups existentes.
