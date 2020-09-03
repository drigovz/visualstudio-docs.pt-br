---
title: Designer de atividade Designer de Fluxo de Trabalho-TryCatch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b70f1d3174990ec12c621dff4a45ce4d899ceb4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593064"
---
# <a name="trycatch-activity-designer"></a>Designer de atividade de TryCatch

O designer de atividade **TryCatch** é usado para criar e configurar uma <xref:System.Activities.Statements.TryCatch> atividade.

## <a name="the-trycatch-activity"></a>A atividade de TryCatch
 A <xref:System.Activities.Statements.TryCatch> atividade contém uma <xref:System.Activities.Statements.TryCatch.Try%2A> atividade, uma coleção de **Catch \<TException> ** e uma <xref:System.Activities.Statements.TryCatch.Finally%2A> atividade. Um <xref:System.Activities.Statements.Catch%601> do tipo **TException** contém um <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> e um <xref:System.Activities.Statements.Catch%601.Action%2A> . São usados juntos para implementar um mecanismo exceção baseado típico de manipulação de erro. Uma atividade de <xref:System.Activities.Statements.TryCatch> tentar executar a atividade de <xref:System.Activities.Statements.TryCatch.Try%2A> . Se a <xref:System.Activities.Statements.TryCatch.Try%2A> atividade lançar qualquer exceção, a <xref:System.Activities.Statements.TryCatch> atividade usará seu **Catch<\> coleção TException** para corresponder à exceção. Se houver uma correspondência, o <xref:System.Activities.Statements.Catch%601.Action%2A> do ** \<TException> Catch** correspondente será executado, servindo como a lógica de tratamento de erros para a exceção. Se as atividades na seção de <xref:System.Activities.Statements.TryCatch.Try%2A> completa com êxito ou as atividades em <xref:System.Activities.Statements.TryCatch.Catches%2A> completa com êxito, a atividade de <xref:System.Activities.Statements.TryCatch> executa sua atividade de <xref:System.Activities.Statements.TryCatch.Finally%2A> . Para obter mais informações, consulte [exceções de fluxo de trabalho do Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Usando o designer de atividade de TryCatch

Acesse o designer de atividade **TryCatch** na categoria **tratamento de erros** da **caixa de ferramentas**.

O designer de atividade **TryCatch** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma atividade de <xref:System.Activities.Statements.TryCatch> com <xref:System.Activities.Activity.DisplayName%2A> padrão de TryCatch. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do designer de atividade **TryCatch** ou na caixa **DisplayName** da grade de propriedades. As outras propriedades devem ser editadas na superfície do designer de atividade **TryCatch** .

Clique no botão expandir no canto superior direito do **TryCatch** designer para ver as caixas **try**, **Catch**e **finally** na exibição expandida. Para adicionar um catch, clique no botão **Adicionar nova captura** no **TryCatch** designer. O botão muda para uma caixa de combinação de tipo. Selecione um tipo de exceção e pressione ENTER para adicionar a captura. Depois de adicionar um **Catch**, a área de captura se expande e uma atividade pode ser removida para o catch para definir a lógica de execução para o catch. Observe que há uma caixa de texto no lado direito da área expandida catch. Você pode nomear a variável de exceções usando esta caixa de texto. A variável de exceção só pode ser usada para atividades dentro do mesmo **Catch**.

O designer **TryCatch** não oferece suporte à edição **Catch**. Se você quiser alterar o tipo de exceção, será necessário excluir o **Catch** e adicionar um novo. Um **Catch** pode ser excluído selecionando-o e excluindo-o ou selecionando **excluir** no menu de contexto que é acessado clicando com o botão direito do mouse.

### <a name="the-trycatch-properties"></a>As propriedades de TryCatch

A tabela a seguir mostra as <xref:System.Activities.Statements.TryCatch> Propriedades e descreve como elas são usadas no designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.TryCatch> . O padrão é TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Falso|A atividade executada primeiro quando <xref:System.Activities.Statements.TryCatch> executar.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Falso|A coleção de elementos **Catch** a ser verificada quando a <xref:System.Activities.Statements.TryCatch.Try%2A> atividade gera uma exceção.<br /><br /> Você precisa pelo menos de adicionar uma atividade em <xref:System.Activities.Statements.TryCatch.Catches%2A> ou uma atividade no bloco de <xref:System.Activities.Statements.TryCatch.Finally%2A> .|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Falso|A atividade a ser executada quando <xref:System.Activities.Statements.TryCatch.Try%2A> e todas as atividades necessárias na coleção de <xref:System.Activities.Statements.TryCatch.Catches%2A> tiver terminado a execução.<br /><br /> Você precisa pelo menos de adicionar uma atividade em <xref:System.Activities.Statements.TryCatch.Catches%2A> ou uma atividade no bloco de <xref:System.Activities.Statements.TryCatch.Finally%2A> .|

## <a name="see-also"></a>Confira também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [Relançar](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
