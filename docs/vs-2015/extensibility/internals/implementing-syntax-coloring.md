---
title: Implementando a cor da sintaxe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90ff340efb4cbdbe6e2ac43b5b459642120cc099
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838428"
---
# <a name="implementing-syntax-coloring"></a>Implementando a coloração de sintaxe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando o serviço de linguagem fornece a colorização de sintaxe, o analisador converte uma linha de texto em uma matriz de itens coloráveis e retorna tipos de token correspondentes a esses itens coloráveis. O analisador deve retornar tipos de token que pertençam a uma lista de itens coloráveis. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] exibe cada item colorável na janela de código de acordo com os atributos atribuídos pelo objeto Colorizer ao tipo de token apropriado.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] não especifica uma interface do analisador, e a implementação do analisador é completamente ativada para você. No entanto, uma implementação de analisador padrão é fornecida no projeto de pacote de linguagem do Visual Studio. Para código gerenciado, a MPF (estrutura de pacote gerenciada) fornece suporte completo para colorir o texto.  
  
 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente de implementar recursos de serviço de linguagem é usar extensões de MEF. Para saber mais sobre a nova maneira de implementar a coloração de sintaxe, consulte [Walkthrough: realce Text](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
> Recomendamos que você comece a usar a nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de linguagem e permitirá que você aproveite os novos recursos do editor.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Etapas seguidas por um editor para colorir o texto  
  
1. O editor Obtém o Colorizer chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objeto.  
  
2. O editor chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> método para determinar se o Colorizer precisa que o estado de cada linha seja mantido fora do Colorizer.  
  
3. Se o Colorizer exigir que o estado seja mantido fora do Colorizer, o editor chamará o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> método para obter o estado da primeira linha.  
  
4. Para cada linha no buffer, o editor chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método, que executa as seguintes etapas:  
  
    1. A linha de texto é passada para um scanner para converter o texto em tokens. Cada token especifica o texto do token e o tipo de token.  
  
    2. O tipo de token é convertido em um índice em uma lista de itens colorable.  
  
    3. As informações de token são usadas para preencher uma matriz de modo que cada elemento da matriz corresponda a um caractere na linha. Os valores armazenados na matriz são os índices na lista de itens colorable.  
  
    4. O estado no final da linha é retornado para cada linha.  
  
5. Se o Colorizer exigir que o estado seja mantido, o editor armazenará em cache o estado dessa linha.  
  
6. O editor renderiza a linha de texto usando as informações retornadas do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método. Isso exige as seguintes etapas:  
  
    1. Para cada caractere na linha, obtenha o índice de item com cores.  
  
    2. Se você estiver usando os itens colorable padrão, acesse a lista de itens coloráveis do editor.  
  
    3. Caso contrário, chame o método do serviço de linguagem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> para obter um item com cores.  
  
    4. Use as informações no item Colorable para renderizar o texto na exibição.  
  
## <a name="managed-package-framework-colorizer"></a>Estrutura de pacote gerenciado Colorizer  
 A MPF (estrutura de pacote gerenciada) fornece todas as classes necessárias para implementar um Colorizer. Sua classe de serviço de linguagem deve herdar a <xref:Microsoft.VisualStudio.Package.LanguageService> classe e implementar os métodos necessários. Você deve fornecer um scanner e um analisador implementando a <xref:Microsoft.VisualStudio.Package.IScanner> interface e retornar uma instância dessa interface do <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método (um dos métodos que devem ser implementados na <xref:Microsoft.VisualStudio.Package.LanguageService> classe). Para obter mais informações, consulte [colorir sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Como: usar itens de cores internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Itens coloridos personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
