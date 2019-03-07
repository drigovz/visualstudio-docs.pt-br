---
title: Folhas de estilos XSLT de edição
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c212bcac1584a47f696f6ab90d4f616286a2ac5e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912554"
---
# <a name="edit-xslt-style-sheets"></a>Editar folhas de estilos XSLT

O editor XML pode ser usado para editar folhas de estilos XSLT. Você pode tirar proveito dos recursos do editor padrão como o IntelliSense, estruturação, snippets XML, e assim por diante. Além disso, há também os novos recursos que tornam ficar em XSLT.

## <a name="xslt-features"></a>Recursos de fonte
 A tabela a seguir descreve os recursos específicos para trabalhar com folhas de estilos XSLT.

 **Coloração de sintaxe**

 Palavras-chave XSLT, tais como `template`, `match`e assim por diante, são exibidos na cor da palavra-chave XSLT especificada pela **fontes e cores** configurações.

 **Sublinhados ondulados**

 O Editor XML usa a instalada *XSLT* arquivo para validar folhas de estilos XSLT. Os erros de validação são mostrados como sublinhados ondulados azuis. O editor XML também compila a folha de estilos em segundo plano e relatar erros ou avisos do compilador com traços ondulados apropriadas.

 **Suporte para blocos de script**

 O código nos blocos de script é suportado pelo depurador XSLT para que você pode definir pontos de interrupção e percorrer o código de bloco de script.

 **Saída XSLT de exibição**

 Você pode executar uma transformação XSL e exibir a saída do editor XML. Para obter mais informações, confira [Como: Executar uma transformação XSLT do Editor XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Debug XSLT**

 Você pode iniciar o depurador XSLT de um arquivo fonte no editor XML. O depurador oferece suporte pontos de interrupção no arquivo XSLT, estado de configuração de execução XSLT de exibição, e assim por diante. Passa sobre uma variável XSLT traz anterior um ToolTip com o valor da variável. O depurador pode ser usado para depurar uma folha de estilos, ou depurar uma transformação XSL compilado chamada de outro aplicativo. Para obter mais informações, consulte [depuração XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)