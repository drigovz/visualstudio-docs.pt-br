---
title: Designer de atividade Designer de Fluxo de Trabalho-TerminateWorkflow
description: Saiba como você pode usar o designer de atividade TerminateWorkflow para criar e configurar uma atividade TerminateWorkflow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5af1f8656e796d9551e1d140b07868551d563a90
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433863"
---
# <a name="terminateworkflow-activity-designer"></a>Designer de atividade de TerminateWorkflow

O designer de atividade **TerminateWorkflow** é usado para criar e configurar uma <xref:System.Activities.Statements.TerminateWorkflow> atividade.

## <a name="the-terminateworkflow-activity"></a>A atividade de TerminateWorkflow

A atividade de <xref:System.Activities.Statements.TerminateWorkflow> finaliza a execução de um fluxo de trabalho.

### <a name="using-the-terminateworkflow-activity-designer"></a>Usando o designer de atividade de TerminateWorkflow

O designer de atividade do **TerminateWorkflow** pode ser encontrado na categoria **tempo de execução** da **caixa de ferramentas** , que é acessada clicando na guia caixa de **ferramentas** (como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou CTRL + ALT + X).

O designer de atividade do **TerminateWorkflow** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma <xref:System.Activities.Statements.TerminateWorkflow> atividade com um **DisplayName** padrão de TerminateWorkflow. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **TerminateWorkflow** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-terminateworkflow-properties"></a>As propriedades de TerminateWorkflow

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.TerminateWorkflow> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas delas podem ser editadas na superfície Designer de Fluxo de Trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.TerminateWorkflow> . O padrão é TerminateWorkflow. Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Falso|A exceção para indicar quando o fluxo de trabalho é encerrado. Defina essa propriedade na grade de propriedade.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Falso|A razão que explica como o fluxo de trabalho foi encerrado. Defina essa propriedade na grade de propriedade.|

## <a name="see-also"></a>Confira também

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [Persistir](../workflow-designer/persist-activity-designer.md)
