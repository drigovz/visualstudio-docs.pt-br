---
title: Utilitário RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f811eb37da730d63e199a0e378b8a9122143649e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724445"
---
# <a name="regpkg-utility"></a>Utilitário RegPkg
> [!NOTE]
> A maneira preferida de registrar pacotes no Visual Studio é usando arquivos. pkgdef. Isso permite a implantação da extensão sem a necessidade de acessar o registro do sistema, que é um requisito para a implantação do VSIX. Os arquivos pkgdef são criados usando o [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obter mais informações sobre a implantação de pacote do Visual Studio, consulte [enviando extensões do Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 O utilitário RegPkg. exe registra um VSPackage com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e o prepara para implantação. Esse utilitário é usado nos bastidores durante o desenvolvimento de VSPackage. Ele é executado como parte do processo de compilação para que você possa compilar e executar um VSPackage no hive experimental.

 O RegPkg pode gerar scripts de registro do sistema em vários formatos. Você pode incorporar esses scripts em projetos de implantação, como projetos. msi ou Windows Installer arquivos de conjunto de ferramentas XML.

 O RegPkg. exe normalmente está localizado em \<*caminho de instalação do SDK do Visual Studio*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue esta sintaxe:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root: a raiz executa o registro sob o especificado

 raiz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 /regfile: FileName cria um arquivo. reg em vez de atualizar o registro.  Não pode ser usado com/vrgfile ou/rgsfile ou/wixfile.

 /rgsfile: FileName cria um arquivo. rgs em vez de atualizar o registro.  Não pode ser usado com/vrgfile ou/regfile ou/wixfile.

 /vrgfile: FileName cria um arquivo. VRG em vez de atualizar o registro.  Não pode ser usado com/regfile ou/rgsfile ou/wixfile.

 /RGM cria um arquivo. RGM além do arquivo RGS.  Deve ser combinado com/rgsfile.

 /wixfile: FileName cria um Windows Installer arquivo compatível com o conjunto de ferramentas XML em vez de atualizar o registro.  Não pode ser usado com/regfile ou/rgsfile ou/vrgfile.

 /codebase força o registro com CodeBase em vez de assembly.

 /assembly força o registro com assembly em vez de CodeBase.

 /unregister Cancela o registro deste pacote.  Não pode ser usado

 com/regfile ou/vrgfile ou/rgsfile ou/wixfile.

## <a name="see-also"></a>Consulte também
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Solucionar problemas de registro de pacote RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)