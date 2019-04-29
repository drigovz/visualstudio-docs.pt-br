---
title: Designer de atividade Throw | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db909618971eeab2d92506d1c29b06290aa9263b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976625"
---
# <a name="throw-activity-designer"></a>Lance o designer de atividades
O **lançar** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Throw> atividade.  
  
## <a name="the-throw-activity"></a>A atividade throw  
 A atividade de <xref:System.Activities.Statements.Throw> gerencie uma exceção.  
  
### <a name="using-the-throw-activity-designer"></a>Usando o designer de atividade throw  
 O **lançar** designer de atividade pode ser encontrado na **tratamento de erros** categoria da **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas**guia no lado esquerdo do [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu, ou CTRL + ALT + X.)  
  
 O **lançar** designer de atividade pode ser arrastado da **caixa de ferramentas** e ser solto sobre a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície onde quer que as atividades são colocadas em geral, como em um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.Throw> atividade com um padrão **DisplayName** throw. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **lançar** designer de atividade ou nos **DisplayName** caixa da grade de propriedade. A propriedade de <xref:System.Activities.Statements.Throw.Exception%2A> deve ser editada na grade de propriedade.  
  
### <a name="the-throw-properties"></a>As propriedades throw  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Throw> e descreve como elas são usadas no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Throw> . O padrão é throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|verdadeiro|A exceção para lançar. Esta exceção deve derivar de <xref:System.Exception>. Para especificar a exceção, digite uma expressão do Visual Basic na grade de propriedade.|  
  
## <a name="see-also"></a>Consulte também  
 [coleção](../workflow-designer/collection-activity-designers.md)   
 [Relançar](../workflow-designer/rethrow-activity-designer.md)   
 [Designer de atividade Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)