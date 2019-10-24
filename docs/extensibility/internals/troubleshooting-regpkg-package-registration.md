---
title: Solucionando problemas de registro do pacote RegPkg | Microsoft Docs
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
ms.openlocfilehash: 386a1a17c036207d122e4b3c7cb142a628dcfe38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722271"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solucionando problemas de registro de pacote RegPkg
> [!NOTE]
> A maneira preferida de registrar pacotes no Visual Studio é usando arquivos. pkgdef. Isso permite a implantação da extensão sem a necessidade de acessar o registro do sistema. Os arquivos pkgdef são criados usando o [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Para registrar um pacote usando o RegPkg no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você deve usar a versão do RegPkg apropriada para seu pacote.

## <a name="regpkg-versions-related-to-package-versions"></a>Versões do RegPkg relacionadas a versões do pacote
 Há duas versões do RegPkg. Uma versão está incluída no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Use esta versão para registrar pacotes que foram criados usando um dos seguintes assemblies:

1. Microsoft. VisualStudioShell. 9.0. dll

2. Microsoft. VisualStudioShell. 10.0. dll

3. Microsoft. VisualStudioShell. 11.0. dll

   Ele não pode registrar pacotes que foram criados usando o assembly Microsoft. VisualStudio. Shell. dll anterior.

   A versão anterior do RegPkg pode registrar pacotes que foram criados usando o assembly Microsoft. VisualStudio. Shell. dll. No entanto, ele não pode registrar pacotes criados usando versões posteriores desse assembly.

## <a name="see-also"></a>Consulte também
- [VSPackages](../../extensibility/internals/vspackages.md)