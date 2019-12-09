---
title: Designer de atividade de interoperabilidade Designer de Fluxo de Trabalho
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650203"
---
# <a name="interop-activity-designer"></a>Designer de atividade de Interoperabilidade

O **Interop** Activity Designer é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Interop>.

## <a name="the-interop-activity"></a>A atividade de Interoperabilidade

A atividade de <xref:System.Activities.Statements.Interop> gerencia a execução de tipos que derivam de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> em um fluxo de trabalho.

### <a name="use-the-interop-activity-designer"></a>Usar o Interop Activity Designer

O **Interop** Activity Designer pode ser encontrado na categoria **migração** da caixa de **ferramentas**, que é acessada clicando na guia **caixa de ferramentas** . como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** +**ALT** +**X**.

A categoria de [migração](../workflow-designer/migration-activity-designers.md) que contém a atividade de <xref:System.Activities.Statements.Interop> só aparecerá na **caixa de ferramentas** se seu projeto tiver como alvo .NET Framework 4 (completo) ou posterior. Se necessário, você pode alterar a versão do Framework que seu projeto tem como destino.

O **Interop** Activity Designer pode ser arrastado da **caixa de ferramentas** e descartado na superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Descartar o **Interop** Activity Designer cria uma atividade de <xref:System.Activities.Statements.Interop> com um **DisplayName** padrão de Interop. Você pode editar o <xref:System.Activities.Activity.DisplayName%2A> no cabeçalho do designer de atividade de **interoperabilidade** ou na caixa **DisplayName** da grade de propriedades.

Clique no **clique para procurar** o texto na caixa **ActivityType** , seja no designer de atividade de **interoperabilidade** ou na grade de propriedades, para abrir a caixa de diálogo **procurar e selecionar um tipo .net** . Somente os tipos de fluxo de trabalho 3,0 ou atividades do fluxo de trabalho 3,5 são mostrados. Ou seja, somente os tipos derivados de <xref:System.Workflow.ComponentModel.Activity> são mostrados. Para obter mais informações sobre como usar essa caixa para especificar um tipo, consulte [procurar e selecionar uma caixa de diálogo de tipo .net](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>As propriedades de Interoperabilidade

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Interop> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades ou na superfície de Designer de Fluxo de Trabalho.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Interop> . O valor padrão é **Interop**. Embora o nome de exibição não seja necessário, é recomendável fornecer um.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|verdadeiro|Especifica o tipo de atividade contida pela atividade de <xref:System.Activities.Statements.Interop> . Este tipo especificado deve derivar de <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Consulte também

- [Migração](../workflow-designer/migration-activity-designers.md)