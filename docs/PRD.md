# PRD: Caderninho de Contas

App web de treino de matemática para crianças, inspirado no método Kumon.
Versão do documento: 0.2 (baseada no protótipo `index.html`)

---

## 1. Resumo

O Caderninho de Contas é um app em HTML, pensado para celular, que treina soma, subtração e multiplicação por meio de folhas de 10 contas medidas por **acerto e tempo**. A criança só sobe de nível quando faz 3 folhas seguidas, acertando tudo dentro de um tempo-meta. O app nunca diz "você errou": ele mostra quantas contas estão certas, destaca as que precisam de revisão e deixa a criança corrigir até acertar tudo. O progresso é salvo no próprio aparelho, com backup por código.

## 2. Problema e oportunidade

- A criança está consolidando soma, tem alguma dificuldade em subtração e acabou de ser introduzida à multiplicação (tabuadas do 1 ao 5).
- Falta um treino curto, repetível e progressivo, que meça fluência (precisão + velocidade) e não apenas "fazer a conta".
- Apps de matemática comuns costumam depender de feedback de erro ("errado!"), pontuação por volume e distrações. O objetivo aqui é o oposto: foco, domínio e confiança.

## 3. Público e contexto de uso

| Item | Descrição |
|---|---|
| Usuário principal | Criança em alfabetização matemática (perfil de referência: soma fácil, subtração com alguma dificuldade, multiplicação sendo introduzida) |
| Usuário secundário | Pais/responsáveis (acompanham a evolução, ajustam níveis, fazem backup) |
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
- Tempo total médio por folha por nível, em queda ao longo das repetições.
- Taxa de acertos na 1ª entrega, em alta ao longo das repetições.
- Níveis vencidos por semana.
- Taxa de abandono de folha (saída no meio).

## 5. Fora de escopo (v1)

- Contas de login, nuvem, sincronização entre aparelhos.
- Ranking ou competição entre crianças (a competição é só do aluno consigo mesmo).
- Divisão, frações, problemas de texto.
- Anúncios, compras no app, coleta de dados pessoais.
- Múltiplos perfis (candidato à v2).

## 6. Princípios de produto

1. **Domínio antes de avanço:** 3 folhas seguidas com 100% de acertos dentro do tempo-meta.
2. **Nunca dizer "errou":** feedback sempre positivo e orientado à ação. Palavras proibidas na interface: *errou, errado, erro, incorreto, falhou, perdeu*. Cor de revisão: âmbar (nunca vermelho).
3. **Competir consigo mesmo:** recordes de tempo próprio, sem comparação com terceiros.
4. **Pouca distração:** visual limpo, estilo folha de caderno, sem personagens ou animações excessivas.
5. **Pais no controle:** ajustes de nível e backup ficam na Área dos pais.

## 7. Trilhas e níveis

Cada folha tem **10 contas** sorteadas dentro do intervalo do nível. O tempo-meta é de **1:30 por folha** (tempo total, incluindo correções) e vale para todos os níveis. Para subir de nível, a criança precisa fazer **3 folhas seguidas, cada uma com 10/10 e dentro do tempo-meta**.

### Soma (resultado da conta)
| Nível | Resultados |
|---|---|
| 1 | até 20 |
| 2 | de 21 a 40 |
| 3 | de 41 a 60 |
| 4 | de 61 a 80 |
| 5 | de 81 a 100 |

### Subtração (valor de onde se tira)
| Nível | Primeiro número |
|---|---|
| 1 | até 20 |
| 2 | de 21 a 40 |
| 3 | de 41 a 60 |
| 4 | de 61 a 80 |
| 5 | de 81 a 100 |

O resultado nunca é negativo.

### Multiplicação
| Nível | Conteúdo |
|---|---|
| 1 | Tabuadas do 1, 2 e 3 |
| 2 | Tabuadas do 4, 5 e 6 |
| 3 | Tabuadas do 7, 8 e 9 |
| 4 | Tabuada do 10 e todas as tabuadas misturadas |

Cada tabuada vai de 1 a 10 (por exemplo, a do 3 vai de 3 × 1 a 3 × 10).

Observações:
- A meta de 1:30 é uma estimativa inicial e deve ser calibrada com uso real (ponto em aberto 1).
- Cada folha sorteia contas novas dentro do nível. A repetição que constrói fluência acontece entre folhas: a criança refaz o nível até dominar.
- Na multiplicação, a ordem dos fatores é sorteada (3 × 4 ou 4 × 3). As duas ordens podem aparecer na mesma folha, mas a mesma conta idêntica nunca se repete.
- Folha fora da meta zera a contagem de folhas rápidas do nível (3 seguidas). A mensagem é sempre positiva.
- Quando a trilha é concluída, a criança pode **treinar** o último nível (sem pontos e sem avanço).

## 8. Fluxos principais

