---
title: Suporte de automação para páginas de opções | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03360bfc01110e7b4ef73956f0199aaaed9cee2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848967"
---
# <a name="automation-support-for-options-pages"></a>Suporte de automação para páginas de opções
VSPackages pode fornecer caixas de diálogo de **Opções** personalizadas ao menu **ferramentas** (**ferramentas opções** páginas) no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e pode disponibilizá-las para o modelo de automação.

## <a name="tools-options-pages"></a>páginas de Opções de Ferramentas
 Para criar uma página de **Opções de ferramentas** , um VSPackage deve fornecer uma implementação de controle de usuário retornada ao ambiente por meio da implementação do VSPackage do método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>. (Ou, para o código gerenciado, o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>.)

 É opcional, mas altamente recomendável permitir o acesso a essa nova página por meio do modelo de automação. Você pode fazer isso com as seguintes etapas:

1. Estenda o objeto <xref:EnvDTE._DTE.Properties%2A> por meio da implementação de um objeto derivado de IDispatch.

2. Retorne uma implementação do método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (ou para código gerenciado o método <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>) para o objeto derivado de IDispatch.

3. Quando um consumidor de automação chama o método <xref:EnvDTE._DTE.Properties%2A> em uma página de propriedades de **opção** personalizada, o ambiente usa o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> para obter a implementação de automação de uma página de **Opções de ferramentas** personalizadas.

4. O objeto Automation do VSPackage é usado para fornecer cada <xref:EnvDTE.Property> retornado pelo <xref:EnvDTE._DTE.Properties%2A>.

   Para obter um exemplo de implementação de uma página de **Opções de ferramentas** personalizadas, consulte [exemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Veja também
- [Expor objetos do projeto](../../extensibility/internals/exposing-project-objects.md)
