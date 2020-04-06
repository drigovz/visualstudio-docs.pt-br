---
title: Coloração de sintaxe em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704751"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Coloração de sintaxe em um serviço de linguagem herdado

O Visual Studio usa um serviço de coloração para identificar elementos do idioma e exibi-los com as cores especificadas em um editor.

## <a name="colorizer-model"></a>Modelo de colorizador
 O serviço de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> idiomas implementa a interface, que é então usada pelos editores. Esta implementação é um objeto separado do serviço de idiomas, como mostrado na ilustração a seguir:

 ![Gráfico do colorador SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> O serviço de coloração de sintaxe é separado do mecanismo geral do Visual Studio para colorir texto. Para obter mais [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] informações sobre o mecanismo geral de suporte à coloração, consulte [Usando fontes e cores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Além do colorador, o serviço de idiomas pode fornecer itens coloráveis personalizados que são usados pelo editor, anunciando que ele fornece itens coloridos personalizados. Você pode fazer isso <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> implementando a interface no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> mesmo objeto que implementa a interface. Ele retorna o número de itens coloríveis personalizados quando o editor chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> retorna um item colorível personalizado individual quando o editor chama o método.

 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método retorna um objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> que implementa a interface. Se o serviço de idioma suportar valores de cor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> de 24 bits <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> ou altos, ele deve implementar a interface no mesmo objeto que a interface.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Como um VSPackage usa um colorador de serviço de idioma

1. O VSPackage deve obter o serviço de idioma apropriado, que requer o serviço de idiomaVSPackage para fazer o seguinte:

    1. Use um objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> que implemente a interface para que o texto seja colorido.

         O texto é normalmente exibido usando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> um objeto que implementa a interface.

    2. Obtenha o serviço de idioma consultando o provedor de serviços do VSPackage para o serviço de idioma GUID. Os serviços de idioma são identificados no registro por extensão de arquivo.

    3. Associar o serviço <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> de idiomas com o chamando de seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método.

2. O VSPackage agora pode obter e usar o objeto colorador da seguinte forma:

    > [!NOTE]
    > VsPacotes que usam o editor principal não têm que obter objetos corificantes de um serviço de idioma explicitamente. Assim que uma instância do editor principal obtém um serviço de idioma apropriado, ele executa todas as tarefas de colorização mostradas aqui.

    1. Obtenha o objeto colorizador do serviço <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> idiomas, que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> implementa as interfaces <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> e as interfaces, chamando o método no objeto do serviço de idiomas.

    2. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> o método para obter as informações do colorador para um determinado período de texto.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>retorna uma matriz de valores, um para cada caractere no período de texto que está sendo colorido. Os valores são índices em uma lista de itens coloridos que é a lista de itens coloríveis padrão mantida pelo editor principal ou uma lista de itens coloríveis personalizada mantida pelo próprio serviço de idiomas.

    3. Use as informações de colorização retornadas pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para exibir o texto selecionado.

> [!NOTE]
> Além de usar um colorador de serviço de idioma, um VSPackage também pode usar o mecanismo de coloração de texto visual studio de uso geral. Para obter mais informações sobre esse mecanismo, consulte [Usando fontes e cores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>Nesta seção
- [Implementando a coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)

 Discute como um editor acessa a coloração de sintaxe de um serviço de idiomas e o que o serviço de idiomas deve implementar para suportar a coloração de sintaxe.

- [Como usar itens de coloração internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Demonstra como usar itens coloridos incorporados a partir do serviço de idiomas.

- [Itens personalizados que podem ser coloridos](../../extensibility/internals/custom-colorable-items.md)

 Discute como implementar itens coloráveis personalizados.
