---
title: 'Como: Usar itens coloridos embutidos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707784"
---
# <a name="how-to-use-built-in-colorable-items"></a>Como: Usar itens coloridos incorporados
Antes de usar os itens coloridos incorporados, você deve primeiro sinalizar para o ambiente de desenvolvimento integrado (IDE) que você <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> não está fornecendo seus próprios itens coloríveis personalizados, que neste caso seriam objetos. Você faz isso definindo uma entrada de registro para o serviço de idioma.

## <a name="to-use-built-in-colorable-items"></a>Para usar itens coloridos incorporados

1. Sob **HKEY_LOCAL_MACHINE\VisualStudio\\<X.Y>\Languages\Languageservices\\<Language Name\>**, onde \< \<X.Y> é uma versão de e Nome do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] idioma> é o nome do seu idioma, crie um valor de entrada de registro DWORD chamado **RequestStockColors**.

2. Defina o valor de entrada do registro **RequestStockColors** como *1*.

    Depois de criar a entrada de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> registro, o método <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> do seu colorador pode usar os membros da enumeração para preencher a matriz de atributos de cor para uso pelo editor.

   > [!NOTE]
   > Não defina esta entrada de registro se estiver fornecendo itens coloríveis personalizados. Para obter mais informações, consulte [itens coloríveis personalizados](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Confira também
- [Colorir sintaxe em editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorir sintaxe em um serviço de linguagem legado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementando coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)
- [Itens coloridos personalizados](../../extensibility/internals/custom-colorable-items.md)
- [Registre um serviço de idioma legado](../../extensibility/internals/registering-a-legacy-language-service2.md)
