# Consolidação O.S. — Automação de Aprovação de Orçamentos

Fluxo construído no **Microsoft Power Automate** que automatiza a aprovação de orçamentos de ordens de serviço diretamente pelo Microsoft Teams, eliminando idas e vindas manuais por e-mail.

## O que o fluxo faz

1. **Monitora um canal do Teams** em busca de novas mensagens contendo orçamentos em PDF anexados (verificação a cada 5 minutos).
2. **Identifica o responsável** pela aprovação com base no conteúdo da mensagem.
3. **Envia um Adaptive Card** interativo ao responsável, com três ações:
   - 📄 **Abrir orçamento em PDF** — leva direto à mensagem original no Teams, onde o anexo está disponível.
   - ✅ **Aprovar orçamento**
   - ❌ **Recusar orçamento**
4. **Registra a decisão automaticamente**:
   - Dispara um e-mail para os gestores responsáveis informando o resultado (aprovado/recusado).
   - Em caso de aprovação, envia também um card de confirmação simplificado via Teams.

## Destaques técnicos

- **Adaptive Cards** para UI interativa dentro do Teams (sem precisar de um app dedicado).
- **Expressões condicionais** para rotear a aprovação entre diferentes responsáveis.
- **Tratamento de link robusto**: o botão de abrir o PDF usa o `webUrl` da própria mensagem do Teams como link principal (com fallback para o anexo), evitando erros de acesso comuns em links de anexo direto.
- **Ações paralelas**: e-mail de notificação e card de confirmação disparam em paralelo, sem depender um do outro.

## Stack

`Power Automate` · `Microsoft Teams connector` · `Office 365 Outlook connector` · `Adaptive Cards (JSON)`

---

> Dados de e-mail/empresa neste export foram generalizados para fins de portfólio.
