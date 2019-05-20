---
title: Lidar com licenças solicitada em excesso | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 02/13/2018
ms.topic: conceptual
description: Saiba como os administradores podem resolver o excesso de assinaturas solicitadas
searchscope: VS Subscription
ms.openlocfilehash: 6217dcd3cef9a65db3e45ba76f57167f47535671
ms.sourcegitcommit: bd519d1da375e374016f94a44c295d3253f61a8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945135"
---
# <a name="overallocated-subscriptions"></a>Assinaturas superalocadas

Às vezes, os pedidos são alterados após os assinantes serem adicionados, o que pode resultar em um número maior de assinaturas atribuídas que licenças pertencentes à empresa. Quando isso ocorre, a guia Assinantes mostra um alerta e fornece mais informações.

> [!NOTE]
> Os cenários de solicitações em excesso não são permitidos em programas Open License.  Além disso, outros programas podem exibir essas informações no portal de maneira diferente.
>
> [!div class="mx-imgBorder"]
> ![Aviso de assinaturas solicitadas em excesso](_img/over-claimed/over-claimed-alert.png)

## <a name="resolving-overallocated-subscriptions"></a>Como resolver assinaturas superalocadas

Para resolver licenças superalocadas:

1. Clique no texto de alerta. Com isso, será exibida uma lista filtrada dos assinantes atribuídos ao nível de assinatura e a data de expiração da solicitação em excesso. 

2. Remova os assinantes conforme necessário para corrigir as licenças solicitadas em excesso. 

3. A visão geral no lado esquerdo da página será atualizada para mostrar que você está novamente em conformidade e todas as notificações de solicitação em excesso desaparecerão. 

## <a name="billing-and-true-up"></a>Adequação ("true-up") e cobrança

Se sua organização tiver um EA (Contrato Enterprise), os administradores poderão atribuir assinaturas sem comprá-las e pagar por elas mais tarde por meio de um processo de reconciliação, conhecido como adequação ("true-up").  Ao superalocar, sua organização será cobrada pelo número máximo de assinaturas atribuídas aos usuários durante a adequação ("true-up").  Isso acontecerá mesmo se você não tiver o número máximo de assinaturas atribuído no momento em que ocorrer a adequação ("true-up").  Para saber mais sobre como monitorar seu uso máximo, acesse o tópico [Uso máximo](maximum-usage.md).

> [!Important]
> Se as Assinaturas do Visual Studio com o GitHub Enterprise tiverem sido atribuídas por administradores de assinatura do Visual Studio e nunca houver acontecido uma compra dessas assinaturas, elas não estarão visíveis para administradores do GitHub Enterprise dentro da organização. Para garantir que as assinaturas do GitHub Enterprise estejam visíveis, uma compra incluindo **pelo menos um** Visual Studio Professional com o GitHub Enterprise ou o Visual Studio Enterprise com a assinatura do GitHub Enterprise deverá ser feita na primeira vez em que as assinaturas forem atribuídas.  
>
> É responsabilidade do cliente garantir que, para cada assinatura do GitHub atribuída, haja uma assinatura correspondente do Visual Studio com o GitHub atribuída no portal de gerenciamento para permanecer em conformidade com os requisitos de licenciamento para este assinatura.


Saiba mais sobre como gerenciar [Assinaturas do Visual Studio com o GitHub Enterprise](assign-github.md).

## <a name="support-resources"></a>Recursos de suporte
-  Para obter assistência com vendas, assinaturas, contas e cobrança para Assinaturas do Visual Studio, entre em contato com o [Suporte a Assinaturas](https://visualstudio.microsoft.com/subscriptions/support/) do Visual Studio.