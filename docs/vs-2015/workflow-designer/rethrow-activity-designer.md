---
title: Relançar designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c65469242a60c64d6f31bfaea4fdbbf2d5251a34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663366"
---
# <a name="rethrow-activity-designer"></a>Designer de atividade de Relançar
O designer de atividade **Rethrow** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Rethrow>.

## <a name="the-rethrow-activity"></a>A atividade de Relançar
 A atividade de <xref:System.Activities.Statements.Rethrow> lança uma exceção lançada anteriormente. Esta atividade somente pode ser usada em um manipulador de <xref:System.Activities.Statements.Catch> na atividade de <xref:System.Activities.Statements.TryCatch> .

### <a name="using-the-rethrow-activity-designer"></a>Usando o designer de atividade de Relançar
 O designer de atividade **Rethrow** pode ser encontrado na **categoria tratamento de erros** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** no lado esquerdo da [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione barra de **ferramentas** no  **Menu Exibir** ou CTRL + ALT + X.)

 O designer de atividade **Rethrow** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.Rethrow> com um **DisplayName** padrão de Throw. O valor <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **Rethrow** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-rethrow-properties"></a>As propriedades de Relançar
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Rethrow> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Rethrow> . O padrão é Relançar.|

## <a name="see-also"></a>Consulte também
 [Coleção](../workflow-designer/collection-activity-designers.md) [throws](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)