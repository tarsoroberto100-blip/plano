Plano de Teste — AgendaFácil

## Histórico de versões

| Versão | Data | Autor | Descrição |
| --- | --- | --- | --- |
| 1.0 | 03/11/2026 | Tarso | Versão inicial do plano |
| 1.1 | [dd/mm/aaaa] | Tarso | [Preencher depois da revisão por pares: o que foi corrigido] |

## 1. Identificação

| Campo | Valor |
| --- | --- |
| Identificador do plano | PT-AF-001 |
| Versão do plano | 1.0 |
| Sistema | AgendaFácil, aplicativo de agendamento da Barbearia Bigode Grosso |
| Versão em teste | 1.0 (candidata a lançamento) |
| Plataformas | Aplicativo Android, aplicativo iOS e versão web (balcão) |
| Documento de referência | `REQUISITOS-AgendaFacil.md` v1.0 (fonte da verdade) |
| Autor | Tarso |
| Data | 03/11/2026 |
| Lançamento previsto | Sexta-feira, 13/11/2026 |

## 2. Objetivo

Responder, até quinta-feira 12/11 às 17h, a uma pergunta: **a versão 1.0 pode ser lançada em 13/11?** Para isso, o ciclo de testes vai verificar que:

1. as regras de negócio RN01 a RN12 funcionam como descrito nos requisitos;
2. os requisitos não-funcionais RNF01 a RNF05 são atendidos;
3. nenhum defeito impede o cliente de fazer login, agendar ou cancelar, e os dados dos clientes estão protegidos (critério de lançamento do cliente, seção 6 dos requisitos).

O resultado final é uma recomendação de **liberar** ou **não liberar** a versão, com evidências.

## 3. Escopo (o que será testado)

- Regras de negócio RN01 a RN12 no aplicativo Android, no aplicativo iOS e na versão web do balcão (RN12).
- Requisitos não-funcionais RNF01 a RNF05.
- Os fluxos completos: cadastro → login → agendamento → lembrete → cancelamento → atendimento concluído ou não comparecimento no balcão.

## 4. Fora do escopo

| Item | Justificativa |
| --- | --- |
| Pagamento pelo aplicativo | Fora do escopo da versão 1.0 (requisitos, seção 5). A RN11 só mostra o valor, e isso é testado. |
| Avaliação dos barbeiros | Fora do escopo da versão 1.0 (requisitos, seção 5). |
| Venda de produtos | Fora do escopo da versão 1.0 (requisitos, seção 5). |
| Teste de invasão (pentest) | Exige especialista e mais tempo do que os 4 dias disponíveis. A RNF03 é testada só pelo acesso indevido entre clientes. Recomendado para uma versão futura. |
| Envio de mensagens a clientes reais e testes em produção | Os testes são feitos só na homologação, com dados fictícios. |
| Android abaixo da versão 10, iOS abaixo da 15 e navegadores fora de Chrome, Edge e Safari | Fora da RNF04. |

## 5. Itens a testar e prioridades

**Prioridades:** **Crítica** = ligada ao critério de lançamento do cliente (login, agendar, cancelar, dados protegidos); **Alta** = regra de negócio ou requisito com impacto direto no cliente ou em dinheiro; **Média** = impacto menor ou contornável.

