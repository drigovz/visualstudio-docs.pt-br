---
title: Atrasar designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656792"
---
# <a name="delay-activity-designer"></a>Atrasar o designer de atividades
O designer de atividade de **atraso** é usado para criar e configurar uma <xref:System.Activities.Statements.Delay> atividade.

## <a name="the-delay-activity"></a>A atividade do atraso
 A atividade de <xref:System.Activities.Statements.Delay> atrasa a execução de um fluxo de trabalho para uma quantidade de tempo especificada.

### <a name="using-the-delay-activity-designer"></a>Usando o designer de atividade do atraso
 O designer de atividade de **atraso** pode ser encontrado na categoria **primitivos** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** do [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade de **atraso** pode ser arrastado da **caixa de ferramentas** e descartado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma atividade de <xref:System.Activities.Statements.Delay> com uma opção <xref:System.Activities.Activity.DisplayName%2A> de atraso. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **atraso** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-delay-properties"></a>As propriedades do atraso
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Delay> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e alguns deless podem ser editados na superfície do designer de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome da propriedade|Obrigatório|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.Delay> . O padrão é atraso. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Verdadeiro|A quantidade de tempo para atrasar o fluxo de trabalho. Essa propriedade é definida na grade de propriedade. Digite qualquer um <xref:System.TimeSpan> literal no 00:00 de formato: 00 ou uma expressão do Visual Basic para especificar a quantidade de tempo.|

## <a name="see-also"></a>Consulte Também
 [Primitivas](../workflow-designer/primitives-activity-designers.md) [atribuir](../workflow-designer/assign-activity-designer.md) [atraso do designer de atividade](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)