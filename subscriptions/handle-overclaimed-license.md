---
title: Lidar com licenças superalocadas | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Saiba como os administradores podem resolver excesso de alocações de assinaturas
ms.openlocfilehash: 924f6fb2c513d70aefd28c1d4ff18d1af62178c2
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605514"
---
# <a name="overallocated-subscriptions"></a>Assinaturas superalocadas
Às vezes, os pedidos são alterados após os assinantes serem adicionados, o que pode resultar em um número maior de assinaturas atribuídas que licenças pertencentes à empresa. Isso é chamado de "superalocação".  Quando isso ocorre, a guia Assinantes mostra um alerta e fornece mais informações sobre quantas assinaturas foram superalocadas.

> [!NOTE]
> Superalocações não são permitidos em programas Open License.  Além disso, outros programas podem exibir essas informações no portal de maneira diferente.
>
> [!div class="mx-imgBorder"]
> ![Aviso de assinaturas solicitadas em excesso](_img/over-claimed/over-claimed-alert.png)

## <a name="resolve-overallocated-subscriptions"></a>Resolver assinaturas superalocadas
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

## <a name="next-steps"></a>Próximas etapas
- Saiba mais sobre como gerenciar [Assinaturas do Visual Studio com o GitHub Enterprise](assign-github.md).
- Para obter assistência com vendas, assinaturas, contas e cobrança para Assinaturas do Visual Studio, entre em contato com o [Suporte a Assinaturas](https://visualstudio.microsoft.com/subscriptions/support/) do Visual Studio.
