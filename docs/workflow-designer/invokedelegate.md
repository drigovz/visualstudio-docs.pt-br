---
title: Designer de Fluxo de Trabalho-InvokeDelegate
description: Saiba mais sobre o InvokeDelegate designer e como você pode usar o InvokeDelegate designer para criar e configurar uma atividade de InvokeDelegate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: a482f23b1df1587e9a1c7e3023bfb0d1737f1fae
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437743"
---
# <a name="invokedelegate"></a>InvokeDelegate

O designer de **InvokeDelegate** é usado para criar e configurar uma <xref:System.Activities.Statements.InvokeDelegate> atividade.

## <a name="the-invokedelegate-activity"></a>A atividade InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> chama um delegate público.

### <a name="use-the-invokedelegate-activity-designer"></a>Usar o designer de atividade do InvokeDelegate

Acesse o designer de atividade do **InvokeDelegate** na categoria **primitivos** da **caixa de ferramentas**. O designer de atividade do **InvokeDelegate** pode ser arrastado da **caixa de ferramentas** e colocado na superfície de designer de fluxo de trabalho, onde as atividades sempre são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Descartar o designer de atividade cria uma <xref:System.Activities.Statements.InvokeDelegate> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de InvokeDelegate. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **InvokeDelegate** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-invokedelegate-properties"></a>As propriedades InvokeDelegate

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.InvokeDelegate> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas podem ser editadas na superfície Designer de Fluxo de Trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.InvokeDelegate> . O valor padrão é InvokeDelegate.<br /><br /> Embora o <xref:System.Activities.Activity.DisplayName%2A> não seja estritamente necessário, é melhor usar um.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Verdadeiro|O nome de <xref:System.Activities.ActivityDelegate> a ser chamado quando a atividade executar. Essa propriedade pode ser editada na superfície do designer e é obrigatória.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Falso|A coleção de argumento de representante chamado. As chaves são os nomes dos objetos de parâmetro no <xref:System.Activities.ActivityDelegate> , e os valores são os argumentos cujas expressões são avaliadas e atribuídas aos objetos de parâmetro correspondentes. Para exibir a caixa de diálogo **DelegateArguments** em que você pode definir essa propriedade, clique no botão de reticências no campo **DelegateArguments** da grade de propriedades. Clique no campo **criar argumento** para adicionar os argumentos.|

## <a name="see-also"></a>Confira também

- [Como: Defina e consumir representantes de atividade em Designer de Fluxo de Trabalho](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)