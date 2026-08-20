# excluir-conta — página pública de exclusão de conta do ProPulse

Página estática, uma só, publicada por GitHub Pages:

**https://propulse-app.github.io/excluir-conta/**

## Por que existe

O Google Play exige, no **Data Safety**, uma URL de exclusão de conta que
carregue sem erro, seja alcançável **sem instalar o app e sem login**, cite o
nome do aplicativo e descreva o caminho da exclusão de forma proeminente
(`support.google.com/googleplay/android-developer/answer/13327111`).

As três candidatas do domínio `propulseapp.com.br` **não serviam** em 17/08/2026:

| URL | O que renderiza | Veredito |
|---|---|---|
| `/excluir-conta` | tela de login | 🔴 rota não existe no bundle publicado (`1.0.1+7`, corte de 26/07) |
| `/contato` | tela de login | 🔴 nunca foi rota de nada — e era o que estava no Console |
| `/privacy` | política de **09/07/2026** | 🟡 carrega, mas o §9 publicado não descreve a exclusão |

Esta página é a opção **(b)** do recon: superfície estática avulsa, isolada, que
não mexe no que está no ar. Decisão do Samuel em 17/08/2026.

## Quem aponta para cá

- **Play Console → Data Safety**, nos dois campos de exclusão de conta
  (o de excluir conta e dados, e o de excluir só os dados).

Nada mais. O app **não** linka para esta URL — dentro dele o equivalente é a
rota `/excluir-conta`, servida pelo próprio Flutter.

## Fonte da verdade do conteúdo

O texto **espelha** o repositório principal `propulse-app/propulse`. Ele não é
autoral; é cópia derivada de:

| Bloco desta página | Origem |
|---|---|
| passos, o que é apagado, prazos, o que é conservado | `lib/pages/excluir_conta/excluir_conta_widget.dart` (rota `/excluir-conta`) |
| retenção e ressalva legal | `lib/pages/privacy/privacy_widget.dart` §9 (política `2026-08-01`) — cópia pública em `propulse-app/politica-privacidade` |
| aviso da assinatura Pro | `lib/backend/assinatura/aviso_exclusao_assinatura.dart` (`kAvisoAssinaturaExclusao` — **texto aprovado pelo dono, não editar sem ele**) |

✅ **Os passos daqui voltaram a bater com o app em 19/08/2026** — o realinhamento
previsto abaixo aconteceu, e a página foi corrigida junto.

O histórico, porque explica a nota de alternativa que ficou no texto: depois do
commit `9c7996a` (tela principal nova do perfil), o item "Excluir conta" da
seção Perfil abria uma página explicativa **sem botão**, e quem excluía de fato
era **Perfil → "Informações pessoais"** — o caminho que esta página publicava.
O **PR #178** deu botão próprio à rota `/excluir-conta`, e o **release 1.0.5
(bundle 18), público na Play desde 19/08**, é o primeiro build em mãos de
usuário com ele. Os passos passaram a ser o caminho curto (Perfil → "Excluir
conta" → botão); "Informações pessoais" continua funcionando e virou nota.

⚠️ **Regra que fica:** o gatilho para mexer nesta página é **build publicado**,
não merge no repositório. Ela descreve o app que está no aparelho.

⚠️ **Os prazos não são texto de marketing:** "imediatamente" é a cascata das FKs
de `delete_my_account()`; "até 30 minutos" é o intervalo do Schedule Trigger do
workflow n8n que consome a `storage_cleanup_queue`. Mudou o intervalo? Esta
página mente até ser corrigida.

## Como mexer

`index.html` é o arquivo inteiro — HTML e CSS, sem dependência externa, sem
script, sem fonte remota, sem coleta de dado. Commit na `main` republica.
