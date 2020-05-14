---
title: Itens coloridos personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708992"
---
# <a name="custom-colorable-items"></a>Itens coloridos personalizados
Você pode substituir a lista de tipos para colorir, como palavras-chave e comentários, implementando itens coloríveis personalizados como parte do seu serviço de idioma.

## <a name="user-settings-of-colorable-items"></a>Configurações do usuário de itens coloridos
 Você pode exibir a caixa de diálogo **Fontes e Cores** selecionando **Opções** no menu **Ferramentas** e, em seguida, selecionando Fontes **e Cores** em **Ambiente**. Quando você seleciona um display, como **Editor de texto** ou janela de **comando,** a caixa de lista **de itens de exibição** mostra todos os itens coloridos para esse display. Você pode visualizar e alterar a fonte, o tamanho, a cor do primeiro plano e a cor de fundo para cada item colorível. Suas escolhas são armazenadas em um cache no registro e acessadas pelo nome do item colorível.

## <a name="presentation-of-colorable-items"></a>Apresentação de itens coloridos
 Como o IDE lida com substituições de itens coloridos na caixa de diálogo **Fontes e Cores,** você só precisa fornecer cada item colorível personalizado com um nome. Este nome é o que aparece na lista **de itens exibir.** Os itens coloridos aparecem em ordem alfabética. Para agrupar os itens coloríveis personalizados do seu serviço de idioma, você pode começar cada nome com o nome do seu idioma, por exemplo **NewLanguage - Comment** and **NewLanguage - Keyword**.

> [!CAUTION]
> Você deve incluir o nome do idioma no nome do item colorível para evitar colisões com nomes de itens coloríveis existentes. Se você alterar o nome de um de seus itens coloridos durante o desenvolvimento, você deve redefinir o cache que foi criado na primeira vez que seus itens coloridos foram acessados. Você pode redefinir o cache experimental com a ferramenta **CreateExpInstance,** que está instalada com o Visual Studio SDK, normalmente no diretório:
>
> *C:\Arquivos de programa (x86)\Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Para redefinir o cache, **digite CreateExpInstance /Reset**. Para obter mais informações sobre **o CreateExpInstance,** consulte [o utilitário CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).

 O primeiro item da sua lista de itens coloridos nunca é referenciado. O primeiro item corresponde a um índice de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] item colorido de 0, e sempre fornece as cores e atributos de texto padrão para esse item. A maneira mais fácil de lidar com este item não referenciado é fornecer um item colorível de espaço reservado em sua lista como o primeiro item.

## <a name="implement-custom-colorable-items"></a>Implementar itens coloráveis personalizados

1. Defina o que deve ser colorido em seu idioma, por exemplo Palavra-chave, Operador e Identificador.

2. Crie uma enumeração desses itens coloridos.

3. Associe os tipos de tokenretornados de um analisador ou scanner com os valores enumerados.

    Por exemplo, os valores que representam os tipos de token podem ser os mesmos valores na enumeração de itens coloráveis personalizados.

4. Na implementação <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> do método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> em seu objeto, preencha a lista de atributos com os valores de sua enumeração de itens coloríveis personalizados correspondentes aos tipos de token retornados do analisador ou scanner.

5. Na mesma classe que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>interface e seus dois métodos, e .

6. Implemente a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Se você quiser suportar valores de cor de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 24 bits ou altos, implemente também a interface.

8. No objeto de serviço do idioma, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> crie uma lista que contenha seus objetos, um para cada item colorível que seu analisador ou scanner pode identificar.

    Você pode acessar cada item da lista usando o valor correspondente da enumeração de itens coloridos personalizados. Use os valores de enumeração como um índice na lista. O primeiro item da lista nunca é acessado, pois corresponde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ao estilo de texto padrão que sempre se compara a si mesmo. Você pode compensar isso inserindo um item colorível no início da lista.

9. Na implementação <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> do método, retorne o número de itens em sua lista de itens coloríveis personalizados.

10. Na implementação <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> do método, retorne o item colorível solicitado da sua lista.

    Para um exemplo de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> implementar as <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>interfaces e interfaces, consulte .

## <a name="see-also"></a>Confira também
- [Modelo de um serviço de linguagem legado](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Colorir sintaxe em editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorir sintaxe em um serviço de linguagem legado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementar coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)
- [Como: Usar itens coloridos incorporados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
