---
title: 'Como: usar a navegação por trilha | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c01e48e6aa34513e57b373150c605cb0a7f5b18
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659151"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Como: Use a navegação de rastreamento
Existem três maneiras principais de alterar o conjunto de atividades que são exibidas em [!INCLUDE[wfd1](../includes/wfd1-md.md)]:

1. Clique duas vezes para furar na uma atividade filho.

2. Clique em um botão na barra de rastreamento para navegar em uma atividade de ancestral.

3. Expandir ou recolher atividades no lugar.

### <a name="using-breadcrumb-navigation"></a>Usando a navegação de rastreamento

1. Clique duas vezes em uma atividade de [!INCLUDE[wfd2](../includes/wfd2-md.md)] para alterar a atividade raiz a atividade clicado. A atividade clicada completa é expandida na raiz e seus ancestrais são mostrados na barra de rastreamento. Isso é às vezes chamado perfuração ou de uma atividade.

2. Para navegar a um predecessor de atividade atual da raiz, clique na atividade na barra de rastreamento.

### <a name="expanding-or-collapsing-an-activity-in-place"></a>Expandindo ou recolhendo uma atividade no lugar

1. Clique nas vigas em uma atividade expande ou recolhe a atividade no lugar.

2. Quando o estado do estado de expansão é alterado clicando no botão, o novo estado de expansão é salvo em XAML.

    > [!WARNING]
    > Nem todas as atividades podem ser expandidos no lugar. Há dois casos quando uma atividade não pode ser expandida no local: ou o pai da atividade não permite seus filhos sejam expandidos no lugar, (por exemplo, as atividades em um fluxograma não podem ser expandidos no local), ou o designer de atividade não se permite que é expandido no lugar. Embora nenhum dos designers atividade estão incluídos em [!INCLUDE[wfd2](../includes/wfd2-md.md)] tenham o último comportamento, quaisquer atividades personalizados podem exibir esse comportamento.

### <a name="expanding-all-or-collapsing-all-activities"></a>Tudo expandir ou recolher todas as atividades

1. Use os botões **expandir tudo** e **recolher tudo** na interface do usuário para expandir ou recolher todas as atividades na raiz de navegação estrutural atual. Observe que expande todas e recolhe todo é estados globais. Isso significa que, quando você altera a atividade raiz usando a navegação estrutural, o estado expandir tudo ou recolher tudo persiste até que você clique em **restaurar**.

2. Depois de aplicar um estado expandir tudo ou recolher tudo, você pode clicar no botão **restaurar** que aparece para voltar ao exame do estado aplicado anteriormente a cada atividade.

    > [!WARNING]
    > Se uma atividade, como <xref:System.Activities.Statements.Flowchart>, tiver optado por expansão em vigor, a funcionalidade associada aos botões **expandir tudo** e **recolher tudo** será desabilitada no designer de **fluxograma** . [!INCLUDE[crabout](../includes/crabout-md.md)] o designer de **fluxograma** , consulte o tópico [fluxograma](../workflow-designer/flowchart-activity-designer.md) .

    > [!WARNING]
    > Expandir tudo também tem um efeito especial nos designers de atividade **switch** e **TryCatch** . Quando você clica em **expandir tudo**, todos os casos de comutador e todos os blocos try/catch/finally são exibidos. Clicar em **restaurar** ou **recolher todos** retorna esses designers ao seu estado padrão, no qual você pode clicar em um caso/bloco individual para exibir seu conteúdo.