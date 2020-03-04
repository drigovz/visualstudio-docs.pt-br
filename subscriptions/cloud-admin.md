---
title: Configurando administradores para assinaturas mensais | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Configurando administradores para assinaturas mensais
ms.openlocfilehash: d9ae6f8aac48b9d54b851d543a72fd98854c1131
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235206"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Configurar administradores para assinaturas mensais do Visual Studio

As assinaturas mensais do Visual Studio são gerenciadas por administradores. Essas pessoas podem atribuir assinaturas, editar atribuições, adicionar ou excluir assinaturas e executar outras tarefas de gerenciamento de assinatura.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>O proprietário da assinatura do Azure é o primeiro administrador

Quando você adquire assinaturas mensais do Visual Studio, como o proprietário da assinatura do Azure usada para fazer as compras, você é automaticamente configurado como um administrador para essas assinaturas.

Você pode adquirir assinaturas mensais por meio do [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)ou contatando um provedor de soluções na nuvem. Se comprar por meio do Visual Studio Marketplace, no final da experiência de compra, você terá a oportunidade de gerenciar usuários. Escolher essa opção levará você para o portal de administração de assinaturas do Visual Studio- [https://manage.visualstudio.com](https://manage.visualstudio.com).

Depois de comprar assinaturas, será possível acessar o [Portal de Administração](https://manage.visualstudio.com) a qualquer momento. Basta entrar no portal e selecionar a assinatura apropriada do Azure no canto superior esquerdo.

Como o proprietário da assinatura do Azure usado para comprar as assinaturas mensais, você também pode atribuir administradores adicionais.

## <a name="add-administrators"></a>Adicionar administradores

Para adicionar administradores:

1. Conecte-se ao Portal do Azure em [portal.azure.com](https://portal.azure.com).
2. Entre com a conta que você usou para comprar as assinaturas mensais do Visual Studio.
3. No painel de navegação esquerdo, role para baixo até **Gerenciamento de Custos + Cobrança**.
4. Na lista **Minhas assinaturas**, escolha a assinatura do Azure que você usou para fazer a compra.
5. Clique em **Controle de acesso**, que está localizado na parte superior da lista no painel de navegação esquerdo.
6. Clique na guia **Adicionar** na parte superior da página.
7. Clique em **Adicionar atribuição de função**.
8. No painel de submenu à direita, clique na lista suspensa **Função** na parte superior do painel, role para baixo e selecione **Administrador de Acesso do Usuário**.
9. Na lista de usuários role para baixo até o usuário que você deseja tornar administrador e selecione-o. 
10. Clique em **Save** (Salvar).
11. Clique na guia **Atribuições de função** para verificar se o usuário selecionado é exibido como um Administrador de Acesso do Usuário.

Agora, o novo administrador pode entrar no [portal de administração](https://manage.visualstudio.com), selecionar a mesma assinatura do Azure que foi usada para comprar as assinaturas mensais da lista no canto superior esquerdo da página e começar a gerenciar essas assinaturas.

> [!NOTE]
> Se você vir os usuários com acesso para editar suas assinaturas mensais que você não estabeleceu como administradores, eles podem ter funções na assinatura subjacente do Azure que permitem gerenciar assinaturas. Essas funções incluem: proprietário, colaborador, administrador de serviços ou coadministrador. Para obter mais informações, visite [Adicionar gerentes de cobrança](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Para obter informações sobre assinaturas mensais do Visual Studio, consulte a [visão geral](vscloud-overview.md) em comprando assinaturas. Para comprar as assinaturas mensais do Visual Studio, visite o Visual Studio Marketplace em [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).

## <a name="see-also"></a>Consulte também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}
Saiba mais sobre como gerenciar assinaturas do Visual Studio.
- [Atribuir assinaturas individuais](assign-license.md)
- [Atribuir várias assinaturas](assign-license-bulk.md)
- [Editar assinaturas](edit-license.md)
- [Determinar o uso máximo](maximum-usage.md)