| Item | Prioridade | Técnica | Testes principais (com valores) |
| --- | --- | --- | --- |
| RN01 — Cadastro | Crítica | Partição de equivalência e valor limite | Nome com 2 caracteres (recusa) e com 3 (aceita); celular com 10, 11 e 12 dígitos; celular sem DDD; e-mail vazio (aceita) e e-mail inválido. |
| RN02 — Login por código | Crítica | Valor limite e transição de estados | Código usado aos 4 min 59 s (aceita) e aos 5 min 01 s (recusa); 2 códigos errados + 1 certo (não bloqueia); 3 errados seguidos (bloqueia por 15 min); nova tentativa aos 14 min 59 s (ainda bloqueado) e aos 15 min 01 s (liberado); reutilizar código já usado. |
| RN03 — Horário de funcionamento | Crítica | Valor limite | Domingo e segunda não aparecem; terça a sábado, primeiro horário às 9h e nenhum horário depois do fechamento das 19h; nenhum horário entre 12h e 13h; primeiro horário da tarde às 13h. |
| RN04 — Antecedência | Crítica | Valor limite | 1 h 59 min de antecedência (recusa), 2 h 00 min e 2 h 01 min (aceita); 30 dias (aceita) e 30 dias + 1 min (recusa). |
| RN05 — Horários disponíveis | Crítica | Valor limite e tabela de decisão | Intervalos de 15 min; Corte (30 min) às 11h30 aparece e às 11h45 não; Corte + Barba (60 min) às 11h00 aparece e às 11h15 não; Pigmentação (45 min) às 11h15 aparece e às 11h30 não; Corte às 18h30 aparece e às 18h45 não (fechamento); horário já ocupado pelo mesmo barbeiro some; o mesmo horário continua livre para outro barbeiro. |
| RN06 — Escolha do barbeiro | Crítica | Tabela de decisão | Léo, Rafa e Duda cada um com a sua agenda; "Qualquer um" mostra a união dos horários livres dos três; só um barbeiro livre; os três ocupados (sem horário). |
| RN07 — Limite por cliente | Alta | Valor limite | 1 e 2 agendamentos futuros (aceita); 3º agendamento (recusa com mensagem clara); cancelar um e conseguir agendar outro; agendamento já concluído não conta no limite. |
| RN08 — Cancelamento | Crítica | Valor limite e tabela de decisão | Cancelar com 3 h 01 min e com 3 h 00 min de antecedência (gratuito); com 2 h 59 min (taxa de R$ 15,00); taxa somada ao próximo atendimento (Corte R$ 45,00 passa a R$ 60,00); cancelar duas vezes o mesmo agendamento; o horário cancelado volta a ficar livre. |
| RN09 — Lembretes | Alta | Teste de fluxo com tempo | Lembrete 24 h antes e outro 1 h antes, com tolerância de 5 min neste plano; agendamento cancelado não gera lembrete; agendamento feito com menos de 24 h de antecedência recebe só o lembrete de 1 h. |
| RN10 — Fidelidade | Alta | Valor limite | Após 9 Cortes concluídos o 10º é pago; após 10 concluídos o 11º é gratuito (R$ 0,00); Barba, Corte + Barba e Pigmentação não contam e nunca são gratuitos; "Cliente não compareceu" não conta; o ciclo recomeça depois do corte gratuito. |
| RN11 — Valor mostrado | Alta | Tabela de decisão | Valor correto de cada serviço (R$ 45,00, R$ 35,00, R$ 70,00, R$ 60,00); com taxa da RN08; com desconto da RN10; taxa e desconto no mesmo atendimento (regra não descrita, ver riscos). |
| RN12 — Painel do balcão | Alta | Funcional e transição de estados | A agenda do dia mostra os três barbeiros; marcar "Concluído" e "Cliente não compareceu"; o status muda e atualiza a fidelidade (RN10); atendente não vê dias sem atendimento. |
| RNF01 — Desempenho | Alta | Medição | 20 medições do carregamento da tela de horários em 4G: nenhuma acima de 2 s. |
| RNF02 — Carga | Alta | Teste de carga | 200 usuários simultâneos por 10 min (login, abrir horários e agendar), com 0 erros. |
| RNF03 — Privacidade (LGPD) | Crítica | Teste de acesso indevido | Cliente A tenta ver nome, celular e histórico do cliente B (alterando identificadores nas requisições e navegando pela agenda); a tela de horários ocupados não mostra quem agendou; testado no app e na web. |
| RNF04 — Compatibilidade | Alta | Matriz de plataformas | Fluxos de login, agendamento e cancelamento em Android 10, Android mais recente, iOS 15, iOS mais recente, e web em Chrome, Edge e Safari (duas últimas versões de cada). |
| RNF05 — Acessibilidade | Média | Teste manual com leitor de tela | Login, agendamento e cancelamento só com TalkBack (Android) e VoiceOver (iOS); fonte no tamanho máximo do aparelho sem cortar texto nem esconder botões. |

## 6. Abordagem

**Níveis de teste:** teste de sistema, de caixa-preta, na versão candidata instalada no ambiente de homologação, mais um teste de fumaça (smoke) inicial e uma regressão final.

**Tipos e técnicas:**

| Tipo | Técnicas | Itens |
| --- | --- | --- |
| Funcional | Partição de equivalência, valor limite, tabela de decisão, transição de estados | RN01 a RN12 |
| Fluxo ponta a ponta | Cenários completos do cliente e do atendente | Todos |
| Desempenho e carga | Medição em 4G e ferramenta de carga (ex.: k6 ou JMeter) | RNF01, RNF02 |
| Privacidade | Tentativas de acesso a dados de outro cliente | RNF03 |
| Compatibilidade | Matriz de aparelhos e navegadores | RNF04 |
| Acessibilidade | Manual com TalkBack e VoiceOver | RNF05 |
| Exploratório | 2 sessões de 60 min por analista | Agendamento e cancelamento |
| Regressão | Reexecução dos fluxos críticos na build final | Login, agendar, cancelar, RNF03 |

