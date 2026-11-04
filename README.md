# Plano de Testes — Aula 1

Hoje você vai aprender a escrever um **plano de teste completo**: o documento que diz o que será testado, como, por quem, quando, com quais critérios e quais riscos existem.

## O que tem neste repositório

```
plano-de-testes/
├── README.md                              ← este arquivo
├── agendafacil/
│   └── REQUISITOS-AgendaFacil.md          ← o sistema que você vai planejar
├── modelos/
│   └── PLANO-DE-TESTE-modelo.md           ← o modelo com as 13 seções
├── pratica1/
│   ├── Plano-MercadoJa-revisar.md         ← um plano com problemas
│   └── DEFEITOS-ENCONTRADOS.md            ← onde vocês registram os problemas
├── revisao/
│   └── CHECKLIST-REVISAO.md               ← checklist da revisão por pares
└── entregas/                             ← seus arquivos finais vão aqui

# Prática 1 — Defeitos encontrados no plano do MercadoJá

**Dupla:** Tarso e [Nome do colega]

Leia o arquivo `Plano-MercadoJa-revisar.md` e registre cada defeito numa linha. Um defeito de documento é qualquer coisa que esteja errada, faltando, vaga, contraditória ou que não dê para verificar.

| # | Seção do plano | Defeito encontrado | Tipo | Por que é um problema | Como corrigir |
| --- | --- | --- | --- | --- | --- |
| 1 | 1. Identificação | Só traz o nome do app e "equipe de QA". Não há identificador do documento, versão do plano, versão do sistema testada nem data. | Falta | Sem versão e data não dá para saber qual build foi testado nem se o plano está atualizado. | Incluir ID do plano (ex.: PT-MJ-001), versão do plano (1.0), versão do app e data. |
| 2 | 2. Objetivo | "Testar o sistema para ver se está funcionando" não diz o que o ciclo de testes precisa responder. | Vago | Não dá para saber quando o objetivo foi atingido nem o que decidir ao final. | Ex.: "Verificar se as regras R1 a R7 funcionam em Android e iOS e se o app pode ser liberado em 10/11." |
| 3 | 3. Escopo | "Vamos testar tudo" não define o que está dentro e o que está fora (plataformas, integrações, tipos de teste). | Vago | Tudo nunca cabe em 2 dias; sem limite, o escopo não é verificável e gera discussão depois. | Listar o que entra (R1 a R7, Android e iOS) e o que fica fora, com justificativa. |
| 4 | 4. Funcionalidades | O frete (R4: grátis a partir de R$ 100,00, senão R$ 9,90) não aparece na lista. | Falta | É regra de negócio que mexe com dinheiro e tem valor limite (R$ 99,99 / R$ 100,00 / R$ 100,01). | Incluir R4 com prioridade Alta e testes de valor limite. |
| 5 | 4. Funcionalidades | Pagamento (R3) e Login (R1) estão com prioridade **Baixa**. | Erro | Sem login e pagamento o cliente não compra: são o caminho crítico e envolvem dinheiro e dados pessoais. | Subir ambos para Alta (ou Crítica). |
| 6 | 4. Funcionalidades | O banner de promoções (R7) está com prioridade **Alta**, a mesma da busca e carrinho. | Erro | É a função de menor impacto no negócio; a prioridade está invertida em relação ao risco. | Rebaixar R7 para Baixa e usar o tempo em R1, R3 e R4. |
| 7 | 5. Abordagem | Fala em testes de **caixa branca**, mas diz que a equipe não tem acesso ao código-fonte. | Contradição | Caixa branca exige o código; a abordagem é impossível de executar como escrita. | Usar caixa preta (partição de equivalência, valor limite) ou conseguir acesso ao código. |
| 8 | 5. Abordagem | É só "faremos testes": sem níveis, tipos (funcional, usabilidade, desempenho, segurança), técnicas nem plataformas (Android e iOS). | Falta | Ninguém sabe como testar; o app é mobile e o plano não cita dispositivos, nem testes de segurança do pagamento. | Definir níveis, tipos e técnicas e ligar cada um aos requisitos (ex.: valor limite em R4). |
| 9 | 6. Critério de saída | "Quando o sistema estiver bom" não é mensurável. | Vago | Cada pessoa vai entender "bom" de um jeito; não há como decidir se pode liberar. | Usar números: ex. 100% dos casos Altos executados, 95% passando, 0 defeitos críticos abertos. |
| 10 | 6. Critério de saída | Não existem critérios de suspensão e retomada dos testes. | Falta | Se o ambiente cair ou houver defeito bloqueante, ninguém sabe quando parar nem quando voltar. | Definir suspensão (ex.: defeito bloqueante em login ou pagamento) e retomada (correção validada). |
| 11 | 7. Entregáveis | Só "prints das telas com erro". Faltam casos de teste, registro de execução, relatório de defeitos e relatório final. | Falta | Print solto não prova o que foi testado nem o resultado; o próprio cronograma prevê relatório final. | Listar: especificação de casos, registro de execução, relatórios de defeito e relatório final. |
| 12 | 8. Ambiente | Testes "no computador do testador", mas o app é Android e iOS. | Erro | O comportamento real (tela, toque, versão do sistema) só aparece em celulares ou emuladores. | Definir aparelhos/emuladores, versões de Android e iOS e rede (Wi-Fi e 4G). |
| 13 | 8. Ambiente | Usa uma cópia do banco com **clientes reais** do supermercado. | Risco (LGPD) | Expõe dados pessoais em ambiente de teste, violando a LGPD, e testadores podem disparar e-mails ou cobranças reais. | Usar apenas dados fictícios, como a regra do curso, ou dados anonimizados. |
| 14 | 8. Ambiente | Nada sobre como testar pagamento por cartão e Pix sem cobrar de verdade. | Falta | Sem ambiente de homologação do meio de pagamento, ou se testa com dinheiro real ou não se testa. | Incluir o ambiente de homologação (sandbox) do gateway, com cartões e Pix de teste. |
| 15 | 9. Responsabilidades | "Todos testam tudo": nenhum responsável por área, nenhum papel. | Vago | Quando todos são responsáveis, ninguém é: há retrabalho e lacunas, e ninguém responde pelo relatório. | Tabela com nome, papel e áreas (ex.: Ana: R1 e R3; Bruno: R2 e R4; líder de QA: relatório). |
| 16 | 10. Cronograma | O lançamento (10/11) vem **antes** da execução dos testes (11/11 a 12/11). | Contradição | O app iria para o cliente sem ter sido testado. | Terminar os testes antes do lançamento, com o relatório final antes de 10/11. |
| 17 | 10. Cronograma | Só 2 dias de execução, sem tempo para correção e reteste e sem marcos (preparação, casos, ciclos). | Falta | Todo defeito achado precisa ser corrigido e retestado; sem folga o cronograma não é realista. | Prever preparação, 2 ciclos de execução, reteste e margem de segurança. |
| 18 | 11. Riscos | "Nenhum risco identificado". | Erro | Há riscos óbvios: prazo curto, pagamento, dados reais, falta de aparelhos, capacidade de entrega por janela (R5). | Listar riscos com probabilidade, impacto e contingência. |
| 19 | Estrutura geral | O plano tem 11 seções; o modelo do curso tem 13. | Falta | Faltam itens do modelo, e nenhum item do plano se liga formalmente a regras e requisitos não-funcionais. | Conferir com `modelos/PLANO-DE-TESTE-modelo.md` e incluir as seções que faltam, ligando cada item a R1 a R7. |

**Tipos:** Falta · Vago · Contradição · Erro · Risco (segurança ou LGPD)

**Qual dos defeitos vocês consideram o mais grave? Por quê?**

O defeito 13 (cópia do banco com clientes reais). Os outros deixam o plano ruim e podem ser corrigidos no papel, mas expor dados pessoais reais em ambiente de teste é uma violação da LGPD que pode causar dano concreto (vazamento, e-mails ou cobranças reais disparados por engano) e não dá para desfazer. Em segundo lugar vem o defeito 16: lançar o aplicativo antes de testá-lo anula o objetivo do plano.
```

