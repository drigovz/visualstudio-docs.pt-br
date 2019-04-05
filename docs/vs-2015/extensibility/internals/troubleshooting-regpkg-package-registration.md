---
title: Solução de problemas de registro de pacote RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6337562ff7a043c225dac678cb846cc76384c03c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924660"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solucionando problemas de registro de pacote RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
>  É a maneira preferencial para registrar os pacotes no Visual Studio por meio de arquivos. pkgdef. Isso permite a implantação de extensão sem a necessidade de acessar o registro do sistema. Pkgdef arquivos são criados usando o [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Para registrar um pacote usando o RegPkg no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], você deve usar a versão do RegPkg é apropriado para seu pacote.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versões RegPkg relacionadas a versões de pacote  
 Há duas versões do RegPkg. Uma versão está incluída no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Use esta versão para registrar os pacotes que foram criados usando um dos seguintes assemblies:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   Ele não pode registrar os pacotes que foram criados usando o assembly Microsoft.VisualStudio.Shell.dll anterior.  
  
   A versão anterior do RegPkg pode registrar os pacotes que foram criados usando o assembly Microsoft.VisualStudio.Shell.dll. No entanto, ele não pode registrar os pacotes criados usando versões mais recentes do assembly.  
  
## <a name="see-also"></a>Consulte também  
 [Liberando um produto](../../misc/releasing-a-visual-studio-integration-product.md)
