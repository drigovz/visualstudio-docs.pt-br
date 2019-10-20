---
title: Como avaliar uma expressão XPath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670862"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Como: Avalie uma expressão XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode avaliar as expressões XPath com a caixa de diálogo **QuickWatch** . A expressão XPath deve ser válido de acordo com a recomendação XPath 1,0 W3C. O contexto XSLT atual, ou seja, o nó `self::node()` na janela **locais** — fornece o contexto de avaliação para a expressão XPath.

 A lista a seguir descreve quais funções são suportadas para avaliar uma expressão XPath:

- As funções internas XPath são suportadas.

- As funções internas XSLT não são suportadas.

- As funções definidas pelo usuário não são suportadas.

> [!NOTE]
> O procedimento a seguir usa os arquivos belowAvg. xsl e books. XML a partir do [tutorial: Depurar um tópico de folha de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .

### <a name="to-evaluate-an-xpath-expression"></a>Para avaliar uma expressão XPath

1. Inserir um ponto de interrupção na tag de início de `xsl:if` .

2. Clique no botão **depurar XSL** na barra de ferramentas do editor de XML.

     Inicia e as quebras do depurador na marca `xsl:if` .

3. Clique com o botão direito do mouse e selecione **QuickWatch**.

     A caixa de diálogo **QuickWatch** é exibida.

4. Insira `./price/text()` no campo **expressão** da caixa de diálogo **QuickWatch** e clique em **reavaliar**.

     O preço do nó do livro atual aparece na caixa **valor** .

5. Altere a expressão XPath para `./price/text() < $bookAverage` e clique em **reavaliar**.

     A caixa **valor** mostra que a expressão XPath é avaliada como `true`.

## <a name="see-also"></a>Consulte também
 [Depuração de XSLT](../xml-tools/debugging-xslt.md)