**Estimativa:** cerca de 100 casos de teste, cada um ligado a uma regra (RN) ou requisito não-funcional (RNF).

**Severidade dos defeitos:**

| Severidade | Definição |
| --- | --- |
| Crítico | Impede login, agendamento ou cancelamento, ou expõe dados de outro cliente. |
| Alto | Regra de negócio errada com impacto em dinheiro ou no cliente, sem impedir o fluxo (ex.: taxa ou corte gratuito errados). |
| Médio | Falha de uso menos frequente ou com contorno. |
| Baixo | Problema visual ou de texto, sem efeito na regra. |

**Testes que dependem de tempo** (RN02, RN04, RN08, RN09): serão feitos com ajuste de data e hora no ambiente de homologação ou com agendamentos criados em horários calculados. A equipe de desenvolvimento precisa liberar isso até 09/11.

## 7. Critérios de entrada e de saída

**Entrada** (para começar os testes, todos verdadeiros):

1. Versão 1.0 candidata instalada na homologação.
2. Teste de fumaça de 10 casos (login, agendar, cancelar, abrir o painel) com 100% aprovados.
3. Massa de dados fictícios carregada: 3 barbeiros, 4 serviços e pelo menos 10 clientes de teste.
4. Aparelhos e navegadores da matriz da RNF04 disponíveis.

**Saída** (para recomendar o lançamento, todos verdadeiros):

1. Todas as RN01 a RN12 e RNF01 a RNF05 têm pelo menos 1 caso executado.
2. 100% dos casos de prioridade Crítica e Alta executados e pelo menos 90% dos de prioridade Média.
3. Pelo menos 95% dos casos aprovados na regressão final.
4. **0 defeitos Críticos abertos, 0 defeitos Altos abertos e no máximo 5 defeitos Médios abertos** (com aceite do cliente).
5. 100% dos casos de privacidade (RNF03) aprovados.
6. RNF01: nenhuma das 20 medições acima de 2 s. RNF02: 200 usuários simultâneos por 10 min com 0 erros.
7. Todo defeito corrigido foi retestado, e a regressão de login, agendamento e cancelamento passou na build final.

**Ligação com o critério de lançamento do cliente:** os itens 4, 5 e 7 garantem que nenhum defeito impede login, agendamento ou cancelamento e que os dados estão protegidos (RNF03).

## 8. Critérios de suspensão e retomada

**Suspender os testes quando:**

- o teste de fumaça falhar em login ou agendamento;
- o ambiente de homologação ficar fora do ar por mais de 2 horas;
- houver 3 ou mais defeitos Críticos abertos ao mesmo tempo;
- for encontrado qualquer vazamento de dados de um cliente para outro (RNF03), que deve ser comunicado ao cliente na hora.

**Retomar quando:**

- uma nova build passar no teste de fumaça com 100% dos casos;
- o ambiente estiver estável por 30 minutos;
- os defeitos que causaram a suspensão estiverem corrigidos e retestados.

## 9. Entregáveis

| Entregável | Conteúdo | Data |
| --- | --- | --- |
| Plano de teste | Este documento (versões 1.0 e 1.1) | 03/11 e depois da revisão |
| Especificação de casos | Casos com ID, regra ligada (RN/RNF), passos, dados e resultado esperado | 06/11 |
| Registro de execução | Resultado de cada caso por plataforma e build | Diário, de 09/11 a 12/11 |
| Relatórios de defeito | ID, severidade, passos, evidência (print ou vídeo), plataforma e build | Ao encontrar |
| Relatório parcial | Situação dos testes e dos defeitos | 10/11, fim do dia |
| Resultados de carga e desempenho | Medições da RNF01 e relatório da RNF02 | 11/11 |
| Relatório final | Resumo, defeitos abertos, cumprimento dos critérios de saída e recomendação de liberar ou não liberar | 12/11, até 17h |

## 10. Ambiente de teste

