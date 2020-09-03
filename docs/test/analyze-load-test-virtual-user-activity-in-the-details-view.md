---
title: Analisando a atividade de usuário virtual do teste de carga
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0289ff0d4a20eacc4f6801d9300d39df594bc79e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591227"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analisando a atividade do usuário virtual do teste de carga na exibição Detalhes do Analisador de Teste de Carga

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Gráfico de atividade do usuário virtual**

![Gráfico de Atividade de Usuário Virtual](../test/media/virtual_actchart.png)

A exibição **Detalhes** mostra o **Gráfico de Atividade do Usuário Virtual**, que é usado para analisar visualmente o que os usuários virtuais individuais fizeram durante o teste de carga. O **Gráfico de Atividade do Usuário Virtual** permite visualizar padrões de atividade do usuário e padrões de carga, correlacionar testes com falha ou lentos e ver as solicitações com outra atividade de usuário virtual. O **Gráfico de Atividade do Usuário Virtual** também pode ajudar a determinar picos de uso da CPU, quedas nas solicitações por segundo e quais testes ou páginas estavam em execução durante os picos e as quedas.

> [!NOTE]
> Antes de executar o teste de carga para o qual você deseja usar o **gráfico de detalhes de atividade de usuário virtual**, você deve verificar se a propriedade de **Armazenamento detalhes de tempo** está definida como a opção **AllIndividualDetails** usando o editor de teste de desempenho de carga.

**Painel de legenda de detalhes**

![Painel de legenda de detalhes](../test/media/ltest_detailslegend.png)

O painel de legenda de detalhes está visível no **Gráfico de Atividade do Usuário Virtual**. O painel permite filtrar testes, páginas e transações com base em vários critérios diferentes. Por exemplo, você pode remover alguns testes da exibição, ou remover todos os testes com êxito, ou remover testes reprovados com determinadas falhas. Também é possível remover todos os testes que não possuem logs.

Você pode realçar testes que falharam, o que exibe todos os testes com falha em vermelho. Também é possível realçar testes que possuem logs de teste. Os testes com logs serão coloridos de verde.

**Painel Filtrar resultados**

![Painel Filtrar resultados](../test/media/ltest_filterresults.png)

O painel Resultados do filtro está visível no **Gráfico de Atividade do Usuário Virtual**. Esse painel pode filtrar o seguinte:

- **Mostrar apenas os resultados com logs** Exibe apenas resultados de teste com logs de teste associados.

- **Mostrar resultados bem-sucedidos** Exibe resultados bem-sucedidos.

- **Mostrar resultados com erros** Exibe resultados com erros que podem ajudar na depuração.

## <a name="tasks"></a>Tarefas

|Tarefas|Tópicos associados|
|-|-|
|**Execute o teste de carga:** Depois de criar um teste de carga e configurá-lo para habilitar a coleta de dados de atividade de usuário virtual, você deve executar o teste até que ele seja concluído para exibir o **gráfico de atividade de usuário virtual**.||
|**Exibir os resultados do teste de carga que contêm os dados de atividade do usuário virtual:** Depois que o teste de carga tiver sido criado, configurado e concluído a execução, você poderá exibir os dados de atividade de usuário virtual usando o **gráfico de atividade de usuário virtual**.|-   [Analisar resultados do teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Como: analisar o que os usuários virtuais estão fazendo durante um teste de carga](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isole os problemas de desempenho nos testes de carga:** Você pode usar o **gráfico de atividade de usuário virtual** para ajudar a isolar problemas de desempenho no teste de carga.|-   [Walkthrough: usando o gráfico de atividade de usuário virtual para isolar problemas](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Confira também

- [Analisar resultados do teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analisar resultados do teste de carga e erros na exibição Tabelas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
