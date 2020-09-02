---
title: Usando fontes e cores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177231"
---
# <a name="using-fonts-and-colors"></a>Usando fontes e cores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] fornece suporte para o uso de fontes e cores para exibir texto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de cor e de fonte](../extensibility/font-and-color-overview.md)  
 Discute as configurações de fonte e cor do texto no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE). Também apresenta os conceitos de categorias e itens de exibição e descreve como o VSPackages e o editor de núcleo usam atributos de texto.  
  
 [Obtenção de informações de cores e fontes para colorização de texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Fornece diretrizes para implementar a colorização de texto em VSPackages que gerenciam **categorias** diferentes do **Editor de texto**.  
  
 [Acessando as configurações de cores e fontes armazenadas](../extensibility/accessing-stored-font-and-color-settings.md)  
 Explica como as configurações atuais de fonte e cor podem ser armazenadas, recuperadas e aplicadas.  
  
 [Implementando itens de exibição e categorias personalizadas](../extensibility/implementing-custom-categories-and-display-items.md)  
 Descreve as etapas básicas pelas quais uma janela pode criar e usar seus próprios itens e **categorias** de **exibição** para dar suporte à exibição de texto.  
  
 Essa abordagem requer um VSPackage para implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface e as interfaces relacionadas.  
  
 [Como acessar o esquema interno de cores e fontes](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Discute como definir e registrar uma categoria usando fontes e cores internas e iniciar o uso de fontes e cores fornecidas pelo sistema.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Fornece uma instância do `IVsFontAndColorDefaults` ou a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface que corresponde a um item específico listado na lista **Mostrar configurações de** na página **fontes e cores** da caixa de diálogo **Opções** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Permite que um VSPackage dê suporte à página **fontes e cores** do IDE definindo fontes e cores padrão para uma janela ou componente de interface do usuário.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Fornece um mecanismo pelo qual um VSPackage que fornece suporte a fontes e cores pode especificar um grupo de itens de exibição – uma supercategoria que representa a União de duas ou mais categorias.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Permite que um VSPackage recupere dados de fonte e cor ou salve-os no registro.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifica VSPackages que estão usando informações de fonte e cor sobre alterações nas configurações de fonte e cor.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Fornece ferramentas para trabalhar com os dados de entrada e saída que são usados pelos métodos do mecanismo de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **fonte e cor** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Controla o cache das configurações de fonte e cor.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Desenvolvendo um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)  
 Discute como o VSPackages pode usar serviços de linguagem para personalizar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
 [Coloração de sintaxe em editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries como o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor usa os serviços de linguagem para implementar a coloração de sintaxe.  
  
 [Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica como usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] os serviços do para criar elementos de interface do usuário que correspondam ao restante do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .
