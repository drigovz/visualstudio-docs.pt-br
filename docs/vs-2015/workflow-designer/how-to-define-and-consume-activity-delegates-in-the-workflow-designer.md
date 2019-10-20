---
title: 'Como: definir e consumir delegados de atividade no Designer de Fluxo de Trabalho | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603852"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Como: Defina e consumir representantes de atividade em Designer de Fluxo de Trabalho
[!INCLUDE[net_v45](../includes/net-v45-md.md)] inclui um novo de designer para fora da caixa para atividades de <xref:System.Activities.Statements.InvokeDelegate> . Este criador pode ser usado para atribuir os representantes para a atividade que derivam de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> ou <xref:System.Activities.ActivityFunc%601>.

### <a name="define-an-activity-delegate"></a>Defina um representante de atividades

1. Em [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], selecione **arquivo**, **novo**, **projeto**. Selecione o nó de **fluxo de trabalho** à esquerda e o modelo de aplicativo do console de **fluxo de trabalho** à direita. Nomeie o projeto (se desejar) e clique em **OK**.

2. Clique com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecione **Adicionar**, **novo item...** . Selecione o nó de **fluxo de trabalho** à esquerda e o modelo de **atividade** à direita. Nomeie a nova atividade **myforeach. XAML** e clique em **OK**. A atividade será aberto no designer de fluxo de trabalho.

3. No designer de fluxo de trabalho, clique na guia **argumentos** .

4. Clique em **criar argumento**. Nomeie os novos **itens**de argumento.

5. Na coluna **tipo de argumento** , selecione **matriz de [T]** .

6. No navegador de tipos, selecione **objeto**. Clique em **OK**.

7. Clique em **criar argumento** novamente. Nomeie o novo **corpo**do argumento. Na coluna **direção** do novo argumento, selecione **Propriedade**.

8. Na coluna tipo de argumento, selecione **procurar tipos...**

9. No navegador de tipos, insira **ActivityAction** no campo **nome do tipo** . Selecione **activityaction \<T >** no modo de exibição de árvore. Selecione **objeto** na lista suspensa que aparece para atribuir o tipo **activityaction \<Object >** ao argumento.

10. Arraste uma atividade de <xref:System.Activities.Statements.While> da seção **fluxo de controle** da caixa de ferramentas para a superfície do designer.

11. Selecione a atividade <xref:System.Activities.Statements.While> e selecione a guia **variáveis** .

12. Selecione **criar variável**. Nomeie o novo **índice**de variável.

13. Na coluna **tipo de variável** , selecione **Int32**. Deixe o **escopo** como **while**e a coluna **padrão** em branco.

14. Defina a propriedade **condição** da atividade de <xref:System.Activities.Statements.While> para **indexar < itens. Length;** .

15. Arraste uma atividade de <xref:System.Activities.Statements.InvokeDelegate> da seção **primitivas** da caixa de ferramentas para o **corpo** da atividade de <xref:System.Activities.Statements.While>.

16. Selecione **corpo** na lista suspensa delegar.

17. Na grade de **Propriedades** da atividade <xref:System.Activities.Statements.InvokeDelegate>, clique em **...** na propriedade de **argumentos de representante** .

18. Na coluna **valor** do argumento chamado **argumento**, insira **itens [índice]** . Clique em **OK** para fechar a caixa de diálogo **DelegateArguments** .

19. Arraste uma atividade de <xref:System.Activities.Statements.Assign> na linha horizontal abaixo de atividade de <xref:System.Activities.Statements.InvokeDelegate> . A atividade de <xref:System.Activities.Statements.Assign> será criada e uma atividade de <xref:System.Activities.Statements.Sequence> será criada automaticamente para conter as duas atividades na seção **corpo** da atividade **myforeach** . A sequência é necessária, pois a seção **Body** só pode conter uma única atividade. Criar automaticamente uma nova atividade de <xref:System.Activities.Statements.Sequence> é um novo recurso de [!INCLUDE[net_v45](../includes/net-v45-md.md)].

20. Defina a propriedade **to** da atividade <xref:System.Activities.Statements.Assign> como **index**. Defina a propriedade **valor** da atividade **atribuir** como **índice + 1**.

    A atividade personalizada **myforeach** agora invocará uma atividade arbitrária uma vez para cada valor passado por meio da coleção **Items** , com os valores na coleção como entradas para a atividade.

### <a name="use-the-custom-activity-in-a-workflow"></a>Use a atividade personalizado em um fluxo de trabalho

1. Crie o projeto pressionando **Ctrl + Shift + B**.

2. No **Gerenciador de soluções**, abra **Workflow1. XAML** no designer.

3. Arraste uma atividade **myforeach** da caixa de ferramentas para a superfície do designer. A atividade será em uma seção da caixa de ferramentas com o mesmo nome que o projeto.

4. Defina a propriedade **Items** da atividade **myforeach** como **New Object [] {1, "ABC"}** .

5. Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> da seção **primitivas** da caixa de ferramentas para a seção **delegar: corpo** da atividade **myforeach** .

6. Defina a propriedade **Text** da atividade de <xref:System.Activities.Statements.WriteLine> como **Argument. ToString ()** .

   Quando o fluxo de trabalho é executado, o console mostrará o seguinte:

   **1** 
   **ABC**