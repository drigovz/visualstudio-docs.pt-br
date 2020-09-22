---
title: Utilitário RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838606"
---
# <a name="regpkg-utility"></a>Utilitário RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> A maneira preferida de registrar pacotes no Visual Studio é usando arquivos. pkgdef. Isso permite a implantação da extensão sem a necessidade de acessar o registro do sistema, que é um requisito para a implantação do VSIX. Os arquivos pkgdef são criados usando o [utilitário CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obter mais informações sobre a implantação de pacote do Visual Studio, consulte [enviando extensões do Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 O utilitário RegPkg.exe registra um VSPackage com o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e o prepara para implantação. Esse utilitário é usado nos bastidores durante o desenvolvimento de VSPackage. Ele é executado como parte do processo de compilação para que você possa compilar e executar um VSPackage no hive experimental.  
  
 O RegPkg pode gerar scripts de registro do sistema em vários formatos. Você pode incorporar esses scripts em projetos de implantação, como projetos. msi ou Windows Installer arquivos de conjunto de ferramentas XML.  
  
 O RegPkg.exe normalmente está localizado em \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue esta sintaxe:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root: raiz  
 Executa o registro sob o especificado  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] básica.  
  
 /regfile: FileName  
 Cria um arquivo. reg em vez de atualizar o registro.  Não pode ser usado com/vrgfile ou/rgsfile ou/wixfile.  
  
 /rgsfile: nome de arquivo  
 Cria um arquivo. rgs em vez de atualizar o registro.  Não pode ser usado com/vrgfile ou/regfile ou/wixfile.  
  
 /vrgfile: nome de arquivo  
 Cria um arquivo. VRG em vez de atualizar o registro.  Não pode ser usado com/regfile ou/rgsfile ou/wixfile.  
  
 /rgm  
 Cria um arquivo. RGM além do arquivo RGS.  Deve ser combinado com/rgsfile.  
  
 /wixfile: nome de arquivo  
 Cria um arquivo compatível com o conjunto de ferramentas XML Windows Installer em vez de atualizar o registro.  Não pode ser usado com/regfile ou/rgsfile ou/vrgfile.  
  
 /codebase  
 Força o registro com CodeBase em vez de assembly.  
  
 /assembly  
 Força o registro com assembly em vez de CodeBase.  
  
 /Unregister  
 Cancela o registro deste pacote.  Não pode ser usado  
  
 com/regfile ou/vrgfile ou/rgsfile ou/wixfile.  
  
## <a name="see-also"></a>Consulte Também  
 [Lançando um produto](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Solucionando problemas de registro de pacote RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
