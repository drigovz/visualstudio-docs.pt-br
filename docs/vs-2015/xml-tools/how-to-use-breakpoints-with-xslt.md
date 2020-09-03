---
title: 'Como: usar pontos de interrupção com XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656303"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Como: Use pontos de interrupção com XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode definir pontos de interrupção em uma folha de estilos XSLT ou no documento de código-fonte XML. Se você definir um ponto de interrupção em uma marca, quando a execução iniciar o ponto de interrupção se transportará para a instrução que tem a seguinte linha de código informações.

 Para obter mais informações, consulte [noções básicas de depuração: pontos de interrupção](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Definir um ponto de interrupção em uma folha de estilos
 Os pontos de interrupção podem ser definidos em marcas inicial, em marcas de fim, e em nós de texto de uma folha de estilos XSLT. Os pontos de interrupção também podem ser definidos no código em um bloco de script.

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Para definir um ponto de interrupção em uma folha de estilos

1. Abra uma folha de estilos no editor XML.

2. Posicione o cursor no local do ponto de interrupção, clique com o botão direito do mouse, aponte para ponto de **interrupção**e clique em **Inserir ponto de interrupção**.

3. Clique no botão procurar (**...**) no campo de **entrada** da janela Propriedades do documento.

4. Localize o documento de origem XML e clique em **abrir**.

     Isso define o arquivo de documento de origem que é usado para a transformação XSLT.

5. Clique no botão **depurar XSL** na barra de ferramentas do editor de XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Definir um ponto de interrupção em um documento-fonte XML
 Os pontos de interrupção podem ser definidas em elementos, atributos, no nó de namespace, nos comentários, na instrução de processamento, e os nós de texto de um documento-fonte XML. Você não pode definir um ponto de interrupção no nó do documento, ou em um nó de namespace que é herdada de elemento pai.

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Para definir um ponto de interrupção em um documento-fonte XML

1. Abra o documento XML no editor XML.

2. Posicione o cursor no local do ponto de interrupção, clique com o botão direito do mouse, aponte para ponto de **interrupção**e clique em **Inserir ponto de interrupção**.

3. Clique no botão procurar (**...**) no campo folha de **estilos** da janela Propriedades do documento.

4. Localize o documento de origem XML e clique em **abrir**.

     Isso define o arquivo de documento de origem que é usado para a transformação XSLT.

5. Clique no botão **depurar XSL** na barra de ferramentas do editor de XML.

## <a name="see-also"></a>Consulte Também
 [Passo a passo: Depurar uma folha de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
