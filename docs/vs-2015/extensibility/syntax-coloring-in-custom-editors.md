---
title: Cores de sintaxe em editores personalizados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0233873ba5d6ea2fca746f8e12f4bf693b79da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838576"
---
# <a name="syntax-coloring-in-custom-editors"></a>Coloração de sintaxe em editores personalizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os editores do SDK do ambiente do Visual Studio, incluindo o editor principal, usam os serviços de linguagem para identificar itens sintáticos específicos e os exibem com cores especificadas para uma determinada exibição de documento.  
  
## <a name="colorization-requirements"></a>Requisitos de colorização  
 Todos os editores que implementam o Colorizer de um serviço de linguagem devem:  
  
1. Use um objeto que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para gerenciar o texto a ser colorido e um objeto que está implementando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para fornecer uma exibição de documento do texto.  
  
2. Obtenha uma interface para um serviço de idioma específico consultando o provedor de serviços do VSPackage usando o GUID de identificação do serviço de idiomas.  
  
3. Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método de implementação do objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Esse método associa o serviço de linguagem à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementação que o VSPackage usa para gerenciar o texto a ser colorido.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Uso do editor de núcleo do Colorizer de um serviço de linguagem  
 Quando um serviço de linguagem com um Colorizer é obtido por uma instância do editor principal, a análise e renderização de texto por um Colorizer de serviço de linguagem ocorre automaticamente sem a necessidade de nenhuma intervenção adicional de sua parte.  
  
 O IDE de forma transparente:  
  
- Chama o Colorizer conforme necessário para analisar e analisar o texto à medida que ele é adicionado ou modificado na implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
- Garante que a exibição fornecida pelo modo de exibição de documento fornecido pela <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementação seja atualizada e repintada usando as informações retornadas pelo Colorizer.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Uso de editor não núcleo de Colorizer de um serviço de linguagem  
 As instâncias de editor não núcleo também podem usar um serviço de colorização de sintaxe de serviço de linguagem, mas devem recuperar e aplicar explicitamente os Colorizer do serviço e redesenhar suas próprias exibições de documentos.  
  
 Para fazer isso, é necessário um editor que não seja de núcleo para:  
  
1. Obtenha um objeto Colorizer do serviço de linguagem (que implementa `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). Seu VSPackage faz isso chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método na interface do serviço de linguagem.  
  
2. Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método para solicitar que um determinado trecho de texto seja colorido.  
  
     O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método retorna uma matriz de valores, um para cada letra no intervalo de texto que está sendo colorido. Ele também identifica o trecho de texto como um tipo específico de item colorable, como um comentário, uma palavra-chave ou um tipo de dados.  
  
3. Use as informações de colorização retornadas por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> para redesenhar e exibir seu texto.  
  
> [!NOTE]
> Além de usar o Colorizer de um serviço de linguagem, um VSPackage pode optar por usar o mecanismo de coloração de texto do SDK do ambiente do Visual Studio para fins gerais. Para obter mais informações sobre esse mecanismo, consulte [usando fontes e cores](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Cores de sintaxe em um serviço de idioma herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementando a cor da sintaxe](../extensibility/internals/implementing-syntax-coloring.md)   
 [Como: usar itens de cores internos](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Itens personalizados que podem ser coloridos](../extensibility/internals/custom-colorable-items.md)
