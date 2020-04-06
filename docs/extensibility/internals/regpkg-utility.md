---
title: Utilitário RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705645"
---
# <a name="regpkg-utility"></a>Utilitário RegPkg
> [!NOTE]
> A maneira preferida de registrar pacotes no Visual Studio é usando arquivos .pkgdef. Isso permite a implantação de extensão sem ter que acessar o registro do sistema, que é um requisito para a implantação do VSIX. Os arquivos Pkgdef são criados usando o [Utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obter mais informações sobre a implantação do pacote Visual Studio, consulte [Shipping Visual Studio Extensions](../../extensibility/shipping-visual-studio-extensions.md).

 O utilitário RegPkg.exe registra um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage com e o prepara para implantação. Este utilitário é usado nos bastidores durante o desenvolvimento do VSPackage. Ele funciona como parte do processo de compilação para que você possa construir e executar um VSPackage na colmeia experimental.

 O RegPkg pode gerar scripts de registro do sistema em vários formatos. Você pode incorporar esses scripts em projetos de implantação, como projetos .msi ou arquivos do Windows Installer XML Toolset.

 O RegPkg.exe está tipicamente localizado no \<caminho de instalação do Visual Studio *SDK*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue esta sintaxe:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Realiza o registro sob o especificado

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Raiz.

 /regfile:FileName Cria um arquivo .reg em vez de atualizar o registro.  Não pode ser usado com /vrgfile ou /rgsfile ou /wixfile.

 /rgsfile:FileName Cria um arquivo .rgs em vez de atualizar o registro.  Não pode ser usado com /vrgfile ou /regfile ou /wixfile.

 /vrgfile:FileName Cria um arquivo .vrg em vez de atualizar o registro.  Não pode ser usado com /regfile ou /rgsfile ou /wixfile.

 /rgm Cria um arquivo .rgm além do arquivo rgs.  Deve ser combinado com /rgsfile.

 /wixfile:FileName Cria um arquivo compatível com o Windows Installer XML Toolset em vez de atualizar o registro.  Não pode ser usado com /regfile ou /rgsfile ou /vrgfile.

 /codebase Forces registro com CodeBase em vez de Assembly.

 /assembly Forces registro com Assembly em vez de CodeBase.

 /unregister Unregisters this package.  Não pode ser usado

 com /regfile ou /vrgfile ou /rgsfile ou /wixfile.

## <a name="see-also"></a>Confira também
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Solucionando problemas de registro de pacote RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
