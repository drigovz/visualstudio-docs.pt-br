---
title: 'Como: Avaliar uma expressão XPath | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77c9acae710baeb885bcf901257367251d86c3a2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929737"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Como: Avaliar uma expressão XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode avaliar expressões XPath com o **QuickWatch** caixa de diálogo. A expressão XPath deve ser válido de acordo com a recomendação XPath 1,0 W3C. XSLT de contexto atual — ou seja, o `self::node()` nó o **Locals** janela — fornece o contexto de avaliação da expressão XPath.  
  
 A lista a seguir descreve quais funções são suportadas para avaliar uma expressão XPath:  
  
-   As funções internas XPath são suportadas.  
  
-   As funções internas XSLT não são suportadas.  
  
-   As funções definidas pelo usuário não são suportadas.  
  
> [!NOTE]
>  O procedimento a seguir usa arquivos de Belowavg e Books. XML do [passo a passo: Depurar uma folha de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tópico.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Para avaliar uma expressão XPath  
  
1.  Inserir um ponto de interrupção na tag de início de `xsl:if` .  
  
2.  Clique o **depurar XSL** na barra de ferramentas do Editor de XML.  
  
     Inicia e as quebras do depurador na marca `xsl:if` .  
  
3.  Clique com botão direito e selecione **QuickWatch**.  
  
     O **QuickWatch** caixa de diálogo é exibida.  
  
4.  Insira `./price/text()` no **expressão** campo dos **QuickWatch** caixa de diálogo e clique em **reavaliar**.  
  
     O preço do nó atual do catálogo aparece na **valor** caixa.  
  
5.  Altere a expressão XPath para `./price/text() < $bookAverage` e clique em **reavaliar**.  
  
     O **valor** caixa mostra que a expressão XPath é avaliada como `true`.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração de XSLT](../xml-tools/debugging-xslt.md)
