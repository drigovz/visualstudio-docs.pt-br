---
title: Persistir o designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60a63dd4036863641646e85a89f5018cba786802
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672619"
---
# <a name="persist-activity-designer"></a>Persistir o designer de atividades
O designer de atividade de **persistência** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Persist>.

## <a name="the-persist-activity"></a>A atividade persistir
 A atividade de <xref:System.Activities.Statements.Persist> salva um fluxo de trabalho em disco, se possível. A atividade de <xref:System.Activities.Statements.Persist> não pode ser executada em uma zona de não persistência como, por exemplo, em uma atividade de <xref:System.Activities.Statements.TransactionScope> . Se você usar uma atividade de <xref:System.Activities.Statements.Persist> em um escopo de não persistência, uma exceção é lançada em tempo de execução.

### <a name="using-the-persist-activity-designer"></a>Usando o designer de atividade de persistir
 O designer de atividade de **persistência** pode ser encontrado na categoria **tempo de execução** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** (como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou CTRL + ALT + X).

 O designer de atividade de **persistência** pode ser arrastado da **caixa de ferramentas** e colocado na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.Persist> com um **DisplayName** padrão de persistir. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **persistência** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-persist-properties"></a>As propriedades persistir
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Persist> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e algumas delass podem ser editadas na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Persist> . O padrão é persiste. Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|

## <a name="see-also"></a>Consulte também
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [de tempo de execução](../workflow-designer/runtime-activity-designers.md)