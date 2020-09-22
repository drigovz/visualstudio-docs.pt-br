---
title: Cores de sintaxe em um serviço de linguagem herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59d25c338cb0c7406c533afeceaf3675fbd16e96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838559"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Coloração de sintaxe em um serviço de linguagem herdado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usa um serviço de coloração para identificar elementos do idioma e exibi-los com as cores especificadas em um editor.  
  
## <a name="colorizer-model"></a>Modelo Colorizer  
 O serviço de linguagem implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface, que é usada pelos editores. Essa implementação é um objeto separado do serviço de idioma, conforme mostrado na ilustração a seguir.  
  
 ![Gráfico SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Modelo simples de Colorizer  
  
> [!NOTE]
> O serviço de coloração de sintaxe é separado do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mecanismo geral para colorir o texto. Para obter mais informações sobre o [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] mecanismo geral que dá suporte à coloração, consulte [usando fontes e cores](../../extensibility/using-fonts-and-colors.md).  
  
 Além do Colorizer, o serviço de linguagem pode fornecer itens coloráveis personalizados que são usados pelo editor anunciando que ele fornece itens personalizáveis personalizados. Você pode fazer isso implementando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface no mesmo objeto que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface. Ele retorna o número de itens colorable personalizados quando o editor chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método e retorna um item Colorable personalizado individual quando o editor chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método.  
  
 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método retorna um objeto que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface. Se o serviço de linguagem der suporte a valores de 24 bits ou de cor alta, ele deverá implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface no mesmo objeto que a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Como um VSPackage usa um serviço de linguagem Colorizer  
  
1. O VSPackage deve obter o serviço de idioma apropriado, que exige que o serviço de linguagem VSPackage faça o seguinte:  
  
    1. Use um objeto que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface para obter o texto a ser colorido.  
  
         Normalmente, o texto é exibido usando um objeto que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.  
  
    2. Obtenha o serviço de linguagem consultando o provedor de serviços do VSPackage para o GUID do serviço de idioma. Os serviços de linguagem são identificados no registro por extensão de arquivo.  
  
    3. Associe o serviço de linguagem ao <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> chamando seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método.  
  
2. O VSPackage agora pode obter e usar o objeto Colorizer da seguinte maneira:  
  
    > [!NOTE]
    > VSPackages que usam o editor de núcleo não precisam obter explicitamente os objetos Colorizer de um serviço de linguagem. Assim que uma instância do editor central Obtém um serviço de idioma apropriado, ele executa todas as tarefas de colorização mostradas aqui.  
  
    1. Obtenha o objeto Colorizer do serviço de linguagem, que implementa as `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` interfaces e, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método no objeto do serviço de idioma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  
  
    2. Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para obter as informações de Colorizer para um determinado trecho de texto.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Retorna uma matriz de valores, um para cada caractere no intervalo de texto que está sendo colorido. Os valores são índices em uma lista de itens colorable que é a lista de itens colorable padrão mantida pelo editor principal ou uma lista de itens colorable personalizável mantida pelo próprio serviço de linguagem.  
  
    3. Use as informações de colorização retornadas pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para exibir o texto selecionado.  
  
> [!NOTE]
> Além de usar um Colorizer de serviço de linguagem, um VSPackage também pode usar o mecanismo de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] coloração de texto de uso geral. Para obter mais informações sobre esse mecanismo, consulte [usando fontes e cores](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementando a coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)  
 Discute como um editor acessa a cor da sintaxe de um serviço de linguagem e o que o serviço de idioma deve implementar para dar suporte à cor da sintaxe.  
  
 [Como usar itens de coloração internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Demonstra como usar itens coloráveis internos do serviço de linguagem.  
  
 [Itens personalizados que podem ser coloridos](../../extensibility/internals/custom-colorable-items.md)  
 Discute como implementar itens coloráveis personalizados.  
  
## <a name="see-also"></a>Consulte Também  
 [Usando fontes e cores](../../extensibility/using-fonts-and-colors.md)
