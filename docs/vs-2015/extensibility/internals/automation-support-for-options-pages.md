---
title: Suporte de automação para páginas de opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157250"
---
# <a name="automation-support-for-options-pages"></a>Suporte à automação para páginas de opções
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O VSPackages pode fornecer caixas de diálogo de **Opções** personalizadas ao menu **ferramentas** (ferramentas opções páginas) no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e pode torná-las disponíveis para o modelo de automação.  
  
## <a name="tools-options-pages"></a>Páginas de opções de ferramentas  
 Para criar uma página de **Opções de ferramentas** , um VSPackage deve fornecer uma implementação de controle de usuário retornada ao ambiente por meio da implementação do VSPackage do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método (ou para código gerenciado, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método).  
  
 É opcional, mas altamente recomendável permitir o acesso a essa nova página por meio do modelo de automação. Você pode fazer isso por meio das seguintes etapas:  
  
1. Estenda o <xref:EnvDTE._DTE.Properties%2A> objeto por meio da implementação de um objeto derivado de IDispatch.  
  
2. Retornar uma implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método (ou para código gerenciado o <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> método) para o objeto derivado de IDispatch.  
  
3. Quando um consumidor de automação chama o <xref:EnvDTE._DTE.Properties%2A> método em uma página de propriedades de **opção** personalizada, o ambiente usa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método para obter a implementação de automação de uma página de **Opções de ferramentas** personalizadas.  
  
4. O objeto Automation do VSPackage é usado para fornecer cada um deles <xref:EnvDTE.Property> retornado por <xref:EnvDTE._DTE.Properties%2A> .  
  
   Para obter um exemplo de implementação de uma página de opções de ferramentas personalizadas, consulte [exemplos de VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Expondo objetos do projeto](../../extensibility/internals/exposing-project-objects.md)
