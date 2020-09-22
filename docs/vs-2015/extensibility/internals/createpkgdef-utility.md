---
title: Utilitário CreatePkgDef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838299"
---
# <a name="createpkgdef-utility"></a>Utilitário CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usa um arquivo. dll para uma extensão do Visual Studio como um parâmetro e cria um arquivo. pkgdef para acompanhar o. dll. O arquivo. pkgdef contém todas as informações que, de outra forma, seriam gravadas no registro do sistema quando a extensão é instalada.  
  
> [!NOTE]
> A maioria dos modelos de projeto incluídos no SDK do Visual Studio criam automaticamente arquivos. pkgdef como parte do processo de compilação. Este documento destina-se a aqueles que desejam criar pacotes manualmente ou converter pacotes existentes para usar a implantação do. pkgdef.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumentos  
 /out =`FileName`  
 Necessário. Define o nome do arquivo de saída. pkgdef como `FileName` .  
  
 /codebase  
 Opcional. Força o registro com o utilitário CodeBase.  
  
 /assembly  
 Força o registro com o utilitário assembly.  
  
 `AssemblyPath`  
 O caminho do arquivo. dll do qual você deseja gerar o. pkgdef.  
  
## <a name="remarks"></a>Comentários  
 A implantação de extensão usando arquivos. pkgdef substitui os requisitos de registro de versões anteriores do Visual Studio.  
  
 Os arquivos. pkgdef devem ser instalados em um dos seguintes locais:%localappdata%\Microsoft\Visual Studio\14.0\Extensions\ ou%vsinstalldir%\Common7\IDE\Extensions \\ . Se a pasta de instalação for%localappdata%\Microsoft\Visual Studio\14.0\Extensions \\ , a extensão será reconhecida pelo Visual Studio, mas será desabilitada por padrão. O usuário pode habilitar a extensão usando **extensões e atualizações**. Se a pasta de instalação for%vsinstalldir%\Common7\IDE\Extensions \\ , a extensão será habilitada por padrão.  
  
> [!NOTE]
> A ferramenta **extensões e atualizações** não pode ser usada para acessar uma extensão, a menos que ela seja instalada como parte de um pacote VSIX.  
  
## <a name="see-also"></a>Consulte Também  
 [Utilitário CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
