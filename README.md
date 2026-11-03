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
└── entregas/                              ← seus arquivos finais vão aqui
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
