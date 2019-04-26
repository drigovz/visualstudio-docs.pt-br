---
title: Criar código personalizado e plug-ins para testes de carga
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8382d5014b88d9f1711a082e46530e1e3dfb96e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965410"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Criar código personalizado e plug-ins para testes de carga

Um plug-in personalizado usa um código que você grava e anexa a um teste de carga ou a um teste de desempenho na Web. Você pode usar a API do teste de carga API e a API do teste de desempenho na Web a fim de criar plug-ins personalizados para que os testes sejam expandidos até a funcionalidade interna. Você pode adicionar vários plug-ins ao teste de carga.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Tarefas

|Tarefas|Tópicos associados|
|-|-----------------------|
|**Criar um plug-in personalizado para o teste de carga**: Use a API de teste de carga para criar um plug-in personalizado para adicionar mais funcionalidades de teste ao teste de carga.|-   [Como: Usar a API de teste de carga](../test/how-to-use-the-load-test-api.md)<br />-   [Como: Criar um plug-in de teste de carga](../test/how-to-create-a-load-test-plug-in.md)|
|**Criar um plug-in personalizado para o teste de desempenho Web:** Use a API do teste de desempenho Web para criar um plug-in personalizado para adicionar mais funcionalidades de teste ao teste de desempenho Web, incluindo no nível de solicitação. Você também pode criar um teste de serviço Web.<br /><br /> Além disso, você pode criar um plug-in de gravador da Web capaz de modificar um teste de desempenho na Web depois de gravado, mas antes de ser exibido no Visualizador de Testes de Desempenho Web.|-   [Como: Usar a API de teste de desempenho Web](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Como: Criar um plug-in de teste de desempenho Web](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Como: Criar um plug-in de solicitação](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Como: Criar um teste de serviço Web](../test/how-to-create-a-web-service-test.md)<br />-   [Como: Criar um plug-in do gravador](../test/how-to-create-a-recorder-plug-in.md)|
|**Adicionar funcionalidades de interface do usuário ao Visualizador de Resultados do Teste de Desempenho Web:** Adicione mais funcionalidades de interface do usuário ao Visualizador de Resultados do Teste de Desempenho Web usando um suplemento do Visual Studio.|-   [Como: Criar um suplemento do Visual Studio para o visualizador de resultados de teste de desempenho Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Criar um editor de corpo HTTP personalizado:** Crie um editor personalizado para editar respostas XML HTTP de cadeia de caracteres ou binárias em um serviço Web.|-   [Como: Criar um editor de corpo HTTP personalizado para o Editor de Testes de Desempenho Web](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Referência

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Consulte também

- [Analisar resultados do teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Gerar e executar um teste de desempenho Web codificado](../test/generate-and-run-a-coded-web-performance-test.md)