## Antes de começar

1. Clique em **Use this template → Create a new repository**.
2. Nome: `plano-de-testes-nome-sobrenome`. Pode ser **Private**, com o professor como colaborador.
3. Clone: `git clone <link-do-seu-repositorio>` e abra a pasta no VS Code.
4. Para ver os arquivos `.md` formatados no VS Code, abra o arquivo e aperte **Ctrl + Shift + V**.

## As práticas de hoje

| Prática | O que fazer | Arquivo | Mensagem do commit |
| --- | --- | --- | --- |
| 1 — Caça aos defeitos | Em dupla, encontrar os problemas do plano do MercadoJá | `pratica1/DEFEITOS-ENCONTRADOS.md` | `docs: defeitos do plano MercadoJa` |
| 2 — Plano do AgendaFácil | Escrever o plano completo, usando o modelo | `entregas/PLANO-DE-TESTE-AgendaFacil.md` | `docs: plano de teste AgendaFacil` |
| 3 — Revisão por pares | Revisar o plano de um colega e corrigir o seu | `entregas/REVISAO-por-<nome>.md` | `docs: revisao por pares e correcoes` |

Na Prática 1, cada integrante da dupla salva uma cópia do arquivo no próprio repositório.

## Regras

- O `REQUISITOS-AgendaFacil.md` é a fonte da verdade. Todo item do plano deve se ligar a uma regra (RN) ou a um requisito não-funcional (RNF).
- Seja específico: "testar o login" não diz nada; "testar o bloqueio após 3 códigos errados (RN02), com valor limite" diz.
- Critério de saída sempre com números.
- Use apenas dados fictícios.

## Checklist de entrega

- [ ] `pratica1/DEFEITOS-ENCONTRADOS.md` preenchido
- [ ] `entregas/PLANO-DE-TESTE-AgendaFacil.md` com as 13 seções preenchidas
- [ ] `entregas/REVISAO-por-<nome>.md` feito pelo colega no seu repositório
- [ ] Plano corrigido depois da revisão (versão 1.1 no histórico de versões)
- [ ] 3 commits e push feitos
