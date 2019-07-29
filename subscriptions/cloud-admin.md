---
title: Configuração de administradores para assinaturas de nuvem | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: lank
ms.date: 07/17/2019
ms.topic: conceptual
description: Configuração de administradores para assinaturas de nuvem
ms.openlocfilehash: 62a350e6061444e3c75878dfd89739011c4641d5
ms.sourcegitcommit: 57866dd72fd0e15ce61128df70729b427a2d02eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315214"
---
# <a name="set-up-administrators-for-visual-studio-cloud-subscriptions"></a>Configure administradores para assinaturas de nuvem do Visual Studio

As assinaturas de nuvem do Visual Studio são gerenciadas por administradores. Essas pessoas podem atribuir assinaturas, editar atribuições, adicionar ou excluir assinaturas e executar outras tarefas de gerenciamento de assinatura.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>O proprietário da assinatura do Azure é o primeiro administrador

Ao comprar assinaturas de nuvem do Visual Studio, como o proprietário da assinatura do Azure usado para fazer as compras, você é configurado automaticamente como administrador dessas assinaturas.

Você pode comprar assinaturas de nuvem por meio do [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) ou contatando um Provedor de Soluções na Nuvem. Se comprar por meio do Visual Studio Marketplace, no final da experiência de compra, você terá a oportunidade de gerenciar usuários. Ao escolher essa opção, você será levado para o Portal de Administração de assinaturas do Visual Studio – [https://manage.visualstudio.com](https://manage.visualstudio.com).

Depois de comprar assinaturas, será possível acessar o [Portal de Administração](https://manage.visualstudio.com) a qualquer momento. Basta entrar no portal e selecionar a assinatura do Azure apropriada no canto superior esquerdo.

Como o proprietário da assinatura do Azure usado para comprar as assinaturas de nuvem, você também pode atribuir outros administradores.

## <a name="add-administrators"></a>Adicionar administradores

Para adicionar administradores:

1. Conecte-se ao Portal do Azure em [portal.azure.com](https://portal.azure.com).
2. Entre com a conta usada para comprar as assinaturas de nuvem do Visual Studio.
3. No painel de navegação esquerdo, role para baixo até **Gerenciamento de Custos + Cobrança**.
4. Na lista **Minhas assinaturas**, escolha a assinatura do Azure que você usou para fazer a compra.
5. Clique em **Controle de acesso**, que está localizado na parte superior da lista no painel de navegação esquerdo.
6. Clique na guia **Adicionar** na parte superior da página.
7. Clique em **Adicionar atribuição de função**.
8. No painel de submenu à direita, clique na lista suspensa **Função** na parte superior do painel, role para baixo e selecione **Administrador de Acesso do Usuário**.
9. Na lista de usuários role para baixo até o usuário que você deseja tornar administrador e selecione-o. 
10. Clique em **Salvar**.
11. Clique na guia **Atribuições de função** para verificar se o usuário selecionado é exibido como um Administrador de Acesso do Usuário.

Agora, o novo administrador pode entrar no [Portal de Administração](https://manage.visualstudio.com), selecionar a mesma assinatura do Azure que foi usada para comprar as assinaturas de nuvem na lista no canto superior esquerdo da página e começar a gerenciar essas assinaturas.

> [!NOTE]
> Se você vir os usuários com acesso para editar suas assinaturas de nuvem que você não estabeleceu como administradores, isso poderá significar que eles têm funções na assinatura do Azure subjacente que lhes permite gerenciar assinaturas. Essas funções incluem: proprietário, colaborador, administrador de serviços ou coadministrador. Para obter mais informações, visite [Add billing managers](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts) (Adicionar gerenciadores de cobrança).

Para saber mais sobre assinaturas de nuvem do Visual Studio, confira a [Visão geral](vscloud-overview.md) em Comprar assinaturas. Para comprar assinaturas de nuvem do Visual Studio, visite o Visual Studio Marketplace em [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).
