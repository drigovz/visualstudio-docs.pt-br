---
title: Visão geral de fonte e cor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204354"
---
# <a name="font-and-color-overview"></a>Visão geral de cor e de fonte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico discute as configurações de fonte e cor do texto no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE). Ele também apresenta os conceitos de categorias e itens de exibição e descreve como o VSPackages e o editor de núcleo usam atributos de texto.  
  
## <a name="the-fonts-and-colors-property-page"></a>A página de propriedades de fontes e cores  
 Você pode gerenciar atributos de texto exibido no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE) por meio da página de propriedades **fontes e cores** . Para localizar a página de propriedades **fontes e cores** , no menu **ferramentas** , clique em **Opções**. Expanda **Ambiente**e depois clique em **Fontes e Cores**.  
  
## <a name="categories-and-display-items"></a>Categorias e itens de exibição  
 As fontes e as cores são organizadas em **categorias** e **itens de exibição**.  
  
- Uma **categoria** é um contêiner lógico ou funcional para vários itens de **exibição**.  
  
   Uma lista de **categorias** está na caixa suspensa **Mostrar configurações para** da página de propriedades **fontes e cores** .  
  
- Um **item de exibição** é uma entidade de texto bem definida, como um comentário, uma cadeia de caracteres ou uma estrutura de controle que deve ser Colorada quando exibida.  
  
  Cada **item de exibição** é definido exclusivamente dentro da **categoria** que o contém. Consequentemente, mais de uma **categoria** pode ter um **item de exibição** com o mesmo nome.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Controle VSPackage de fontes e cores  
 O [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] permite que o VSPackages:  
  
- Defina as **categorias**de fonte e cor.  
  
- Especifique as fontes e cores usadas para apresentar **itens de exibição**.  
  
- Interaja com a página de propriedades **fontes e cores** .  
  
- Agregue várias **categorias** em grupos.  
  
- Persistir alterações nas configurações padrão.  
  
  Há duas maneiras de interagir com as seleções de fonte e cor dentro do [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- Uma maneira é chamada de *coloração de sintaxe*. Ele é usado por um VSPackage que personaliza o editor existente [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para implementar um serviço de linguagem e criar um editor de origem.  
  
   Apenas uma **categoria** dá suporte a esse mecanismo, ou seja, o **Editor de texto**.  
  
- Uma alternativa mais geral dá suporte a todas as outras **categorias** e componentes de interface do usuário além do editor de origem ao exibir texto. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Configurações de texto do editor de núcleo  
 As configurações de fonte e cor do editor principal de um objeto de serviço de idioma são governadas pelo **texto EditorCategory** encontrado na caixa suspensa **Mostrar configurações para** da página de propriedades **fontes e cores** .  
  
 Ao trabalhar com editores, você deve usar a fonte especializada e o mecanismo de controle de cor que o serviço de linguagem fornece para controlar e estender as configurações do **Editor de texto** . O mecanismo é chamado de *coloração de sintaxe* e fornece:  
  
- Uma técnica simplificada para gerenciar as fontes e cores de itens de exibição.  
  
   Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- Um mecanismo de colorização bem definido e otimizado.  
  
   Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- A capacidade de usar itens de exibição internos do **texto EditorCategory** e estendê-los.  
  
   Para obter mais informações, consulte [como: usar itens coloráveis internos](../extensibility/internals/how-to-use-built-in-colorable-items.md) e [itens personalizáveis personalizados](../extensibility/internals/custom-colorable-items.md).  
  
- Persistência automática do estado atual de itens de exibição internos e personalizados com a categoria editor de **texto** .  
  
  Para obter mais informações sobre cores de sintaxe, consulte [cores de sintaxe em um serviço de linguagem herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces herdadas no editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Coloração de sintaxe em um serviço de linguagem herdado](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
