---
title: Designer de atividade do PickBranch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7c70aa8282fb8f50ed6faca5bcee3177ef81e15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672579"
---
# <a name="pickbranch-activity-designer"></a>Designer de atividade de PickBranch
<xref:System.Activities.Statements.PickBranch> fornece um caminho de execução baseado em uma atividade de <xref:System.Activities.Statements.Pick> que pode ser acionada por um evento de entrada.

## <a name="pickbranch"></a>PickBranch
 <xref:System.Activities.Statements.PickBranch> os objetos estão contidos na <xref:System.Activities.Statements.Pick.Branches%2A> coleção de uma <xref:System.Activities.Statements.Pick> atividade. Cada <xref:System.Activities.Statements.PickBranch> está contido em uma ramificação de atividade de <xref:System.Activities.Statements.Pick> e pode ser executado devido a qualquer evento de entrada que serve como um disparador. Dessa forma [!INCLUDE[wfd1](../includes/wfd1-md.md)] fornece a modelagem com base em eventos de fluxo de controle. Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Como usar o designer de atividade de picareta
 O designer de **PickBranch** pode ser encontrado na categoria **fluxo de controle** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** em [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** no menu **Exibir** ou CTRL + ALT + X).

 Dois <xref:System.Activities.Statements.PickBranch> objetos vazios com nomes de exibição de **Branch1** e **Branch2** são criados por padrão como elementos de uma <xref:System.Activities.Statements.Pick> atividade quando o designer de atividade de **seleção** é inicialmente retirado para o [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Esses respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propriedade podem ser editados no cabeçalho do **PickBranch** designer ou na janela **Propriedades** de cada ramificação.

 Há duas maneiras de adicionar <xref:System.Activities.Statements.PickBranch> objetos à coleção de um <xref:System.Activities.Statements.Pick> objeto: arrastar e soltar o **PickBranch** designer da **caixa de ferramentas** ou usando o menu de contexto de dentro da superfície de design de **escolha** :

1. O designer de **PickBranch** cria um <xref:System.Activities.Statements.PickBranch> quando é arrastado da **caixa de ferramentas** e solto em uma das ramificações de um designer de atividade de **escolha** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície. Novos objetos de <xref:System.Activities.Statements.PickBranch> podem ser colocados dentro do designer de <xref:System.Activities.Statements.Pick> para a esquerda ou direita de todos os elementos existentes de <xref:System.Activities.Statements.PickBranch> já contidos na coleção. Ao arrastar um designer de **PickBranch** para o designer de **seleção** com um mouse, o designer de **seleção** usa uma faixa azul cinza vertical para indicar onde o <xref:System.Activities.Statements.PickBranch> é adicionado para um determinado posicionamento do mouse.

2. Clique com o botão direito do mouse em **escolher** designer de atividade (mas não dentro do **PickBranch** designer) para obter um menu de contexto e selecione **criar Branch** para adicionar um novo <xref:System.Activities.Statements.PickBranch> . Observe que o novo <xref:System.Activities.Statements.PickBranch> é adicionado à direita dos <xref:System.Activities.Statements.PickBranch> objetos existentes no designer de **seleção** .

   O designer de **PickBranch** pode ser expandido para revelar as caixas de **ação** e **gatilho** ou recolhido clicando nos acentos duplos no lado direito de seus cabeçalhos. Edite o <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> de cada um <xref:System.Activities.Statements.PickBranch> descartando atividades nas caixas de **ação** e **gatilho** de seus designers.

   Os <xref:System.Activities.Statements.PickBranch> objetos na <xref:System.Activities.Statements.Pick.Branches%2A> coleção de um <xref:System.Activities.Statements.Pick> objeto podem ser reordenados arrastando-os e soltando-os em um novo local dentro do designer de **seleção** . O designer de **seleção** usa uma faixa azul cinza vertical para indicar onde o <xref:System.Activities.Statements.PickBranch> é adicionado a um determinado posicionamento do mouse.

   Há duas maneiras para excluir <xref:System.Activities.Statements.PickBranch>:

3. Selecione o designer de **PickBranch** e exclua-o.

4. Selecione o designer do **PickBranch** , clique com o botão direito do mouse para obter o menu de contexto e selecione **excluir**.

   Certifique-se de selecionar o designer de **PickBranch** , uma vez que a seleção de uma das atividades dentro de seu **gatilho** ou caixas de **ação** por engano exclui uma dessas atividades e não o <xref:System.Activities.Statements.PickBranch> objeto.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propriedades de PickBranch em Designer de Fluxo de Trabalho
 A tabela a seguir mostra as propriedades mais úteis de <xref:System.Activities.Statements.PickBranch> e descreve como usá-los em [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome da propriedade|Obrigatório|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Falso|O nome amigável exibido no cabeçalho do designer de **PickBranch** . O valor padrão é ramificação.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Verdadeiro|Cada <xref:System.Activities.Statements.PickBranch> contém uma ação de <xref:System.Activities.Statements.PickBranch.Trigger%2A> que pode chamar <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Falso|Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Action%2A> que é executado se disparado.|

## <a name="see-also"></a>Consulte Também
 [Atividade](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [de seleção de fluxo de controle usando a atividade de seleção](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6) [Control Flow](../workflow-designer/control-flow-activity-designers.md)