---
title: 'Como: Criar grafos personalizados nos resultados do teste de carga'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 8fd80a4d7cbfeb7cf79ae3dddad9aa1da367fd87
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992770"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Como: Criar grafos personalizados nos resultados do teste de carga

Você pode projetar gráficos que exibam informações específicas sobre resultados de teste de carga. Você cria um gráfico personalizado especificando os contadores de teste de carga que o gráfico exibirá.

Você pode executar o procedimento a seguir enquanto um teste de carga está em execução ou depois de concluir a execução.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>Para criar um grafo de resultados de teste de carga personalizado

1.  Na barra de ferramentas **Teste de Carga**, escolha **Adicionar um Novo Grafo**.

     \- ou -

     No **Analisador de Teste de Carga**, clique com o botão direito do mouse no painel **Contadores** ou em um grafo e, em seguida, selecione **Adicionar Grafo**.

     A caixa de diálogo **Digite o nome do gráfico** é exibida.

2.  Em **Nome do gráfico**, digite um nome para o gráfico e escolha **OK**.

     O novo grafo é exibido no **Analisador de Teste de Carga**. Ele é exibido no painel de gráfico selecionado no momento; ele substitui o gráfico que foi exibido nesse painel.

3.  Personalize o novo gráfico adicionando contadores. Para obter mais informações, confira [Como: Adicionar e excluir contadores em grafos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

## <a name="see-also"></a>Consulte também

- [Analisar resultados do teste de carga na exibição Grafos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Como: Adicionar e excluir contadores em grafos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)