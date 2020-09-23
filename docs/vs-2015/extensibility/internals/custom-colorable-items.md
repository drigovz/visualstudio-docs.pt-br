---
title: Itens personalizáveis personalizados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24a4db907ec859c6075c06956f86939047379897
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91102540"
---
# <a name="custom-colorable-items"></a>Itens personalizados que podem ser coloridos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Você pode substituir a lista de tipos para coloração, como palavras-chave e comentários, implementando itens colorable personalizados como parte do seu serviço de idioma.  
  
## <a name="user-settings-of-colorable-items"></a>Configurações de usuário de itens Coloráveis  
 Você pode exibir a caixa de diálogo **fontes e cores** selecionando **Opções** no menu **ferramentas** e, em seguida, selecionando **fontes e cores** em **ambiente**. Quando você seleciona uma exibição, como o **Editor de texto** ou a **janela de comando**, a caixa de listagem **Exibir itens** mostra todos os itens coloráveis para essa exibição. Você pode exibir e alterar a fonte, o tamanho, a cor de primeiro plano e a cor da tela de fundo de cada item que pode ser colorido. Suas opções são armazenadas em um cache no registro e acessadas pelo nome de item com cores.  
  
## <a name="presentation-of-colorable-items"></a>Apresentação de itens Coloráveis  
 Como o IDE trata as substituições de usuários de itens coloráveis na caixa de diálogo **fontes e cores** , você precisa fornecer apenas cada item Colorable personalizado com um nome. Esse nome é o que aparece na lista **Exibir itens** . Os itens coloráveis aparecem em ordem alfabética. Para agrupar os itens personalizáveis personalizados do serviço de idioma, você pode iniciar cada nome com o nome do idioma, por exemplo **NewLanguage-comment** e **NewLanguage-keyword**.  
  
> [!CAUTION]
> Você deve incluir o nome do idioma no nome do item Colorable para evitar colisões com nomes de item Colorable existentes. Se você alterar o nome de um dos seus itens coloráveis durante o desenvolvimento, deverá redefinir o cache que foi criado na primeira vez em que os itens colorable foram acessados. Você pode redefinir o cache experimental com a ferramenta CreateExpInstance, que é instalada com o SDK do Visual Studio, normalmente no diretório  
>   
> **C:\Arquivos de programas (x86) \Microsoft Visual Studio 14.0 \ VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
> Para redefinir o cache, chame `CreateExpInstance /Reset` . Para obter mais informações sobre CreateExpInstance, consulte [utilitário CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 O primeiro item na lista de itens coloráveis nunca é referenciado. O primeiro item corresponde a um índice de item colorável de 0 e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sempre fornece as cores de texto padrão e os atributos para esse item. A maneira mais fácil de lidar com esse item não referenciado é fornecer um item de espaço reservado em cores na sua lista como o primeiro item.  
  
## <a name="implementing-custom-colorable-items"></a>Implementando itens colorable personalizados  
  
1. Defina o que deve ser colorido em seu idioma, por exemplo, palavra-chave, operador e identificador.  
  
2. Crie uma enumeração desses itens coloráveis.  
  
3. Associe os tipos de token retornados de um analisador ou scanner com os valores enumerados.  
  
    Por exemplo, os valores que representam os tipos de token podem ser os mesmos valores na enumeração de itens colorable personalizados.  
  
4. Em sua implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método em seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> objeto, preencha a lista de atributos com os valores de sua enumeração de itens colorable personalizados correspondentes aos tipos de token retornados do analisador ou do scanner.  
  
5. Na mesma classe que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface, implemente a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface e seus dois métodos, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .  
  
6. Implemente a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7. Se você quiser oferecer suporte a valores de cores de 24 ou de cor alta, também implemente a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface.  
  
8. No seu objeto de serviço de idioma, crie uma lista que contém seus <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objetos, uma para cada item que pode ser colorido que seu analisador ou scanner possa identificar.  
  
    Você pode acessar cada item na lista usando o valor correspondente da enumeração de itens colorable personalizados. Use os valores de enumeração como um índice na lista. O primeiro item da lista nunca é acessado, pois corresponde ao estilo de texto padrão que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sempre se manipula. Você pode compensar isso inserindo um item de espaço reservado no início da lista.  
  
9. Em sua implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método, retorne o número de itens na sua lista de itens colorable personalizados.  
  
10. Em sua implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método, retorne o item Colorable solicitado da sua lista.  
  
    Para obter um exemplo de como implementar as <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaces e, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .  
  
## <a name="see-also"></a>Consulte Também  
 [Modelo de um serviço de linguagem herdado](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Cores de sintaxe em editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Cores de sintaxe em um serviço de idioma herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementando a cor da sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Como usar itens de coloração internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
