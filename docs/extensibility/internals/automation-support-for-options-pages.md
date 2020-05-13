---
title: Suporte de automação para páginas de opções | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709926"
---
# <a name="automation-support-for-options-pages"></a>Suporte à automação para páginas de opções
O VSPackages pode fornecer caixas de diálogo **de opções** personalizadas para o menu **Ferramentas** (páginas**de opções de ferramentas)** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e pode disponibilizá-las para o modelo de automação.

## <a name="tools-options-pages"></a>páginas de Opções de Ferramentas
 Para criar uma página **de Opções de Ferramentas,** um VSPackage deve fornecer uma implementação de controle de usuário retornada ao ambiente através da implementação do método DO <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> VSPackage. (Ou, para código gerenciado, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> o método.)

 É opcional, mas fortemente incentivado, para permitir o acesso a esta nova página através do modelo de automação. Você pode fazê-lo com as seguintes etapas:

1. Estender <xref:EnvDTE._DTE.Properties%2A> o objeto através da implementação de um objeto derivado do IDispatch.

2. Retorne uma implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método (ou <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> para código gerenciado do método) para o objeto derivado do IDispatch.

3. Quando um consumidor <xref:EnvDTE._DTE.Properties%2A> de automação chama o método em <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> uma página de propriedade de **opção** personalizada, o ambiente usa o método para obter a implementação de automação de uma página de **opções** de ferramentas personalizadas.

4. O objeto de automação do VSPackage <xref:EnvDTE.Property> é então <xref:EnvDTE._DTE.Properties%2A>usado para fornecer cada um devolvido por .

   Para obter uma amostra implementando uma página de **opções** de ferramentas personalizadas, consulte [AMOSTRAS VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Confira também
- [Expor objetos do projeto](../../extensibility/internals/exposing-project-objects.md)
