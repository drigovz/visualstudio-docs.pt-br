---
title: Solução de problemas Registro do pacote RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704323"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solucionando problemas de registro de pacote RegPkg
> [!NOTE]
> A maneira preferida de registrar pacotes no Visual Studio é usando arquivos .pkgdef. Isso permite a implantação de extensão sem ter que acessar o registro do sistema. Os arquivos Pkgdef são criados usando o [Utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Para registrar um pacote usando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]RegPkg in, você deve usar a versão de RegPkg que é apropriada para o seu pacote.

## <a name="regpkg-versions-related-to-package-versions"></a>Versões regPkg relacionadas com versões do pacote
 Há duas versões do RegPkg. Uma versão está [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]incluída em . Use esta versão para registrar pacotes que foram construídos usando um dos seguintes conjuntos:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Ele não pode registrar pacotes que foram construídos usando o conjunto microsoft.visualstudio.shell.dll anterior.

   A versão anterior do RegPkg pode registrar pacotes que foram construídos usando o conjunto Microsoft.VisualStudio.Shell.dll. No entanto, ele não pode registrar pacotes construídos usando versões posteriores desse conjunto.

## <a name="see-also"></a>Confira também
- [VSPackages](../../extensibility/internals/vspackages.md)
