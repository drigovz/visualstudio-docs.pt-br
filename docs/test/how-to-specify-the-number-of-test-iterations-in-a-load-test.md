---
title: Especificar o número de iterações na configuração de execução de teste de carga
description: Saiba como especificar o número de iterações a serem executadas em todos os testes de unidade e de desempenho da Web em todos os cenários em um teste de carga usando o Editor de Teste de Carga.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a257b5800166e840194a28cba0ca99849b05f579
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936191"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Como especificar o número de iterações de teste em uma configuração de execução de teste de carga

Depois de criar seu teste de carga com o **Novo Assistente de Teste de Carga**, você poderá usar o **Editor de Teste de Carga** para alterar as propriedades de cenários para que eles atendam às suas metas e necessidades de teste. Para obter mais informações, consulte [Passo a passo: criar e executar um teste de carga](../test/walkthrough-create-and-run-a-load-test.md).

Usando o **Editor de teste de carga**, você pode editar a propriedade **iterações de teste** de um valor de configurações de execução na janela **Propriedades** . A propriedade **Iterações de teste** especifica o número de iterações a serem executadas em todos os testes de unidade e desempenho Web em todos os cenários em um teste de carga usando o **Editor de Teste de Carga**.

> [!NOTE]
> Para obter uma lista completa das propriedades de configurações de execução e suas descrições, consulte [Propriedades de configurações de execução de teste de carga](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Para especificar o número de iterações de teste em uma configuração de execução

1. Abra um teste de carga.

     O **Editor de Teste de Carga** aparece e exibe a árvore de teste de carga.

2. Na árvore de teste de carga, na pasta **Configurações de Execução**, escolha uma configuração de execução.

3. No menu **Exibição**, selecione a **Janela de Propriedades** para exibir as categorias e as propriedades da configuração de execução de carga.

4. Defina a propriedade **Usar iterações de teste** como **Verdadeiro**.

5. Na propriedade **Iterações de teste**, insira um número que indica o número de iterações de teste a serem executadas durante o teste de carga.

6. Depois de alterar a propriedade, escolha **Salvar** no menu **Arquivo**. Assim, você pode executar o teste de carga usando o novo valor de **Iterações de teste**.

## <a name="see-also"></a>Confira também

- [Definir configurações de execução de teste de carga](../test/configure-load-test-run-settings.md)
- [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md)
