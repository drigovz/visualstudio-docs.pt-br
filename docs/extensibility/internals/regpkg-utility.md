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
ms.openlocfilehash: e5b4e6384730492e0f34470bbe4676ce0d9012c3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310973"
---
# <a name="regpkg-utility"></a>Utilitário RegPkg
> [!NOTE]
> É a maneira preferencial para registrar os pacotes no Visual Studio por meio de arquivos. pkgdef. Isso permite a implantação de extensão sem a necessidade de acessar o registro do sistema, que é um requisito para a implantação do VSIX. Pkgdef arquivos são criados usando o [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obter mais informações sobre a implantação de pacote do Visual Studio, consulte [envio extensões do Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 O utilitário RegPkg.exe registra um VSPackage com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e prepará-lo para implantação. Esse utilitário é usado nos bastidores durante o desenvolvimento de VSPackage. Ele é executado como parte do processo de compilação para que você pode compilar e executar um VSPackage no hive experimental.

 RegPkg pode gerar scripts de registro do sistema em vários formatos. Você pode incorporar esses scripts em projetos de implantação, como arquivos de conjunto de ferramentas do Windows Installer XML ou projetos. msi.

 RegPkg.exe normalmente está localizado em \< *caminho de instalação do SDK do Visual Studio*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue esta sintaxe:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root realiza registro sob especificado

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] raiz.

 /regfile:filename cria um arquivo. reg em vez de atualizar o registro.  Não pode ser usado com /vrgfile ou /rgsfile ou /wixfile.

 /rgsfile:filename cria um arquivo. rgs em vez de atualizar o registro.  Não pode ser usado com /vrgfile ou /regfile ou /wixfile.

 /vrgfile:filename cria um arquivo .vrg em vez de atualizar o registro.  Não pode ser usado com /regfile ou /rgsfile ou /wixfile.

 /rgm cria um arquivo de .rgm além do arquivo rgs.  Deve ser combinada com /rgsfile.

 /wixfile:filename cria um arquivo compatível com o Windows Installer XML conjunto de ferramentas em vez de atualizar o registro.  Não pode ser usado com /regfile ou /rgsfile ou /vrgfile.

 /codebase registro forças com base de código em vez de um Assembly.

 registro de forças de /assembly com o Assembly em vez da Base de código.

 /unregister Unregisters esse pacote.  Não pode ser usado

 com /regfile ou /vrgfile ou /rgsfile ou /wixfile.

## <a name="see-also"></a>Consulte também
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Solucionar problemas de registro de pacote RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)