---
title: Configurações do log do teste de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9751ce3b08a0ac963cccdf091ccb99001c6f2c9f
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416078"
---
# <a name="modify-load-test-logging-settings"></a>Modificar configurações de registro em log de testes de carga

O resultado de teste de carga para o teste de carga concluído contém exemplos de contador de desempenho e informações de erros que foram coletados em um log periodicamente dos computadores em teste. Um grande número de exemplos de contador de desempenho podem ser coletados durante a execução de um teste de carga. A quantidade de dados de desempenho coletados depende da extensão da execução, do intervalo de amostragem, do número de computadores em teste, e do número de contadores para coletar. Para um teste de carga grande, a quantidade de dados de desempenho coletados pode ser facilmente vários gigabytes; portanto, você deverá considerar a possibilidade de modificar o modo como os dados são salvos com frequência no log. Consulte [Controladores e agentes de teste](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

O *controlador de teste* armazena em spool todos os dados de exemplo do teste de carga em um log de banco de dados durante a execução do teste. Os dados adicionais, como detalhes dos erros e de medição de tempo, são carregados no banco de dados quando o teste é concluído.

|Tarefa|Tópicos associados|
|-|-----------------------|
|**Salvar os logs se um teste de carga falhar:** Você poderá especificar se deseja salvar o log de teste sempre que um teste de carga falhar.|-   [Como: Especificar se as falhas de teste são salvas em logs de teste](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Definir o tamanho máximo de arquivo para o arquivo de log:** Você pode editar o arquivo de configuração XML associado ao serviço do controlador de teste para especificar o tamanho máximo de arquivo que você deseja usar para o arquivo de log.|Modifique `<add key="LogSizeLimitInMegs" value="20"/>` no arquivo de configuração XML *QTCcontroller.exe.config*.|

## <a name="see-also"></a>Consulte também

- [Definir configurações de execução de teste de carga](../test/configure-load-test-run-settings.md)