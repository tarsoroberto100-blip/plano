# AgendaFácil — Documento de Requisitos v1.0

**Produto:** AgendaFácil, aplicativo de agendamento para a Barbearia Bigode Grosso
**Plataformas:** aplicativo Android e iOS, e versão web para o balcão da barbearia
**Versão em teste:** 1.0 (candidata a lançamento)
**Lançamento previsto:** sexta-feira, 13/11
**Equipe de testes disponível:** 2 analistas, de segunda 09/11 a quinta 12/11
**Ambiente de homologação:** https://homolog.agendafacil.exemplo (dados fictícios)

---

## 1. Contexto

A Barbearia Bigode Grosso atende hoje só por telefone e WhatsApp. Os clientes reclamam de demora na resposta, e os barbeiros perdem horários por esquecimento. O AgendaFácil permite que o cliente escolha o serviço, o barbeiro, o dia e o horário, e receba lembretes antes do atendimento.

## 2. Serviços e barbeiros

| Serviço | Duração | Preço |
| --- | --- | --- |
| Corte | 30 min | R$ 45,00 |
| Barba | 30 min | R$ 35,00 |
| Corte + Barba | 60 min | R$ 70,00 |
| Pigmentação | 45 min | R$ 60,00 |

Barbeiros: **Léo**, **Rafa** e **Duda**. Todos fazem todos os serviços.

## 3. Regras de negócio

**RN01 — Cadastro do cliente.** O cliente informa nome (mínimo de 3 caracteres) e celular com DDD (11 dígitos). E-mail é opcional.

**RN02 — Login por código.** O login é feito com um código de 6 dígitos enviado por SMS. O código vale por 5 minutos. Depois de 3 códigos errados seguidos, o login fica bloqueado por 15 minutos.

**RN03 — Horário de funcionamento.** A barbearia atende de terça a sábado, das 9h às 19h, com pausa para almoço das 12h às 13h. Domingo e segunda não aparecem no calendário.

**RN04 — Antecedência.** Um agendamento pode ser feito com no mínimo 2 horas e no máximo 30 dias de antecedência.

**RN05 — Horários disponíveis.** A agenda é dividida em intervalos de 15 minutos. Um horário só aparece se o serviço inteiro couber antes do almoço ou do fechamento, sem sobrepor outro agendamento do mesmo barbeiro.

**RN06 — Escolha do barbeiro.** O cliente escolhe um barbeiro ou a opção "Qualquer um". Em "Qualquer um", o sistema mostra a união dos horários livres dos três.

**RN07 — Limite por cliente.** Cada cliente pode ter no máximo 2 agendamentos futuros ao mesmo tempo.

**RN08 — Cancelamento.** O cancelamento é gratuito até 3 horas antes do horário. Depois disso, é cobrada uma taxa de R$ 15,00, somada ao valor do próximo atendimento do cliente.

**RN09 — Lembretes.** O cliente recebe um lembrete por WhatsApp 24 horas antes e outro 1 hora antes do atendimento.

**RN10 — Fidelidade.** A cada 10 serviços de Corte concluídos, o 11º Corte é gratuito. Os outros serviços não contam e não podem ser gratuitos.

**RN11 — Pagamento.** O pagamento é feito na barbearia. O aplicativo só mostra o valor a pagar, já com a taxa da RN08 ou o desconto da RN10, quando houver.

**RN12 — Painel do balcão.** Na versão web, o atendente vê a agenda do dia dos três barbeiros e pode marcar um atendimento como "Concluído" ou "Cliente não compareceu".

## 4. Requisitos não-funcionais

**RNF01 — Desempenho.** A tela de horários disponíveis carrega em até 2 segundos numa conexão 4G.

**RNF02 — Carga.** O sistema atende 200 usuários ao mesmo tempo sem erro, que é o pico esperado no sábado de manhã.

**RNF03 — Privacidade (LGPD).** Um cliente nunca vê nome, celular ou histórico de outro cliente.

**RNF04 — Compatibilidade.** O aplicativo funciona em Android 10 ou superior e iOS 15 ou superior. A versão web funciona nas duas últimas versões de Chrome, Edge e Safari.

**RNF05 — Acessibilidade.** O aplicativo funciona com o leitor de tela do celular (TalkBack e VoiceOver) e respeita o tamanho de fonte escolhido no aparelho.

## 5. Fora do escopo desta versão

- Pagamento pelo aplicativo
- Avaliação dos barbeiros pelos clientes
- Venda de produtos (pomadas, óleos)

## 6. Critério de lançamento definido pelo cliente

A barbearia só lança a versão 1.0 se nenhum defeito impedir o cliente de agendar, cancelar ou fazer login, e se os dados dos clientes estiverem protegidos (RNF03).
