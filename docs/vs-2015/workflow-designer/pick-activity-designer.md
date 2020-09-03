---
title: Escolher designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672592"
---
# <a name="pick-activity-designer"></a>Escolha o designer de atividades
A atividade de <xref:System.Activities.Statements.Pick> fornece o fluxo de controle baseado. A atividade executa um dos vários ramificações em resposta a um evento disparando.

## <a name="the-pick-activity"></a>A atividade de picareta
 Uma atividade de <xref:System.Activities.Statements.Pick> contém uma coleção de objetos <xref:System.Activities.Statements.PickBranch> , uma que a atividade de <xref:System.Activities.Statements.Pick> pode executar devido a qualquer evento de entrada que serve como um disparador. Dessa forma [!INCLUDE[wfd1](../includes/wfd1-md.md)] fornece a modelagem com base em eventos de fluxo de controle. Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A>. No início da execução de uma atividade de <xref:System.Activities.Statements.Pick> , todas as atividades do disparador de elementos de <xref:System.Activities.Statements.PickBranch> são agendadas. Quando a primeira atividade concluir, a atividade correspondente de ação está agendada, e quaisquer atividades restantes do disparador serão canceladas.

### <a name="how-to-use-the-pick-activity-designer"></a>Como usar o designer de atividade de picareta
 O designer de atividade de **escolha** pode ser encontrado na categoria **fluxo de controle** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** em [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade de **escolha** pode ser arrastado da **caixa de ferramentas** e descartado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície onde os designers de atividade normalmente são colocados, por exemplo, dentro de um designer de atividade de **sequência** . Após solto na [!INCLUDE[wfd2](../includes/wfd2-md.md)], cria uma atividade de <xref:System.Activities.Statements.Pick> , que contém por padrão duas atividades vazios de <xref:System.Activities.Statements.PickBranch> como elementos com nomes para exibição de Branch1 e de Branch2. Esses respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propriedade podem ser editados no cabeçalho do designer de atividade **PickBranch** ou na janela **Propriedades** de cada ramificação.

 Há duas maneiras de adicionar <xref:System.Activities.Statements.PickBranch> atividades à coleção de um <xref:System.Activities.Statements.Pick> objeto: arrastar e soltar o **PickBranch** designer da **caixa de ferramentas** ou usando o menu de contexto de dentro da superfície de design de **escolha** . Para obter detalhes, consulte o tópico [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Observe que o único item que pode ser colocado dentro de um designer de atividade de **escolha** é um designer de atividade do **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Escolha propriedades de atividade em Designer de Fluxo de Trabalho
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Pick> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.

|Nome da propriedade|Obrigatório|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Pick> no cabeçalho. O valor padrão é picareta. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|

## <a name="see-also"></a>Consulte Também
 [Atividade](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [de seleção de fluxo de controle usando a atividade de seleção](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6) [Control Flow](../workflow-designer/control-flow-activity-designers.md)