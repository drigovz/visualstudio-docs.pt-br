---
title: Designer de atividade de interoperabilidade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659032"
---
# <a name="interop-activity-designer"></a>Designer de atividade de Interoperabilidade
O **Interop** Activity Designer é usado para criar e configurar uma <xref:System.Activities.Statements.Interop> atividade.

## <a name="the-interop-activity"></a>A atividade de Interoperabilidade
 A atividade de <xref:System.Activities.Statements.Interop> gerencia a execução de tipos que derivam de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> em um fluxo de trabalho.

### <a name="using-the-interop-activity-designer"></a>Usando o designer de atividade de Interoperabilidade
 O **Interop** Activity Designer pode ser encontrado na categoria **migração** da caixa de **ferramentas**, que é acessada clicando na guia **caixa de ferramentas** (como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 A categoria de [migração](../workflow-designer/migration-activity-designers.md) que contém a <xref:System.Activities.Statements.Interop> atividade só aparecerá na **caixa de ferramentas** se o seu projeto estiver direcionando para o todo [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] .

 Para projetos C#, você pode redirecionar o projeto para usar o completo [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] clicando com o botão direito do mouse no projeto no **Gerenciador de soluções** e selecionando **Propriedades**. Na guia **aplicativo** , selecione a opção **NET Framework 4** na estrutura de **destino**. Selecione o botão **Sim** na caixa de diálogo de **alteração da estrutura de destino** que é exibida solicitando que você confirme essa alteração.

 Para projetos do VB, você pode redirecionar o projeto para usar o completo clicando com o [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] botão direito do mouse no projeto no **Gerenciador de soluções** e selecionando **Propriedades**. Na guia **Compilar** , clique no botão **Opções avançadas de compilação** . Selecione **.NET Framework 4** na **lista estrutura de destino** e clique em **OK**. Clique no botão **Sim** na caixa de diálogo de **alteração da estrutura de destino** que é exibida solicitando que você confirme essa alteração.

 O **Interop** Activity Designer pode ser arrastado da **caixa de ferramentas** e retirado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma <xref:System.Activities.Statements.Interop> atividade com um **DisplayName** padrão de Interop. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **interoperabilidade** ou na caixa **DisplayName** da grade de propriedades.

 Clique no **clique para procurar...** texto na caixa **ActivityType** , seja no designer de atividade de **interoperabilidade**  ou na grade de propriedades, para exibir a caixa de diálogo **procurar e selecionar um tipo .net** . Somente tipos para os trabalhos 3,0 ou o trabalho 3,5 atividades são mostrados (isto é, somente os tipos derivados de <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] usando essa caixa para especificar um tipo, consulte a [caixa de diálogo Procurar e selecionar um tipo de .net](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) .

### <a name="the-interop-properties"></a>As propriedades de Interoperabilidade
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Interop> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Nome da propriedade|Obrigatório|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.Interop> . O padrão é Interoperabilidade. Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Verdadeiro|Especifica o tipo de atividade contida pela atividade de <xref:System.Activities.Statements.Interop> . Este tipo especificado deve derivar de <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Consulte Também
 [Migração](../workflow-designer/migration-activity-designers.md)