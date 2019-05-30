---
title: Solução de problemas de registro de pacote RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 219a21eac296daa442fc2f705eb2758790777333
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344749"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solucionando problemas de registro de pacote RegPkg
> [!NOTE]
> É a maneira preferencial para registrar os pacotes no Visual Studio por meio de arquivos. pkgdef. Isso permite a implantação de extensão sem a necessidade de acessar o registro do sistema. Pkgdef arquivos são criados usando o [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Para registrar um pacote usando o RegPkg no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você deve usar a versão do RegPkg é apropriado para seu pacote.

## <a name="regpkg-versions-related-to-package-versions"></a>Versões RegPkg relacionadas a versões de pacote
 Há duas versões do RegPkg. Uma versão está incluída no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Use esta versão para registrar os pacotes que foram criados usando um dos seguintes assemblies:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Ele não pode registrar os pacotes que foram criados usando o assembly Microsoft.VisualStudio.Shell.dll anterior.

   A versão anterior do RegPkg pode registrar os pacotes que foram criados usando o assembly Microsoft.VisualStudio.Shell.dll. No entanto, ele não pode registrar os pacotes criados usando versões mais recentes do assembly.

## <a name="see-also"></a>Consulte também
- [VSPackages](../../extensibility/internals/vspackages.md)