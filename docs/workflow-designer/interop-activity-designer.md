---
title: Designer de atividade de interoperabilidade Designer de Fluxo de Trabalho
description: Saiba mais sobre o Interop Activity Designer e como você pode usar o Interop Activity Designer para criar e configurar uma atividade de interoperabilidade.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4a45187f01469f568a98098a8470ad62f67307a6
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437769"
---
# <a name="interop-activity-designer"></a>Designer de atividade de Interoperabilidade

O **Interop** Activity Designer é usado para criar e configurar uma <xref:System.Activities.Statements.Interop> atividade.

## <a name="the-interop-activity"></a>A atividade de Interoperabilidade

A atividade de <xref:System.Activities.Statements.Interop> gerencia a execução de tipos que derivam de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> em um fluxo de trabalho.

### <a name="use-the-interop-activity-designer"></a>Usar o Interop Activity Designer

O **Interop** Activity Designer pode ser encontrado na categoria **migração** da caixa de **ferramentas** , que é acessada clicando na guia **caixa de ferramentas** . Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** + **ALT** + **X**.

A categoria de [migração](../workflow-designer/migration-activity-designers.md) que contém a <xref:System.Activities.Statements.Interop> atividade só aparecerá na **caixa de ferramentas** se seu projeto estiver direcionado .NET Framework 4 (completo) ou posterior. Se necessário, você pode alterar a versão do Framework que seu projeto tem como destino.

O **Interop** Activity Designer pode ser arrastado da **caixa de ferramentas** e descartado na superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Descartar o **Interop** Activity Designer cria uma <xref:System.Activities.Statements.Interop> atividade com um **DisplayName** padrão de Interop. Você pode editar o <xref:System.Activities.Activity.DisplayName%2A> no cabeçalho do designer de atividade de **interoperabilidade** ou na caixa **DisplayName** da grade de propriedades.

Clique no **clique para procurar** o texto na caixa **ActivityType** , seja no designer de atividade de **interoperabilidade**  ou na grade de propriedades, para abrir a caixa de diálogo **procurar e selecionar um tipo .net** . Somente os tipos de fluxo de trabalho 3,0 ou atividades do fluxo de trabalho 3,5 são mostrados. Ou seja, somente os tipos derivados de <xref:System.Workflow.ComponentModel.Activity> são mostrados. Para obter mais informações sobre como usar essa caixa para especificar um tipo, consulte [procurar e selecionar uma caixa de diálogo de tipo .net](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>As propriedades de Interoperabilidade

A tabela a seguir mostra as <xref:System.Activities.Statements.Interop> Propriedades e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades ou na superfície de Designer de Fluxo de Trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.Interop> . O valor padrão é **Interop**. Embora o nome de exibição não seja necessário, é recomendável fornecer um.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Verdadeiro|Especifica o tipo de atividade contida pela atividade de <xref:System.Activities.Statements.Interop> . Este tipo especificado deve derivar de <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Confira também

- [Migração](../workflow-designer/migration-activity-designers.md)