---
title: Configuração de administradores para assinaturas mensais | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Configuração de administradores para assinaturas mensais
ms.openlocfilehash: a5d7c6e9442efd70ea3e7c2b7e7da4239e226aa2
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "78289835"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Configure administradores para assinaturas mensais do Visual Studio

As assinaturas mensais do Visual Studio são gerenciadas pelos administradores. Essas pessoas podem atribuir assinaturas, editar atribuições, adicionar ou excluir assinaturas e executar outras tarefas de gerenciamento de assinatura.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>O proprietário da assinatura do Azure é o primeiro administrador

Quando você compra assinaturas mensais do Visual Studio, como o proprietário da assinatura do Azure usado para fazer as compras, você é automaticamente configurado como administrador para essas assinaturas.

Você pode comprar assinaturas mensais através do [Visual Studio Marketplace,](https://marketplace.visualstudio.com/subscriptions)ou entrando em contato com um Provedor de Soluções em Nuvem. Se comprar por meio do Visual Studio Marketplace, no final da experiência de compra, você terá a oportunidade de gerenciar usuários. Escolher essa opção vai levá-lo ao Portal [https://manage.visualstudio.com](https://manage.visualstudio.com)de Administração de Assinaturas do Visual Studio - .

Depois de comprar assinaturas, será possível acessar o [Portal de Administração](https://manage.visualstudio.com) a qualquer momento. Basta entrar no portal e selecionar a assinatura apropriada do Azure no canto superior esquerdo.

Como o proprietário da assinatura do Azure usado para comprar as assinaturas mensais, você também pode atribuir administradores adicionais.

## <a name="add-administrators"></a>Adicionar administradores

Para adicionar administradores:

1. Conecte-se ao Portal do Azure em [portal.azure.com](https://portal.azure.com).
2. Faça login com a conta que você usou para comprar as assinaturas mensais do Visual Studio.
3. Em **serviços azure,** escolha **Gerenciamento de Custos + Faturamento**.
   > [!div class="mx-imgBorder"]
   > ![Escolha gerenciamento de custos + faturamento em serviços do Azure](_img/cloud-admin/azure-cost-billing.png)
4. Na lista **Minhas assinaturas**, escolha a assinatura do Azure que você usou para fazer a compra.
   > [!div class="mx-imgBorder"]
   > ![Escolha uma assinatura](_img/cloud-admin/subscription-list.png)
5. Clique **em Access control (IAM)**, que está localizado perto do topo da lista no painel de navegação à esquerda.
6. Clique na guia **Adicionar** na parte superior da página.
7. Clique em **Adicionar atribuição de função**.
   > [!div class="mx-imgBorder"]
   > ![Escolha o controle de acesso, adicione, adicione a atribuição de função](_img/cloud-admin/access-control-add.png)
8. No painel de submenu à direita, clique na lista suspensa **Função** na parte superior do painel, role para baixo e selecione **Administrador de Acesso do Usuário**.
9. Na lista de usuários role para baixo até o usuário que você deseja tornar administrador e selecione-o. 
   > [!div class="mx-imgBorder"]
   > ![Escolha Função, Admin de acesso ao usuário](_img/cloud-admin/add-role-user-access-admin.png)
10. Clique em **Salvar**.
11. Clique na guia **Atribuições de função** para verificar se o usuário selecionado é exibido como um Administrador de Acesso do Usuário.

O novo administrador agora pode entrar no [Portal da Administração,](https://manage.visualstudio.com)selecionar a mesma assinatura do Azure que foi usada para comprar as assinaturas mensais da lista no canto superior esquerdo da página e começar a gerenciar essas assinaturas.

> [!NOTE]
> Se você ver usuários com acesso a editar suas assinaturas mensais que você não estabeleceu como administradores, eles podem ter funções na assinatura subjacente do Azure que lhes permitem gerenciar assinaturas. Essas funções incluem: proprietário, contribuinte, diretor de serviços ou co-admin. Para obter mais informações, visite [Adicionar gerentes de faturamento](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Para obter informações sobre assinaturas mensais do Visual Studio, consulte o [Overview](vscloud-overview.md) em Assinaturas de Compra. Para comprar assinaturas mensais do Visual Studio, [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)visite o Visual Studio Marketplace em .

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Próximas etapas
Saiba mais sobre como gerenciar assinaturas do Visual Studio.
- [Atribuir assinaturas individuais](assign-license.md)
- [Atribuir várias assinaturas](assign-license-bulk.md)
- [Editar assinaturas](edit-license.md)
- [Determine o uso máximo](maximum-usage.md)



