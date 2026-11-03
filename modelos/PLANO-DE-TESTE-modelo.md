# Plano de Teste — [Nome do sistema] v[versão]

> **Como usar este modelo:** copie este arquivo para a pasta `entregas/`, com o nome `PLANO-DE-TESTE-AgendaFacil.md`, e substitua tudo o que está entre colchetes. Os quadros "Exemplo" mostram o nível de detalhe esperado, usando **outro sistema** (uma floricultura online). Apague os exemplos quando terminar.

---

## 1. Identificação

| Campo | Preenchimento |
| --- | --- |
| Identificador do plano | [PT-AAAA-001] |
| Versão do plano | [1.0] |
| Sistema e versão testada | [Nome e versão] |
| Documento de referência | [Documento de requisitos e versão] |
| Autor | [Seu nome] |
| Data | [dd/mm/aaaa] |

**Histórico de versões**

| Versão | Data | Autor | O que mudou |
| --- | --- | --- | --- |
| 1.0 | [dd/mm] | [Nome] | Primeira versão |

## 2. Introdução e objetivo

[Em 3 a 5 linhas: o que é o sistema, para quem é, e o que este ciclo de testes precisa responder.]

> **Exemplo (floricultura):** Este plano define os testes da versão 2.1 do FlorExpress antes da campanha de Dia das Mães. O objetivo é confirmar que o cliente consegue montar um buquê, agendar a entrega e pagar, e que o sistema aguenta o pico de pedidos da véspera.

## 3. Itens de teste

[Quais partes do sistema serão testadas: aplicativos, versões, módulos, plataformas.]

## 4. Funcionalidades que serão testadas

| Regra ou requisito | Funcionalidade | Tipo de teste | Técnica | Prioridade |
| --- | --- | --- | --- | --- |
| [RN01] | [Cadastro do cliente] | [Funcional] | [Valor limite] | [Alta] |
| | | | | |

**Prioridade:** Alta = impede o uso principal ou envolve dinheiro ou dados pessoais. Média = afeta uma regra importante, com contorno. Baixa = conforto ou aparência.

## 5. Funcionalidades que não serão testadas

| Funcionalidade | Motivo |
| --- | --- |
| [Item] | [Fora do escopo da versão / sem ambiente / risco baixo] |

## 6. Abordagem

- **Estratégia:** [preventiva, reativa ou as duas, e por quê]
- **Níveis de teste:** [unitário, integração, sistema, aceitação: quais e quem executa]
- **Tipos de teste:** [funcional, regressão, desempenho, carga, segurança, usabilidade, acessibilidade...]
- **Técnicas:** [partição de equivalência, valor limite, tabela de decisão, transição de estados, exploratório]
- **Manual ou automatizado:** [o que será automatizado e o que será manual, e por quê]

## 7. Critérios de aprovação e falha

- **Um caso de teste passa quando:** [...]
- **Critério de saída (o ciclo termina e o sistema pode ser lançado quando):** [números verificáveis, ligados ao critério de lançamento do cliente]

> **Exemplo (floricultura):** O ciclo termina quando 100% dos casos de prioridade Alta forem executados, pelo menos 95% de todos os casos tiverem passado e nenhum defeito crítico ou alto estiver aberto.

## 8. Critérios de suspensão e retomada

- **Os testes são suspensos quando:** [...]
- **Os testes são retomados quando:** [...]

> **Exemplo (floricultura):** Suspender se o ambiente de homologação ficar fora do ar por mais de 1 hora, ou se o smoke test falhar numa nova versão. Retomar quando o ambiente voltar e o smoke test passar.

## 9. Entregáveis de teste

| Entregável | Quando é entregue | Responsável |
| --- | --- | --- |
| Plano de teste | [Antes do início] | [Nome] |
| Especificação dos casos de teste | | |
| Registro de execução (log) | | |
| Relatórios de defeito | | |
| Relatório final de teste | | |

## 10. Ambiente de teste

| Item | Detalhe |
| --- | --- |
| Dispositivos e sistemas | [Modelos de celular, versões de Android e iOS] |
| Navegadores | [Quais e versões] |
| Ambiente | [Homologação, endereço] |
| Dados de teste | [De onde vêm; nunca dados reais de clientes] |
| Ferramentas | [Bugtracker, planilha, DevTools, ferramenta de carga...] |

## 11. Responsabilidades e cronograma

| Atividade | Responsável | Início | Fim |
| --- | --- | --- | --- |
| [Preparar ambiente e dados] | | | |
| [Executar testes de prioridade Alta] | | | |
| [Reteste e regressão] | | | |
| [Relatório final] | | | |

## 12. Riscos e contingências

| Risco | Probabilidade | Impacto | O que fazer se acontecer |
| --- | --- | --- | --- |
| [Risco específico deste projeto] | [Alta/Média/Baixa] | [Alto/Médio/Baixo] | [Plano de contingência] |

> **Exemplo (floricultura):** Risco: o parceiro de entregas não libera o ambiente de testes. Probabilidade: média. Impacto: alto. Contingência: testar a integração com respostas simuladas e registrar o risco no relatório final.

## 13. Aprovações

| Papel | Nome | Data |
| --- | --- | --- |
| Analista de testes | | |
| Responsável pelo produto | | |
