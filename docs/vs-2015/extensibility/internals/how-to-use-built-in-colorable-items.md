---
title: 'Como: usar itens de cores internas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838332"
---
# <a name="how-to-use-built-in-colorable-items"></a>Como usar itens de coloração internos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Antes de usar os itens coloridos internos, você deve primeiro sinalizar para o IDE (ambiente de desenvolvimento integrado) que você não está fornecendo seus próprios itens personalizáveis personalizados, que nesse caso seriam <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objetos. Você faz isso definindo uma entrada de registro para o serviço de idioma.  
  
### <a name="to-use-built-in-colorable-items"></a>Para usar itens coloráveis internos  
  
1. Em HKEY_LOCAL_MACHINE \VisualStudio \\ *X. Y*\Languages\Language Services \\ *nome do idioma*, em que *X. y* é uma versão do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e *nome do idioma* é o nome do seu idioma, crie um valor de entrada do Registro DWORD chamado `RequestStockColors` .  
  
2. Defina o `RequestStockColors` valor de entrada do registro como 1.  
  
     Depois de criar a entrada do registro, o método de Colorizer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> pode usar os membros da <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumeração para preencher a matriz de atributos de cor para uso pelo editor.  
  
    > [!NOTE]
    > Não defina essa entrada de registro se você estiver fornecendo itens coloridos personalizados. Para obter mais informações, consulte [itens colorable personalizados](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Cores de sintaxe em editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Cores de sintaxe em um serviço de idioma herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementando a cor da sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Itens coloridos personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service2.md)
