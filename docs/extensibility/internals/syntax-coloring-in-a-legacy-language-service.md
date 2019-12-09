---
title: Cores de sintaxe em um serviço de linguagem herdada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa3dcadfc7774766c0e76617ce133d2c30ba2aa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186313"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Coloração de sintaxe em um serviço de linguagem herdado

O Visual Studio usa um serviço de coloração para identificar elementos do idioma e exibi-los com as cores especificadas em um editor.

## <a name="colorizer-model"></a>Modelo Colorizer
 O serviço de linguagem implementa a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, que é usada pelos editores. Essa implementação é um objeto separado do serviço de idioma, conforme mostrado na ilustração a seguir:

 ![Gráfico SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> O serviço de coloração de sintaxe é separado do mecanismo geral do Visual Studio para colorir o texto. Para obter mais informações sobre o mecanismo de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] geral que dá suporte à coloração, consulte [usando fontes e cores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Além do Colorizer, o serviço de linguagem pode fornecer itens coloráveis personalizados que são usados pelo editor, anunciando que ele fornece itens personalizáveis personalizados. Você pode fazer isso implementando a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> no mesmo objeto que implementa a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Ele retorna o número de itens colorable personalizados quando o editor chama o método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> e retorna um item Colorable personalizado individual quando o editor chama o método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

 O método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> retorna um objeto que implementa a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>. Se o serviço de linguagem der suporte a valores de 24 bits ou de cor alta, ele deverá implementar a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> no mesmo objeto que a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Como um VSPackage usa um serviço de linguagem Colorizer

1. O VSPackage deve obter o serviço de idioma apropriado, que exige que o serviço de linguagem VSPackage faça o seguinte:

    1. Use um objeto que implementa a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para obter o texto a ser colorido.

         Normalmente, o texto é exibido usando um objeto que implementa a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

    2. Obtenha o serviço de linguagem consultando o provedor de serviços do VSPackage para o GUID do serviço de idioma. Os serviços de linguagem são identificados no registro por extensão de arquivo.

    3. Associe o serviço de linguagem ao <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> chamando seu método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>.

2. O VSPackage agora pode obter e usar o objeto Colorizer da seguinte maneira:

    > [!NOTE]
    > VSPackages que usam o editor de núcleo não precisam obter explicitamente os objetos Colorizer de um serviço de linguagem. Assim que uma instância do editor central Obtém um serviço de idioma apropriado, ele executa todas as tarefas de colorização mostradas aqui.

    1. Obtenha o objeto Colorizer do serviço de linguagem, que implementa as interfaces <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>, chamando o método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> no objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> do serviço de linguagem.

    2. Chame o método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para obter as informações de Colorizer para um determinado trecho de texto.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> retorna uma matriz de valores, uma para cada caractere no intervalo de texto que está sendo colorido. Os valores são índices em uma lista de itens colorable que é a lista de itens colorable padrão mantida pelo editor principal ou uma lista de itens colorable personalizável mantida pelo próprio serviço de linguagem.

    3. Use as informações de colorização retornadas pelo método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para exibir o texto selecionado.

> [!NOTE]
> Além de usar um Colorizer de serviço de linguagem, um VSPackage também pode usar o mecanismo de coloração de texto de uso geral do Visual Studio. Para obter mais informações sobre esse mecanismo, consulte [usando fontes e cores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>Nesta seção
- [Implementar a coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)

 Discute como um editor acessa a cor da sintaxe de um serviço de linguagem e o que o serviço de idioma deve implementar para dar suporte à cor da sintaxe.

- [Como usar itens de coloração internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Demonstra como usar itens coloráveis internos do serviço de linguagem.

- [Itens de coloração personalizados](../../extensibility/internals/custom-colorable-items.md)

 Discute como implementar itens coloráveis personalizados.