### 8.0 Escolha de nível
Ao tocar em uma trilha na tela inicial, abre a lista de níveis dessa trilha, com três estados (cor e ícone, para não depender só da cor):
- **Verde (✓):** nível já vencido. Pode ser treinado de novo, em modo treino (sem pontos e sem mexer na contagem de folhas rápidas).
- **Azul (▶):** nível atual, o único que conta para subir. Mostra o progresso de folhas rápidas (X de 3).
- **Cinza (🔒):** nível bloqueado. Só abre quando a criança passa pelo nível azul.

Trilha concluída: todos os níveis ficam verdes. A tela de resultado tem o botão "Escolher nível" para voltar a essa lista.

### 8.1 Folha de exercícios
1. A criança escolhe um nível na lista (8.0). O cronômetro inicia.
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
2. Para cada trilha, em ordem (Soma, Subtração, Multiplicação), o teste apresenta etapas de **4 contas**, uma por vez, do nível 1 em diante.
3. A etapa é aprovada se houver **≥ 3 acertos** e tempo ≤ **50% do tempo-meta** da folha (45 s).
4. Aprovou: vai para a etapa seguinte. Não aprovou: a trilha começa nesse nível e o teste passa para a próxima trilha. Se aprovou todas, a trilha fica concluída.
5. "Pular" conta como não respondida. Não há feedback de certo/errado durante o teste, e o cronômetro não aparece na tela.
6. "Parar" salva as trilhas já testadas e mantém as demais como estavam.
7. A tela final lista o ponto de partida de cada trilha.
8. Os pais podem sobrescrever qualquer nível na Área dos pais.

### 8.3 Resultado da folha
| Situação | Mensagem | Efeito |
|---|---|---|
| 10/10 dentro da meta, 1ª ou 2ª folha rápida | "Folha rápida! Faltam X folhas em até 1:30 para subir de nível." | Soma 1 à contagem de folhas rápidas |
| 10/10 dentro da meta, 3ª folha rápida seguida | "Você subiu de nível!" | Sobe de nível, ganha pontos, contagem zera |
| 10/10 fora da meta | "Para subir de nível, faça 3 folhas seguidas em até 1:30. A contagem recomeça agora. Vamos juntos!" | Fica no nível, contagem zera |
| Modo treino (trilha concluída) | "Treino concluído!" | Sem pontos |

A tela de resultado mostra: estrelas, 1ª entrega (acertos e tempo), tempo total, meta da folha, selo de recorde (quando houver) e pontos ganhos. Na tela inicial, cada trilha mostra o progresso de folhas rápidas (3 marcadores).

### 8.4 Área dos pais
- Resumo: folhas feitas, níveis vencidos, pontos.
- Apelido da criança (opcional, até 20 caracteres).
- Ajuste manual do nível de cada trilha (zera a contagem de folhas rápidas).
- Últimas 12 folhas (data, nível, acertos e tempo da 1ª entrega, tempo total, estrelas, indicador de avanço).
- Backup: gerar código, copiar, importar (com confirmação).
- Apagar tudo (com confirmação).

## 9. Regras de pontuação

- **Pontos só ao subir de nível:** 100 base + 10 por estrela acima de 1 + 20 se bateu o recorde de tempo naquele nível. Valem as estrelas e o recorde da 3ª folha rápida.
- **Estrelas por folha concluída:**
  - 3: 10/10 na 1ª entrega e total dentro da meta
  - 2: total dentro da meta, mas com correções
  - 1: concluiu fora da meta
- **Recorde:** tempo total menor que o melhor anterior do mesmo nível (só conta se já havia um tempo registrado).
- **Tempo da 1ª entrega** é registrado para mostrar evolução, mas **o critério de folha rápida usa o tempo total**.

## 10. Requisitos funcionais

| ID | Requisito | Prioridade |
|---|---|---|
| RF-01 | Gerar 10 contas aleatórias por folha, conforme o nível, sem conta idêntica repetida (3 × 4 e 4 × 3 podem aparecer juntas) | Alta |
| RF-02 | Teclado numérico próprio, com apagar e confirmar | Alta |
| RF-03 | Cronômetro com pausa em segundo plano e no feedback | Alta |
| RF-04 | Avaliação de todas as contas a cada conferência | Alta |
| RF-05 | Destaque das contas a revisar sem revelar a resposta | Alta |
| RF-06 | Regra de avanço: 3 folhas seguidas com 100% de acertos e tempo total ≤ 1:30; folha fora da meta zera a contagem | Alta |
| RF-07 | Pontos, estrelas e recorde de tempo | Alta |
| RF-08 | Histórico de folhas (últimas 300) | Alta |
| RF-09 | Salvamento local e restauração ao abrir | Alta |
| RF-10 | Teste de nível por trilha | Alta |
| RF-11 | Backup por código (exportar/importar) com validação | Alta |
| RF-12 | Ajuste manual de nível pelos pais | Média |
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

Armazenado em `localStorage`, chave `caderninho-contas-v2`. A versão 2 (níveis por faixa) não migra dados da v1 (fases antigas): o formato de backup `CADERNINHO1:` é rejeitado.

