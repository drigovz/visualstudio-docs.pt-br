---
title: Funções Superadministrador e Administrador no Portal de Administração
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 04/07/2020
ms.topic: conceptual
description: Saiba mais sobre as funções Superadministrador e Administrador e como atribuir administradores.
ms.openlocfilehash: bf10b95d44a960fea50bff6b2fba7b9a8dc98a26
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248440"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Superadministradores e administradores para contratos de assinatura do Visual Studio

Há duas funções diferentes no novo Portal de Administração de Assinaturas do Visual Studio para clientes do licenciamento por volume. Essas funções são semelhantes à função Contato Principal/para Notificações e à função Gerente de Assinaturas que existiam no VLSC.

**Superadministradores:** Quando uma organização é inicialmente configurada, o contato principal ou avisos se torna um superadministrador por padrão. O contato principal ou para notificações pode optar por atribuir superadministradores ou administradores adicionais. Um superadministrador pode adicionar e remover outros administradores e também assinantes. Se houver mais de dois superadministradores no sistema, um superadministrador poderá excluir todos, exceto os dois últimos por segurança.

**Administradores:** Um administrador só pode ser atribuído por um superadministrador. Um administrador só pode gerenciar assinantes nos acordos que o superadministrador atribui a eles.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-administrators"></a>Como atribuir administradores
Para atribuir novos administradores:
1. Entre em https://manage.visualstudio.com usando um endereço de email atribuído como um superadministrador do contrato por meio do qual as assinaturas foram adquiridas.
2. Selecione a guia rotulada **gerenciar administradores**.
3. Selecione **Adicionar**.
   > [!div class="mx-imgBorder"]
   > ![Adicionar administradores](_img/admin-roles/add-admins.png "Selecione a folha gerenciar administradores e, em seguida, selecione Adicionar para atribuir novos administradores.")
4. Preencha o formulário com as informações do novo administrador.  
   > [!div class="mx-imgBorder"]
   > ![Formulário Adicionar administrador](_img/admin-roles/add-form.png "Insira as informações de entrada para o novo administrador e escolha se deseja torná-las um superadministrador.  Em seguida, selecione Adicionar.")

   > [!NOTE]
   > Caso deseje que esse administrador tenha a capacidade de atribuir administradores adicionais, lembre-se de marcar a caixa **Superadministrador**.

5. Depois de selecionar **Adicionar** para atribuir o novo administrador, eles receberão um email convidando-os para entrar no Portal.  

## <a name="resources"></a>Recursos
- [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Consulte também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Próximas etapas
- Saiba como [atribuir assinaturas](assign-license.md)
- Saiba mais sobre a gama completa de [benefícios da assinatura](https://visualstudio.microsoft.com/vs/benefits/)
- [Definir preferências de contrato](admin-prefs.md) 


