---
title: Avaliar uma expressão XPath durante a depuração
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1585b54d084e3471583f9388d63f5c17e65fc3a7
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526316"
---
# <a name="evaluate-xpath-expressions"></a>Avaliar expressões XPath

Você pode avaliar expressões XPath usando os **QuickWatch** janela durante a depuração. A expressão XPath deve ser válido de acordo com a recomendação XPath 1,0 W3C. XSLT de contexto atual (ou seja, o `self::node()` nó o **Locals** janela) fornece o contexto de avaliação da expressão XPath.

Ao avaliar uma expressão XPath:

- As funções internas XPath são suportadas.

- Não há suporte para as funções internas XSLT e funções definidas pelo usuário.

> [!NOTE]
> Depuração de XSLT só está disponível na edição Enterprise do Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Avaliar uma expressão XPath

O procedimento a seguir usa o *abaixo average.xsl* e *Books. XML* arquivos do [passo a passo: Depurar uma folha de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) página.

1. Inserir um ponto de interrupção na tag de início de `xsl:if` .

2. Para iniciar a depuração, escolha **XML** > **iniciar depuração de XSLT** na barra de menus (ou pressione **Alt**+**F5** ).

   Inicia e as quebras do depurador na marca `xsl:if` .

3. Clique com botão direito e selecione **QuickWatch**.

   O **QuickWatch** janela é aberta.

4. Insira `./price/text()` no **expressão** campo dos **QuickWatch** caixa de diálogo caixa e, em seguida, escolha **reavaliar**.

   O preço do nó atual do catálogo aparece na **valor** caixa.

   ![Avaliar uma expressão XPath na janela Quickwatch](media/quickwatch-price.png)

5. Altere a expressão XPath para `./price/text() < $bookAverage` e clique em **reavaliar**.

   O **valor** caixa mostra que a expressão XPath é avaliada como `true`.

## <a name="see-also"></a>Consulte também

- [Depuração de XSLT](../xml-tools/debugging-xslt.md)