```json
{
  "v": 2,
  "name": "apelido",
  "points": 0,
  "placed": false,
  "lv": { "add": 0, "sub": 0, "mul": 0 },
  "st": { "add": 0, "sub": 0, "mul": 0 },
  "best": { "add2": 140 },
  "hist": [
    { "d": 1760000000000, "t": "add", "L": 2, "f": 8, "ft": 130, "tt": 185, "r": 2, "s": 2, "a": 1, "p": 110 }
  ]
}
```

| Campo | Significado |
|---|---|
| `lv[trilha]` | Índice do nível atual (0 a N-1). Valor igual a N = trilha concluída |
| `st[trilha]` | Folhas rápidas seguidas no nível atual (0 a 2) |
| `best["<trilha><nível>"]` | Melhor tempo total (s) naquele nível |
| `hist[].d` | Timestamp |
| `hist[].t` / `L` | Trilha (`add`, `sub`, `mul`) e nível (índice) |
| `hist[].f` / `ft` | Acertos e tempo (s) na 1ª entrega |
| `hist[].tt` | Tempo total (s) |
| `hist[].r` | Número de entregas/conferências na folha |
| `hist[].s` | Estrelas (1 a 3) |
| `hist[].a` | 1 se subiu de nível |
| `hist[].p` | Pontos ganhos |

**Backup:** `CADERNINHO2:` + Base64 do JSON (UTF-8). A importação valida o prefixo e passa o conteúdo por `sanitize()` (tipos, limites de nível, tamanho do histórico e faixas numéricas de cada campo: estrelas 1 a 3, acertos 0 a 10, tempos até 24 h, pontos por folha até 1000).

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
- Início com as 3 trilhas, progresso por nível, folhas rápidas e pontos.
- Folha de 10 contas, teclado próprio, cronômetro, fluxo de entrega e correção.
- Regras de avanço, estrelas, pontos e recorde.
- Teste de nível adaptativo.
- Área dos pais (resumo, apelido, ajuste de nível, histórico, backup, reset).
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
8. As 3 folhas rápidas são seguidas (uma folha lenta zera a contagem) ou acumuladas? Hoje são seguidas; avaliar se zerar desmotiva a criança.
9. A meta única de 1:30 serve para todos os níveis? Níveis altos de soma e subtração (81 a 100) podem exigir meta maior.

## 17. Roadmap sugerido

**v0.2: validação e ajustes**
- Testar com a criança, coletar tempos reais e recalibrar metas.
- Ajustes de UX conforme observação (tamanho de toque, legibilidade, ritmo).

**v0.3: robustez**
- Testes automatizados da lógica (geração de contas, avanço, teste de nível, import/export).
- Separar o código em módulos (dados dos níveis, lógica, UI).
- PWA: instalável e offline.

**v1.0**
- Múltiplos perfis.
- Gráfico de evolução na Área dos pais (tempo por nível ao longo do tempo).
- Exportação/importação por arquivo.
- Novos conteúdos (divisão, contas com dois fatores, etc.).

**Futuro (exige revisão de privacidade)**
- Sincronização em nuvem e relatórios para os pais.

## 18. Critérios de aceite (v1)

- [ ] Uma folha gera 10 contas válidas, sem conta idêntica repetida, dentro do domínio do nível.
- [ ] Nenhum texto da interface usa as palavras proibidas do guia de tom.
- [ ] A conta marcada para revisão nunca exibe a resposta correta.
- [ ] O nível só sobe após 3 folhas seguidas com 10/10 e tempo total ≤ 1:30; uma folha fora da meta zera a contagem.
- [ ] Os pontos são concedidos uma única vez por avanço.
- [ ] O progresso persiste após fechar e reabrir o app.
- [ ] Exportar e importar em outro aparelho restaura pontos, níveis, folhas rápidas e histórico.
- [ ] O teste de nível define os níveis iniciais e permite ajuste manual.
- [ ] A lista de níveis mostra verde (feito), azul (atual) e cinza (bloqueado); níveis cinza não abrem folha; treinar um nível verde não altera pontos nem a contagem de folhas rápidas.
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

- O protótipo está em arquivo único para facilitar a validação. Ao migrar, sugere-se separar: `data/levels.js` (trilhas, níveis e metas), `core/` (geradores, avaliação, pontuação, teste de nível), `storage.js` (persistência, backup e sanitização) e `ui/` (telas).
- A meta de tempo (`GOAL`), o número de folhas seguidas (`NEED`) e as faixas de cada nível estão centralizados no topo do script (`GOAL`, `NEED`, `TRACKS`); é o primeiro lugar a ajustar durante a calibração.
- A lógica de avanço está em `finishSheet()`, o teste de nível em `answerQ()`/`endTest()` e a sanitização em `sanitize()`.
- Manter a regra de copy (seção 12) como lint: um teste simples que procura as palavras proibidas nos textos da interface.
- Se evoluir para framework (React, Vue, Svelte), manter a persistência com a mesma chave e o mesmo formato para não perder backups existentes.
