---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659014"
---
# <a name="invokedelegate"></a>InvokeDelegate

O designer de **InvokeDelegate** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>A atividade de InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> chama um delegate público.

### <a name="using-the-invokedelegate-activity-designer"></a>Usando o designer de atividade de InvokeDelegate

O designer de atividade do **InvokeDelegate** pode ser encontrado na categoria **primitivos** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione barra de **ferramentas** no menu **Exibir** ou CRTL + ALT + X.)

O designer de atividade do **InvokeDelegate** pode ser arrastado da **caixa de ferramentas** e colocado na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)], onde as atividades sempre são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.InvokeDelegate> com <xref:System.Activities.Activity.DisplayName%2A> padrão de InvokeDelegate. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **InvokeDelegate** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-invokedelegate-properties"></a>As propriedades de InvokeDelegate

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.InvokeDelegate> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície do designer de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.InvokeDelegate> . O valor padrão é InvokeDelegate.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|verdadeiro|O nome de <xref:System.Activities.ActivityDelegate> a ser chamado quando a atividade executar. Esta propriedade pode ser editada na superfície de designer. Esta é uma propriedade imperativa.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|A coleção de argumento de representante chamado. As chaves são os nomes dos objetos de <xref:System.Activities.DelegateArgument> em <xref:System.Activities.ActivityDelegate> e valores são os argumentos cujas ambas as expressões são avaliadas e atribuídas a <xref:System.Activities.DelegateArgument> os objetos correspondentes. Na grade de propriedades, clique no botão de reticências no campo **DelegateArguments** , que exibe a caixa de diálogo **DelegateArguments** para permitir que você defina essa propriedade. Clique no campo **criar argumento** para adicionar os argumentos.|

## <a name="see-also"></a>Consulte também

- [Como definir e consumir delegados de atividade no Designer de Fluxo de Trabalho](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)