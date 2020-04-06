---
title: Implementando coloração de sintaxe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707643"
---
# <a name="implementing-syntax-coloring"></a>Implementando a coloração de sintaxe
Quando o serviço de idioma fornece colorização de sintaxe, o analisador converte uma linha de texto em uma matriz de itens coloridos e retorna tipos de tokencorrespondentes a esses itens coloridos. O analisador deve retornar tipos de tokens que pertencem a uma lista de itens coloridos. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]exibe cada item colorível na janela de código de acordo com os atributos atribuídos pelo objeto corizador ao tipo de token apropriado.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]não especifica uma interface de analisador, e a implementação do analisador depende completamente de você. No entanto, uma implementação de analisador padrão é fornecida no projeto Visual Studio Language Package. Para código gerenciado, o mpf (managed package framework, quadro de pacotes gerenciados) fornece suporte completo para colorir texto.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais sobre a nova forma de implementar a coloração de sintaxe, consulte [Passo a Passo: Texto de Destaque](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Passos seguidos por um editor para colorir texto

1. O editor obtém o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> colorador <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> chamando o método no objeto.

2. O editor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> chama o método para determinar se o colorador precisa que o estado de cada linha seja mantido fora do colorador.

3. Se o colorador exigir que o estado seja mantido <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> fora do colorador, o editor chama o método para obter o estado da primeira linha.

4. Para cada linha no buffer, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> o editor chama o método, que executa as seguintes etapas:

    1. A linha de texto é passada para um scanner para converter o texto em tokens. Cada token especifica o texto do token e o tipo de token.

    2. O tipo de token é convertido em um índice em uma lista de itens coloridos.

    3. As informações de token são usadas para preencher uma matriz de tal forma que cada elemento da matriz corresponda a um caractere na linha. Os valores armazenados na matriz são os índices na lista de itens coloridos.

    4. O estado no final da linha é devolvido para cada linha.

5. Se o colorador exigir que o estado seja mantido, o editor armazena o estado para essa linha.

6. O editor faz a linha de texto usando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> as informações retornadas do método. Isso exige as seguintes etapas:

    1. Para cada caractere da linha, obtenha o índice de item colorido.

    2. Se usar os itens coloríveis padrão, acesse a lista de itens coloridos do editor.

    3. Caso contrário, chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método do serviço de idiomas para obter um item colorido.

    4. Use as informações no item colorível para renderizar o texto no visor.

## <a name="managed-package-framework-colorizer"></a>Colorador de framework de pacote gerenciado
 O mpf (framework de pacote gerenciado) fornece todas as classes necessárias para implementar um colorador. Sua classe de serviço <xref:Microsoft.VisualStudio.Package.LanguageService> de idiomas deve herdar a classe e implementar os métodos necessários. Você deve fornecer um scanner e <xref:Microsoft.VisualStudio.Package.IScanner> um analisador implementando a <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> interface e retornar uma instância dessa interface <xref:Microsoft.VisualStudio.Package.LanguageService> a partir do método (um dos métodos que devem ser implementados na classe). Para obter mais informações, consulte [Sintaxdimensionar colorir em um serviço de linguagem legado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Confira também
- [Como usar itens de coloração internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Itens personalizados que podem ser coloridos](../../extensibility/internals/custom-colorable-items.md)
- [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
