---
title: Designer de atividade Designer de Fluxo de Trabalho-Persist
description: Saiba mais sobre a atividade de persistência e como usar o designer de atividade de persistência para criar e configurar uma atividade de persistência.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3daa7cef76d2448cc7bcda66a967a3406bb2352c
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435567"
---
# <a name="persist-activity-designer"></a>Persistir o designer de atividades

O designer de atividade de **persistência** é usado para criar e configurar uma <xref:System.Activities.Statements.Persist> atividade.

## <a name="the-persist-activity"></a>A atividade persistir

A atividade de <xref:System.Activities.Statements.Persist> salva um fluxo de trabalho em disco, se possível. A atividade de <xref:System.Activities.Statements.Persist> não pode ser executada em uma zona de não persistência como, por exemplo, em uma atividade de <xref:System.Activities.Statements.TransactionScope> . Se você usar uma <xref:System.Activities.Statements.Persist> atividade em um escopo sem persistência, uma exceção será lançada em tempo de execução.

### <a name="using-the-persist-activity-designer"></a>Usando o designer de atividade de persistir

O designer de atividade de **persistência** pode ser encontrado na categoria **tempo de execução** da **caixa de ferramentas** , que é acessada clicando na guia caixa de **ferramentas** (como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou CTRL + ALT + X).

O designer de atividade de **persistência** pode ser arrastado da **caixa de ferramentas** e colocado na superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma <xref:System.Activities.Statements.Persist> atividade com um **DisplayName** padrão de persist. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **persistência** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-persist-properties"></a>As propriedades persistir

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Persist> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas delas podem ser editadas na superfície Designer de Fluxo de Trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.Persist> . O padrão é persiste. Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|

## <a name="see-also"></a>Confira também

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
