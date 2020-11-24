---
title: Como criar gráficos personalizados em resultados de teste de carga
description: Saiba como projetar grafos que exibem informações específicas sobre os resultados do teste de carga durante a execução de um teste de carga ou após a conclusão da execução.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c003fc5d6573dfdd88ec85ea37fbb10f80c94484
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441033"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Como criar grafos personalizados em resultados do teste de carga

Você pode projetar gráficos que exibam informações específicas sobre resultados de teste de carga. Você cria um gráfico personalizado especificando os contadores de teste de carga que o gráfico exibirá.

Você pode executar o procedimento a seguir enquanto um teste de carga está em execução ou depois de concluir a execução.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>Para criar um grafo de resultados de teste de carga personalizado

1. Na barra de ferramentas **teste de carga** , escolha **Adicionar novo grafo**.

     \- ou –

     No **analisador de testes de carga**, clique com o botão direito do mouse no painel **contadores** ou em um grafo e selecione **Adicionar grafo**.

     A caixa de diálogo **Digite o nome do gráfico** é exibida.

2. Em **Nome do gráfico**, digite um nome para o gráfico e escolha **OK**.

     O novo grafo é exibido no **Analisador de Teste de Carga**. Ele é exibido no painel de gráfico selecionado no momento; ele substitui o gráfico que foi exibido nesse painel.

3. Personalize o novo gráfico adicionando contadores. Para saber mais, confira [Como adicionar e excluir contadores em gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

## <a name="see-also"></a>Confira também

- [Analisar resultados do teste de carga na exibição Grafos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Como: Adicionar e excluir contadores em gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
