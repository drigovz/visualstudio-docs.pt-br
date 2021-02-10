---
title: Designer de atividade Designer de Fluxo de Trabalho-PickBranch
description: Saiba como o designer de atividade do PickBranch fornece um caminho de execução baseado em evento em uma atividade de seleção que pode ser disparada por um evento de entrada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d3ac314d5f8eb7980bdf5102d871546d3167141
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968665"
---
# <a name="pickbranch-activity-designer"></a>Designer de atividade de PickBranch

<xref:System.Activities.Statements.PickBranch> fornece um caminho de execução baseado em uma atividade de <xref:System.Activities.Statements.Pick> que pode ser acionada por um evento de entrada.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> os objetos estão contidos na <xref:System.Activities.Statements.Pick.Branches%2A> coleção de uma <xref:System.Activities.Statements.Pick> atividade. Cada <xref:System.Activities.Statements.PickBranch> está contido em uma ramificação de atividade de <xref:System.Activities.Statements.Pick> e pode ser executado devido a qualquer evento de entrada que serve como um disparador. Dessa forma, o Designer de Fluxo de Trabalho fornece modelagem de fluxo de controle baseado em eventos. Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Como usar o designer de atividade de picareta

Acesse o designer do **PickBranch** na categoria **fluxo de controle** da **caixa de ferramentas**.

Dois <xref:System.Activities.Statements.PickBranch> objetos vazios com nomes de exibição de **Branch1** e **Branch2** são criados por padrão como elementos de uma <xref:System.Activities.Statements.Pick> atividade quando o designer de atividade de **seleção** é inicialmente retirado para o designer de fluxo de trabalho. Esses respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propriedade podem ser editados no cabeçalho do **PickBranch** designer ou na janela **Propriedades** de cada ramificação.

Há duas maneiras de adicionar <xref:System.Activities.Statements.PickBranch> objetos à coleção de um <xref:System.Activities.Statements.Pick> objeto: arrastar e soltar o designer **PickBranch** da **caixa de ferramentas** ou usando o menu de atalho de dentro da superfície de design de **escolha** :

- O designer **PickBranch** cria um <xref:System.Activities.Statements.PickBranch> quando ele é arrastado da **caixa de ferramentas** e é colocado em uma das ramificações de um designer de atividade de **escolha** na superfície de designer de fluxo de trabalho. Novos objetos de <xref:System.Activities.Statements.PickBranch> podem ser colocados dentro do designer de <xref:System.Activities.Statements.Pick> para a esquerda ou direita de todos os elementos existentes de <xref:System.Activities.Statements.PickBranch> já contidos na coleção. Ao arrastar um designer de **PickBranch** para o designer de **seleção** com um mouse, o designer de **seleção** usa uma faixa azul cinza vertical para indicar onde o <xref:System.Activities.Statements.PickBranch> é adicionado para um determinado posicionamento do mouse.

- Clique com o botão direito do mouse em **escolher** designer de atividade (mas não dentro do **PickBranch** designer) para obter um menu de contexto e selecione **criar Branch** para adicionar um novo <xref:System.Activities.Statements.PickBranch> . Observe que o novo <xref:System.Activities.Statements.PickBranch> é adicionado à direita dos <xref:System.Activities.Statements.PickBranch> objetos existentes no designer de **seleção** .

O designer de **PickBranch** pode ser expandido para revelar as caixas de **ação** e **gatilho** ou recolhido clicando nos acentos duplos no lado direito de seus cabeçalhos. Edite o <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> de cada um <xref:System.Activities.Statements.PickBranch> descartando atividades nas caixas de **ação** e **gatilho** de seus designers.

Os <xref:System.Activities.Statements.PickBranch> objetos na <xref:System.Activities.Statements.Pick.Branches%2A> coleção de um <xref:System.Activities.Statements.Pick> objeto podem ser reordenados arrastando-os e soltando-os em um novo local dentro do designer de **seleção** . O designer de **seleção** usa uma faixa azul cinza vertical para indicar onde o <xref:System.Activities.Statements.PickBranch> é adicionado a um determinado posicionamento do mouse.

Há duas maneiras para excluir <xref:System.Activities.Statements.PickBranch>:

- Selecione o designer de **PickBranch** e exclua-o.
- Selecione o designer do **PickBranch** , clique com o botão direito do mouse para obter o menu de contexto e selecione **excluir**.

Certifique-se de selecionar o designer de **PickBranch** , uma vez que a seleção de uma das atividades dentro de seu **gatilho** ou caixas de **ação** por engano exclui uma dessas atividades e não o <xref:System.Activities.Statements.PickBranch> objeto.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propriedades de PickBranch em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades mais úteis <xref:System.Activities.Statements.PickBranch> e descreve como usá-las no designer de fluxo de trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Falso|O nome amigável exibido no cabeçalho do designer de **PickBranch** . O valor padrão é ramificação.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Cada <xref:System.Activities.Statements.PickBranch> contém uma ação de <xref:System.Activities.Statements.PickBranch.Trigger%2A> que pode chamar <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Falso|Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Action%2A> que é executado se disparado.|

## <a name="see-also"></a>Confira também

- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
- [Escolher atividade](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Usando a atividade de Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)