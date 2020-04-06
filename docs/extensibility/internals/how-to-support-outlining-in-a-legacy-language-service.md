---
title: 'Como: Suporte delineamento em um serviço de idioma legado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707913"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Como: Suporte delineamento em um serviço de idioma legado
O delineamento é usado para expandir ou colapsar diferentes regiões do texto. A forma como o delineamento é usado pode ser definida de forma diferente por diferentes línguas. Para obter mais informações, consulte [Estrutura de tópicos](../../ide/outlining.md).

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais sobre a nova forma de implementar o delineamento, consulte [Passo a Passo: Delineando](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

 O seguinte demonstra como suportar este comando para o seu serviço de idioma.

## <a name="to-support-outlining"></a>Para apoiar o delineamento

1. Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> em seu objeto de serviço de idioma.

2. Convoque <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> o objeto de sessão de delineamento atual para adicionar novas regiões de contorno.

## <a name="robust-programming"></a>Programação robusta
 Quando um usuário seleciona **''''''''Desemrumio',** o IDE chama **Outlining** <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> o serviço de idioma.

 Quando esse método é chamado, o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> IDE passa em um ponteiro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (um ponteiro para um buffer de texto) e um (um ponteiro para a sessão de delineamento atual).

 Você pode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> chamar o método para várias regiões `rgOutlnReg` de contorno especificando essas regiões no parâmetro. O `rgOutlnReg` parâmetro é <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> uma estrutura. Esse processo permite especificar diferentes características da região oculta, como se uma determinada região é expandida ou colapsada.

> [!NOTE]
> Tenha cuidado ao esconder personagens de nova linha. O texto oculto deve se estender desde o início da primeira linha até o último caractere da última linha em uma seção, deixando visível o caractere final da nova linha.

## <a name="see-also"></a>Confira também
- [Como: Fornecer suporte a texto oculto em um serviço de idioma legado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Como: Fornecer suporte de delineamento expandido em um serviço de idioma legado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
