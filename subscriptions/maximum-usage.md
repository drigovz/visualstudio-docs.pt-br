---
title: Usar o recurso de Uso Máximo no Portal de Administração
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/24/2019
ms.topic: conceptual
description: Saiba como exibir o número máximo de assinaturas atribuídas no portal de administração
ms.openlocfilehash: 15ef4acf8bd02ec4846f387fdce3a9882585a64a
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605483"
---
# <a name="use-the-maximum-usage-feature-to-track-the-number-of-assigned-subscriptions"></a>Usar o recurso de Uso Máximo para controlar o número de assinaturas atribuídas
Um novo recurso no portal de administração de assinaturas do Visual Studio ajuda a acompanhar quantas assinaturas você adquiriu e atribuiu e identifica o número máximo de assinaturas de cada nível que você atribuiu, no ano passado e por toda a duração dos seus contratos. 

## <a name="view-your-maximum-usage"></a>Exibir seu uso máximo
Para ver o número máximo de assinaturas atribuídas para qualquer nível de assinatura e de contrato:
1. Selecione o contrato que você deseja exibir na lista suspensa na parte superior esquerda do portal. (Se você tiver apenas um único contrato, ele já estará selecionado.)
2. Clique na guia **Uso Máximo**.  
    > [!div class="mx-imgBorder"]
    > ![Menu Uso Máximo](_img/maximum-usage/maximum-usage-menu.png)
3. O "Resumo de Uso Máximo" será exibido e o número máximo de assinaturas que você atribuiu no último ano para cada nível será exibido junto com a data em que você atingiu esse pico.  Se você atingiu o pico mais de uma vez, a primeira vez em que você chegou a ele será exibida. 
    > [!div class="mx-imgBorder"]
    > ![Resumo de Uso Máximo](_img/maximum-usage/maximum-usage-summary.png)
4. Para ver o número máximo de assinaturas atribuídas durante a vida útil do contrato, clique na guia **Termo completo**.

## <a name="view-your-assignment-history"></a>Exibir o histórico de atribuições
Além de ver o pico de atribuições para cada nível de assinatura, você pode ver uma conta em execução da atividade no contrato, incluindo compras e atribuições, clicando no botão **Exportar o relatório completo**.  

> [!div class="mx-imgBorder"]
> ![Relatório Completo do Uso Máximo](_img/maximum-usage/maximum-usage-full-report.png)

Para cada nível de assinatura, o relatório mostra a data em que você atingiu um novo nível de atribuição máxima e o número de assinaturas que você comprou a partir dessa data, permitindo que você veja facilmente qualquer uma das datas em que você tinha superalocações.  

Por exemplo, na tabela acima, você pode ver que no dia 13/12/2018 havia 123 assinaturas do Visual Studio Enterprise no contrato e 120 foram atribuídas.  Em 8/1/2019, foi atribuída mais uma assinatura, elevando o total para 121.  No dia seguinte, outras seis assinaturas foram atribuídas e outro quatro assinaturas foram adicionadas ao contrato para cobrir as novas atribuições.  

## <a name="frequently-asked-questions"></a>Perguntas frequentes
### <a name="q-how-is-the-information-in-the-maximum-usage-different-from-the-assignment-information-available-in-the-overview-section-on-the-left-side-of-the-portal"></a>P: Como as informações de uso máximo são diferentes das informações de atribuição disponíveis na seção "Visão geral" no lado esquerdo do portal?
R:  As informações na visão geral mostram as atribuições *atuais* e as assinaturas disponíveis para cada nível de assinatura.  Isso pode ser muito diferente do número máximo de assinaturas atribuídas para o contrato durante o ano atual ou a vida útil do contrato.  O recurso de Uso Máximo permite que você veja quando os níveis máximos de atribuição foram atingidos e quais foram esses níveis.  Essa é uma distinção importante, já que a cobrança de assinaturas durante a adequação ("true-up") é baseada no número máximo de assinaturas atribuídas a qualquer momento ao longo do ano. 

## <a name="resources"></a>Recursos
- [White paper de licenciamento do Visual Studio](https://aka.ms/vslicensing)
- [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Termos de licenciamento por volume](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="next-steps"></a>Próximas etapas
- Se você tiver alguma dúvida sobre atribuições de assinatura ou em outros aspectos do portal de administração, entre em contato com https://visualstudio.microsoft.com/subscriptions/support/ para obter assistência. 
- Saiba mais sobre o que fazer se você atribuir mais assinaturas que comprou, chamadas de [superalocações](handle-overclaimed-license.md).
