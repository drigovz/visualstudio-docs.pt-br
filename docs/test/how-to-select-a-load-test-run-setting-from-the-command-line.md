---
title: Definir as configurações de execução de teste de carga na linha de comando
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 760cf18062e607e9f9039c6cc5f4adf409134cb5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588987"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Como selecionar uma configuração de execução de teste de carga a ser usada na linha de comando

Um teste de carga pode incluir *configurações de execução*, que são propriedades que influenciam a forma como um teste de carga é executado. As configurações de execução são organizadas por categorias na janela **Propriedades**. Quando é executado, um teste de carga usa a configuração de execução definida como ativa no momento.

Se contiver apenas uma configuração de execução, o teste de carga será sempre o nó ativo. Se o teste de carga contiver vários nós de configurações de execução, você poderá selecionar um para usar ao executar um teste de carga na linha de comando. [Veja Como: Adicionar configurações adicionais de execução a um teste de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Para alterar a configuração de execução na linha de comando

1. Se quiser usar configurações de execução diferentes na linha de comando para se beneficiar da estratégia do parâmetro de contexto, use o seguinte comando:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. Execute o teste de carga usando mstest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Confira também

- [Configure as configurações de execução do teste de carga](../test/configure-load-test-run-settings.md)
- [Especificar os conjuntos de contadores e as regras de limite para computadores em um teste de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Como: Adicionar configurações adicionais de execução a um teste de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Como selecionar a configuração de execução ativa para um teste de carga](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
