---
title: Designer de Fluxo de Trabalho-selecionar designer de atividade
description: Saiba como a atividade de seleção fornece fluxo de controle baseado em evento e executa uma de várias ramificações em resposta a um evento de disparo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b616cf3d9b7eba5b2a2e9de23546a8a5f9c36ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968691"
---
# <a name="pick-activity-designer"></a>Escolha o designer de atividades

A atividade de <xref:System.Activities.Statements.Pick> fornece o fluxo de controle baseado. A atividade executa um dos vários ramificações em resposta a um evento disparando.

## <a name="the-pick-activity"></a>A atividade de picareta

Uma atividade de <xref:System.Activities.Statements.Pick> contém uma coleção de objetos <xref:System.Activities.Statements.PickBranch> , uma que a atividade de <xref:System.Activities.Statements.Pick> pode executar devido a qualquer evento de entrada que serve como um disparador. Dessa forma Designer de Fluxo de Trabalho fornece modelagem de fluxo de controle baseado em evento. Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A>. No início da execução de uma <xref:System.Activities.Statements.Pick> atividade, todas as atividades de gatilho dos <xref:System.Activities.Statements.PickBranch> elementos são agendadas. Quando a primeira atividade concluir, a atividade correspondente de ação está agendada, e quaisquer atividades restantes do disparador serão canceladas.

### <a name="how-to-use-the-pick-activity-designer"></a>Como usar o designer de atividade de picareta

Acesse o designer de atividade de **escolha** na categoria **fluxo de controle** da **caixa de ferramentas**. O designer de atividade de **escolha** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho onde os designers de atividade normalmente são colocados, por exemplo, dentro de um designer de atividade de **sequência** . Depois de soltá-lo em Designer de Fluxo de Trabalho, ele cria uma <xref:System.Activities.Statements.Pick> atividade, que por padrão contém duas atividades vazias <xref:System.Activities.Statements.PickBranch> como elementos com nomes de exibição de Branch1 e Branch2. Esses respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propriedade podem ser editados no cabeçalho do designer de atividade **PickBranch** ou na janela **Propriedades** de cada ramificação.

Há duas maneiras de adicionar <xref:System.Activities.Statements.PickBranch> atividades à coleção de um <xref:System.Activities.Statements.Pick> objeto: arrastando e soltando o designer **PickBranch** da **caixa de ferramentas** ou usando o menu de atalho de dentro da superfície de design de **escolha** . Para obter detalhes, consulte o tópico [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Observe que o único item que pode ser colocado dentro de um designer de atividade de **escolha** é um designer de atividade do **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Escolha propriedades de atividade em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Pick> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Pick> no cabeçalho. O valor padrão é picareta. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|

## <a name="see-also"></a>Confira também

- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
- [Escolher atividade](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Usando a atividade de Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)