| Item | Descrição |
| --- | --- |
| Servidor | Homologação: https://homolog.agendafacil.exemplo |
| Dados | **Somente dados fictícios**: 3 barbeiros (Léo, Rafa e Duda), 4 serviços, pelo menos 10 clientes de teste com celulares fictícios |
| Android | Android 10 (mínimo) e a versão mais recente disponível |
| iOS | iOS 15 (mínimo) e a versão mais recente disponível |
| Web | Chrome, Edge e Safari, nas duas últimas versões de cada |
| Rede | 4G (RNF01) e Wi-Fi |
| Ferramentas | Ferramenta de carga (ex.: k6 ou JMeter), planilha ou Markdown para casos e registro, gravação de tela |
| Mensageria | SMS (RN02) e WhatsApp (RN09) em modo de teste, sem envio a clientes reais |

## 11. Responsabilidades

| Pessoa | Papel | Responsabilidades |
| --- | --- | --- |
| Analista 1 [nome] | Líder de testes | RN01 a RN07, RNF01 e RNF02, relatório parcial e final |
| Analista 2 [nome] | Analista de testes | RN08 a RN12, RNF03, RNF04 e RNF05 |
| Equipe de desenvolvimento [nome do contato] | Correção | Corrigir defeitos: Crítico em até 4 horas úteis, Alto em até 1 dia útil. Liberar o ajuste de data e hora do ambiente até 09/11. |
| Barbearia Bigode Grosso [nome do contato] | Cliente | Esclarecer dúvidas dos requisitos e aprovar a liberação (go/no-go) |

## 12. Cronograma

| Data | Atividade |
| --- | --- |
| Qua 04/11 a sex 06/11 | Escrita dos casos de teste e preparação da massa de dados |
| Seg 09/11 (manhã) | Verificação do ambiente e teste de fumaça (critério de entrada) |
| Seg 09/11 (tarde) | Ciclo 1: RN01 a RN06 (login e agendamento) |
| Ter 10/11 | Ciclo 1: RN07 a RN12, RNF03 e RNF05. Relatório parcial no fim do dia. |
| Qua 11/11 | Carga e desempenho (RNF01, RNF02), compatibilidade (RNF04) e reteste dos defeitos corrigidos |
| Qui 12/11 | Regressão final, reteste, relatório final até 17h e decisão de liberar (go/no-go) |
| Sex 13/11 | Lançamento, se aprovado |

A janela de execução (09/11 a 12/11) usa toda a equipe disponível e termina um dia antes do lançamento.

## 13. Riscos

| # | Risco | Probabilidade | Impacto | Contingência |
| --- | --- | --- | --- | --- |
| R1 | Janela curta (4 dias, 2 analistas): defeitos achados no fim não dão tempo de corrigir e retestar | Alta | Alto | Executar primeiro os casos Críticos (RN01 a RN08 e RNF03); relatório parcial dia 10/11; se faltar tempo, recomendar adiar o lançamento. |
| R2 | Defeito Crítico em login ou agendamento nos últimos dias | Média | Alto | Correção em até 4 horas úteis e regressão focada nesses fluxos. |
| R3 | Testes de RN02, RN04, RN08 e RN09 dependem do relógio e ficam lentos ou inviáveis | Alta | Alto | Combinar com o desenvolvimento o ajuste de data e hora na homologação até 09/11. |
| R4 | Falta de aparelhos iOS 15 e de Mac para o Safari | Média | Médio | Usar simuladores ou serviço de aparelhos na nuvem; se não for possível, registrar a RNF04 como parcialmente testada no relatório. |
| R5 | Carga de 200 usuários simultâneos derruba ou deixa lenta a homologação (RNF02) | Média | Médio | Rodar a carga fora do horário de testes manuais e avisar antes ao desenvolvimento. |
| R6 | Requisitos ambíguos geram resultados esperados diferentes | Média | Médio | Registrar as dúvidas abaixo e pedir resposta ao cliente até 09/11. |
| R7 | SMS e WhatsApp de homologação indisponíveis ou enviando para números reais | Baixa | Alto | Usar só números fictícios e confirmar o modo de teste antes de começar. |
| R8 | Vazamento de dados entre clientes (RNF03) | Baixa | Crítico | Executar os testes da RNF03 no primeiro dia; qualquer falha suspende os testes e vai direto ao cliente. |

**Dúvidas para o cliente (R6):**

1. Se um atendimento tiver a taxa da RN08 pendente e também for o Corte gratuito da RN10, o valor a pagar é R$ 15,00 ou R$ 0,00?
2. "Cliente não compareceu" gera alguma taxa ou só deixa de contar na fidelidade?
3. Depois do Corte gratuito (11º), a contagem de 10 cortes recomeça do zero?