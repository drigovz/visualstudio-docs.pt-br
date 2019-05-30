---
title: Coloração de sintaxe em um serviço de linguagem herdado | Microsoft Docs
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
ms.openlocfilehash: 47d7164df48011907f8bea408c0acf08250d0657
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331311"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Coloração de sintaxe em um serviço de linguagem herdado

Visual Studio usa um serviço de codificação por cores para identificar elementos da linguagem e exibi-los com as cores especificadas em um editor.

## <a name="colorizer-model"></a>Modelo de colorizador
 O serviço de linguagem implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface, que é usada por editores. Essa implementação é um objeto separado do serviço de linguagem, como mostrado na ilustração a seguir:

 ![Gráfico do colorizador SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> O serviço de coloração de sintaxe é separado do mecanismo geral do Visual Studio para colorir texto. Para obter mais informações sobre o general [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mecanismo que dão suporte a coloração, consulte [usando fontes e cores](../../extensibility/using-fonts-and-colors.md).

 Além de colorizador, o serviço de linguagem pode fornecer itens de coloração personalizados que são usados pelo editor de publicidade que ele fornece itens de coloração personalizados. Você pode fazer isso com a implementação de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface no mesmo objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface. Ele retorna o número de itens de coloração personalizados quando o editor chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método e ele retorna um item individual de coloração personalizado quando chama o editor a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método.

 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método retorna um objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface. Se o serviço de linguagem dá suporte a valores de cor de 24 bits ou alto, ele deverá implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface no mesmo objeto como o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Como um VSPackage usa um colorizador do serviço de linguagem

1. O VSPackage deverá obter o serviço de idioma apropriado, o que exige que o serviço de linguagem VSPackage para fazer o seguinte:

    1. Usar um objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> a interface para obter o texto a ser colorido.

         Texto normalmente é exibido usando um objeto que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.

    2. Obtenha o serviço de linguagem, consultando o provedor de serviços do VSPackage para o GUID do serviço de linguagem. Serviços de linguagem são identificados no registro pela extensão de arquivo.

    3. Associar o serviço de linguagem com o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> chamando seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método.

2. O VSPackage agora pode obter e usar o objeto colorizador da seguinte maneira:

    > [!NOTE]
    > Os VSPackages que usam o editor de núcleo não precisa obter objetos de colorizador do serviço um idioma explicitamente. Assim que uma instância do editor de núcleo obtiver um serviço de idioma apropriado, ele executa todas as tarefas de colorização mostradas aqui.

    1. Obter o objeto de colorizador do serviço de linguagem, que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfaces, chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método no serviço de linguagem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objeto.

    2. Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para obter as informações de colorizador para um determinado intervalo de texto.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Retorna uma matriz de valores, um para cada caractere em que o intervalo de texto que está sendo colorido. Os valores são índices em uma lista de itens que pode ser colorido que é a lista de itens de coloração do padrão mantidas pelo editor de núcleo ou uma lista de itens de coloração personalizados mantido pelo serviço de linguagem em si.

    3. Use as informações de colorização retornadas pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para exibir o texto selecionado.

> [!NOTE]
> Além de usar um colorizador do serviço de linguagem, um VSPackage também pode usar o texto do Visual Studio para fins gerais coloração mecanismo. Para obter mais informações sobre esse mecanismo, consulte [usando fontes e cores](../../extensibility/using-fonts-and-colors.md).

## <a name="in-this-section"></a>Nesta seção
- [Implementar a coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)

 Discute como um editor acessa um serviço de linguagem coloração de sintaxe e que o serviço de linguagem deve implementar para dar suporte à sintaxe colorida.

- [Como: usar itens de coloração internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Demonstra como usar itens de coloração internos do serviço de linguagem.

- [Itens de coloração personalizados](../../extensibility/internals/custom-colorable-items.md)

 Discute como implementar itens de coloração personalizados.

## <a name="see-also"></a>Consulte também

- [Usando fontes e cores](../../extensibility/using-fonts-and-colors.md)