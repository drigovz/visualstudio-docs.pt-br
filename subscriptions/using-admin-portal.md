---
title: Introdução ao portal de administração de assinaturas | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Saiba como começar a gerenciar as assinaturas do Visual Studio de sua organização com o portal de administração de assinaturas.
ms.openlocfilehash: f3b11a0a0977fff8a6c89f565adffb1cac49e2ad
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605723"
---
# <a name="get-started-with-the-visual-studio-subscriptions-administration-portal"></a>Introdução ao portal de administração de assinaturas do Visual Studio
Lembre-se disto ao usar o Portal de Administração de Assinaturas do Visual Studio:
- **As assinaturas do Visual Studio são licenciadas por usuário.** Cada assinante pode usar o software em quantos computadores forem necessários para desenvolvimento e teste.
- **Atribua apenas um nível de assinatura para cada assinante**, correspondente à assinatura do Visual Studio comprada pela sua organização. Se houver assinantes com mais de um nível de assinatura atribuído, edite as configurações para que eles fiquem com apenas uma.
- **O nível de assinatura de um assinante precisará ser atualizado** quando a assinatura for atualizada (após a compra de um licença de “step-up”) ou renovada para um nível inferior.
- **Não compartilhe assinaturas entre assinantes.** As assinaturas devem ser atribuídas a indivíduos nomeados.  A atribuição de assinaturas a equipes não é permitida.  Você deverá atribuir uma assinatura a qualquer pessoa que usar completa ou parcialmente os benefícios da assinatura (software para desenvolvimento e teste, Microsoft Azure, e-learning, etc.).

## <a name="access-to-the-portal"></a>Acesso ao portal
Se você for o contato principal ou para notificações no contrato de sua organização, o acesso ao portal será provisionado automaticamente para você ao configurar seu contrato de licenciamento por volume. Você receberá um email de boas-vindas disparado pelo sistema e ele indicará o endereço de email a ser usado para entrar no portal. Quando estiver conectado, você será configurado automaticamente como um superadministrador e poderá começar a gerenciar assinaturas e outros administradores. 

## <a name="administrator-roles"></a>Funções de administrador
Há duas funções diferentes no novo Portal de Administração de Assinaturas do Visual Studio para clientes do Volume Licensing. Essas funções são como a função de contato principal/para notificações e a função de gerenciador de assinaturas que existem atualmente no VLSC.

**Superadministradores:** Ao configurar uma organização pela primeira vez, o Contato Principal ou para Notificações torna-se um superadministrador por padrão. O contato principal ou para notificações pode optar por atribuir superadministradores ou administradores adicionais. Um superadministrador pode adicionar e remover outros administradores e também assinantes. Se houver mais de dois superadministradores no sistema, um superadministrador poderá excluir todos, exceto os dois últimos por segurança.

**Administradores:** Um administrador só pode ser configurado por um superadministrador. Um administrador pode gerenciar os assinantes nos contratos que o superadministrador atribui a ele.

## <a name="the-subscribers-page"></a>A página Assinantes
Depois que você atribuir as assinaturas, a guia Assinantes fornecerá informações detalhadas sobre seus assinantes, incluindo:
- O nome e o sobrenome de cada assinante.
- O endereço de email deste usuário.
- O nível de assinatura que foi atribuído.
- A data em que a assinatura foi atribuída.
- A data de validade da assinatura.
- Uma descrição de texto opcional.
- Uma indicação se os downloads para o assinante foram habilitados ou desabilitados.
- O país em que eles estão localizados.
- A preferência de idioma para o email de comunicação de atribuição do portal de administração.
- Um campo opcional para um endereço de email diferente usado para comunicações de conexão.

No lado esquerdo dessa página, são exibidas informações adicionais sobre o número de licenças de assinatura compradas, atribuídas e ainda disponíveis na organização para cada contrato.
> [!div class="mx-imgBorder"]
> ![Página Assinantes do Portal de Administração de Assinaturas do Visual Studio](_img/using-admin-portal/subscribers-page.png)

## <a name="the-details-page"></a>A página Detalhes
Para obter mais informações sobre o contrato exibido, selecione a guia Detalhes. Ela mostra o status do contrato, a conta da compra, os detalhes da organização, os superadministradores e outras informações pertinentes.
> [!div class="mx-imgBorder"]
> ![Página Detalhes do Portal de Administração de Assinaturas do Visual Studio](_img/using-admin-portal/details-page.png)

## <a name="next-steps"></a>Próximas etapas
Saiba mais as políticas dos administradores:
- [Visão geral das responsabilidades do administrador](admin-responsibilities.md)
- [Inventário do ambiente de pré-produção](admin-inventory.md)
- [Gerenciar equipes grandes e prestadores de serviço externos](manage-teams.md)
- [Rastrear atribuições de usuário e processar pedidos](assignments-orders.md)
- Utilizar o [Uso Máximo](maximum-usage.md) para rastrear os compromissos de compra
