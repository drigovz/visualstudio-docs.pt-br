---
title: Editando folhas de estilo XSLT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e1669affa89c91ca3ae1958c22ff3ec4d56bb8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670964"
---
# <a name="editing-xslt-style-sheets"></a>Folhas de estilos XSLT de edição
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor XML pode ser usado para editar folhas de estilos XSLT. Você pode tirar proveito dos recursos do editor padrão como o IntelliSense, estruturação, snippets XML, e assim por diante. Além disso, há também os novos recursos que tornam ficar em XSLT.

## <a name="xslt-features"></a>Recursos de fonte
 A tabela a seguir descreve os recursos específicos para trabalhar com folhas de estilos XSLT.

 **Cor da sintaxe** As palavras-chave XSLT, como `template` , `match` e assim por diante, são exibidas na cor da palavra-chave XSLT especificada pelas configurações de **fontes e cores** .

 **Sublinhados ondulados** O editor de XML usa o arquivo XSLT. xsd instalado para validar as folhas de estilo XSLT. Os erros de validação são mostrados como sublinhados ondulados azuis. O editor XML também compila a folha de estilos em segundo plano e relatar erros ou avisos do compilador com traços ondulados apropriadas.

 **Suporte para blocos de script** O código em blocos de script tem suporte do depurador XSLT para que você possa definir pontos de interrupção e percorrer o código de bloco de script.

 **Exibir saída XSLT** Você pode executar uma transformação XSL e exibir a saída do editor de XML. Para obter mais informações, consulte [como executar uma transformação XSLT no editor de XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Depurar XSLT** Você pode iniciar o depurador XSLT de um arquivo XSLT no editor de XML. O depurador oferece suporte pontos de interrupção no arquivo XSLT, estado de configuração de execução XSLT de exibição, e assim por diante. Passa sobre uma variável XSLT traz anterior um ToolTip com o valor da variável. O depurador pode ser usado para depurar uma folha de estilos, ou depurar uma transformação XSL compilado chamada de outro aplicativo. Para obter mais informações, consulte [DEBUGGING XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Consulte Também
 [Editor de XML](../xml-tools/xml-editor.md)
