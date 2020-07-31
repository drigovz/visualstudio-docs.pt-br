---
title: Lidar com licenças superalocadas | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 03/03/2020
ms.topic: conceptual
description: Saiba como os administradores podem resolver assinaturas Superalocadas
ms.openlocfilehash: b518dc9300862e7c39af0489734734668097ef9f
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453719"
---
# <a name="over-allocated-subscriptions"></a>Assinaturas Superalocadas
Às vezes, os pedidos são alterados após os assinantes serem adicionados, o que pode resultar em um número maior de assinaturas atribuídas que licenças pertencentes à empresa. Isso é chamado de "sobrealocação".  

Para ver as alocações de sua assinatura, clique no ícone superior à esquerda para abrir o painel alocações.  

> [!NOTE]
> Não são permitidas sobrelocalidades em programas de licença aberta.  Além disso, outros programas podem exibir essas informações no portal de maneira diferente.
>
> [!div class="mx-imgBorder"]
> ![Aviso de assinaturas solicitadas em excesso](_img/over-claimed/over-claimed-alert.png "O número de sobrealocações é listado na visão geral e é representado pela barra com hash no grafo para cada tipo de assinatura.")

Observe que a exibição usa uma barra com hash para indicar assinaturas Superalocadas.  O número de sobrealocações em todos os tipos de assinatura está incluído na seção de visão geral na parte superior e cada nível de assinatura também exibe seu próprio status de alocação.  

## <a name="resolve-over-allocated-subscriptions"></a>Resolver assinaturas Superalocadas
Há várias maneiras de resolver superalocações:
- Entre em contato com seu revendedor para comprar assinaturas adicionais.
- Aguarde até o período de adequação ("true-up") anual e pague pelas assinaturas superalocadas nesse momento. 
- Exclua algumas atribuições de assinatura.  (Isso não evitará a necessidade de pagamento na adequação ("true-up") anual, pois essa adequação é baseada no número máximo de assinaturas atribuídas em qualquer momento durante o ano.)

## <a name="billing-and-true-up"></a>Adequação ("true-up") e cobrança
Se sua organização tiver um EA (Contrato Enterprise), os administradores poderão atribuir assinaturas sem comprá-las e pagar por elas mais tarde por meio de um processo de reconciliação, conhecido como adequação ("true-up").  Ao superalocar, sua organização será cobrada pelo número máximo de assinaturas atribuídas aos usuários durante a adequação ("true-up").  Isso acontecerá mesmo se você não tiver o número máximo de assinaturas atribuído no momento em que ocorrer a adequação ("true-up").  Para saber mais sobre como monitorar seu uso máximo, acesse o tópico [Uso máximo](maximum-usage.md).

> [!Important]
> Se as Assinaturas do Visual Studio com o GitHub Enterprise tiverem sido atribuídas por administradores de assinatura do Visual Studio e nunca houver acontecido uma compra dessas assinaturas, elas não estarão visíveis para administradores do GitHub Enterprise dentro da organização. Para garantir que as assinaturas do GitHub Enterprise estejam visíveis, uma compra incluindo **pelo menos um** Visual Studio Professional com o GitHub Enterprise ou o Visual Studio Enterprise com a assinatura do GitHub Enterprise deverá ser feita na primeira vez em que as assinaturas forem atribuídas.
>
> É responsabilidade do cliente garantir que, para cada assinatura do GitHub atribuída, haja uma assinatura correspondente do Visual Studio com o GitHub atribuída no portal de gerenciamento para permanecer em conformidade com os requisitos de licenciamento para este assinatura.

## <a name="see-also"></a>Veja também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Próximas etapas
- Saiba mais sobre como gerenciar [Assinaturas do Visual Studio com o GitHub Enterprise](assign-github.md).
- Para obter assistência com vendas, assinaturas, contas e cobrança para Assinaturas do Visual Studio, entre em contato com o [Suporte a Assinaturas](https://visualstudio.microsoft.com/subscriptions/support/) do Visual Studio.