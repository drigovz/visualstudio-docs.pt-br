---
title: Sintaxe colorindo em editores personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699335"
---
# <a name="syntax-coloring-in-custom-editors"></a>Coloração de sintaxe em editores personalizados
Os editores do Visual Studio Environment SDK, incluindo o editor principal, usam serviços de linguagem para identificar itens sintáticos específicos e exibi-los com cores especificadas para uma determinada exibição de documento.

## <a name="colorization-requirements"></a>Requisitos de colorização
 Todos os editores que implementam o colorador de um serviço de idiomas devem:

1. Use uma implementação de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto para gerenciar o texto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a ser colorido e um objeto implementando para fornecer uma visualização documental do texto.

2. Obtenha uma interface para um determinado serviço de idioma consultando o provedor de serviços do VSPackage usando o GUID de identificação do serviço de idiomas.

3. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> o método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>implementação do objeto . Este método associa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> serviço de idiomas à implementação que o VSPackage usa para gerenciar o texto que deve ser colorido.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Uso do editor principal do colorador de um serviço de idiomas
 Quando um serviço de idioma com um colorador é obtido por uma instância do editor principal, a análise e renderização de texto pelo colorador de um serviço de idioma ocorre automaticamente sem exigir qualquer intervenção adicional de sua parte.

 O IDE de forma transparente:

- Chama o colorador conforme necessário para analisar e analisar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>texto à medida que é adicionado ou modificado na implementação de .

- Garante que o visor fornecido pela <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> exibição do documento fornecido pela implementação seja atualizado e repintado usando as informações devolvidas pelo colorador.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Uso não-core do editor do colorador de um serviço de idiomas
 As instâncias de editor não-core também podem usar o serviço de coloração de sintaxe de um serviço de idiomas, mas eles devem recuperar e aplicar explicitamente o colorador do serviço e repintar suas próprias visualizações de documentos.

 Para fazer isso, um editor não-core deve:

1. Obtenha o objeto colorizador de um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>serviço de idioma (que implementa e ). O VSPackage faz isso <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> chamando o método na interface do serviço de idiomas.

2. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> o método para solicitar que um determinado período de texto seja colorido.

     O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método retorna uma matriz de valores, uma para cada letra no período de texto que está sendo colorido. Ele também identifica o período de texto como um tipo particular de item colorível, como um comentário, palavra-chave ou tipo de dados.

3. Use as informações de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> colorização retornadas para repintar e exibir seu texto.

> [!NOTE]
> Além de usar o colorador de um serviço de idiomas, um VSPackage pode optar por usar o mecanismo de coloração de texto Visual Studio Environment SDK de uso geral. Para obter mais informações sobre este mecanismo, consulte [Usando fontes e cores](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="see-also"></a>Confira também

- [Coloração de sintaxe em um serviço de linguagem herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementando a coloração de sintaxe](../extensibility/internals/implementing-syntax-coloring.md)
- [Como usar itens de coloração internos](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Itens personalizados que podem ser coloridos](../extensibility/internals/custom-colorable-items.md)
