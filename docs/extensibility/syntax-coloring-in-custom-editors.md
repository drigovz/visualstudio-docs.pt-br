---
title: Cores de sintaxe em editores personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4302f463d93776d17be0251e6194375c15adc19
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718764"
---
# <a name="syntax-coloring-in-custom-editors"></a>Coloração de sintaxe em editores personalizados
Os editores do SDK do ambiente do Visual Studio, incluindo o editor principal, usam os serviços de linguagem para identificar itens sintáticos específicos e os exibem com cores especificadas para uma determinada exibição de documento.

## <a name="colorization-requirements"></a>Requisitos de colorização
 Todos os editores que implementam o Colorizer de um serviço de linguagem devem:

1. Use um objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para gerenciar o texto a ser colorido e um objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para fornecer uma exibição de documento do texto.

2. Obtenha uma interface para um serviço de idioma específico consultando o provedor de serviços do VSPackage usando o GUID de identificação do serviço de idiomas.

3. Chame o método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> do objeto que está implementando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Esse método associa o serviço de linguagem com a implementação de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> que o VSPackage usa para gerenciar o texto a ser colorido.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Uso do editor de núcleo do Colorizer de um serviço de linguagem
 Quando um serviço de linguagem com um Colorizer é obtido por uma instância do editor principal, a análise e renderização de texto por um Colorizer de serviço de linguagem ocorre automaticamente sem a necessidade de nenhuma intervenção adicional de sua parte.

 O IDE de forma transparente:

- Chama o Colorizer conforme necessário para analisar e analisar o texto à medida que ele é adicionado ou modificado na implementação de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

- Garante que a exibição fornecida pelo modo de exibição de documento fornecido pela implementação de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> seja atualizada e repintada usando as informações retornadas pelo Colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Uso de editor não núcleo de Colorizer de um serviço de linguagem
 As instâncias de editor não núcleo também podem usar um serviço de colorização de sintaxe de serviço de linguagem, mas devem recuperar e aplicar explicitamente o Colorizer do serviço e redesenhar suas próprias exibições de documento.

 Para fazer isso, um editor não principal deve:

1. Obtenha um objeto Colorizer do serviço de linguagem (que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). O VSPackage faz isso chamando o método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> na interface do serviço de linguagem.

2. Chame o método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para solicitar que um determinado trecho de texto seja colorido.

     O método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> retorna uma matriz de valores, um para cada letra no intervalo de texto que está sendo colorido. Ele também identifica o trecho de texto como um tipo específico de item colorable, como um comentário, uma palavra-chave ou um tipo de dados.

3. Use as informações de colorização retornadas por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> redesenhar e exibir seu texto.

> [!NOTE]
> Além de usar o Colorizer de um serviço de linguagem, um VSPackage pode optar por usar o mecanismo de coloração de texto do SDK do ambiente do Visual Studio para fins gerais. Para obter mais informações sobre esse mecanismo, consulte [usando fontes e cores](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Consulte também

- [Coloração de sintaxe em um serviço de linguagem herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementar a coloração de sintaxe](../extensibility/internals/implementing-syntax-coloring.md)
- [Como usar itens de coloração internos](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Itens de coloração personalizados](../extensibility/internals/custom-colorable-items.md)