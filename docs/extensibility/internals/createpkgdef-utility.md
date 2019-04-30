---
title: Utilitário CreatePkgDef | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19372b341a0a8ba49caa0208a9a2fbbfd0a6b29b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418707"
---
# <a name="createpkgdef-utility"></a>Utilitário CreatePkgDef
Usa um arquivo. dll para uma extensão do Visual Studio como um parâmetro e cria um *pkgdef* arquivo para acompanhar as *. dll* arquivo. O *pkgdef* arquivo contém todas as informações que, caso contrário, seriam gravadas no registro do sistema quando a extensão está instalada.

> [!NOTE]
> A maioria dos modelos de projeto que estão incluídos no SDK do Visual Studio automaticamente cria *pkgdef* arquivos como parte do processo de compilação. Este documento destina-se para aqueles que desejam criar pacotes manualmente ou converter pacotes existentes para usar *pkgdef* implantação.

## <a name="syntax"></a>Sintaxe

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Arguments
 **/out=&lt;FileName&gt;** Required. Define o nome da *pkgdef* arquivo de saída &lt;FileName&gt;.

 **/codebase** opcional. Força o registro com o **CodeBase** utilitário.

 **/assembly** força o registro com o **Assembly** utilitário.

 **&lt;AssemblyPath&gt;**  o caminho da *. dll* arquivo do qual você deseja gerar o *pkgdef*.

## <a name="remarks"></a>Comentários
 Implantação de extensão usando *pkgdef* arquivos substitui os requisitos de registro de versões anteriores do Visual Studio.

 O *pkgdef* arquivos devem ser instalados em um dos seguintes locais:

- *%LocalAppData%\Microsoft\Visual Studio\14.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

  Se a pasta de instalação estiver *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*, a extensão será reconhecida pelo Visual Studio, mas será desabilitada por padrão. O usuário pode habilitar a extensão usando **extensões e atualizações**.

  Se a pasta de instalação estiver *%vsinstalldir%\Common7\IDE\Extensions\\*, a extensão está habilitada por padrão.

> [!NOTE]
> O **extensões e atualizações** ferramenta não pode ser usada para acessar uma extensão, a menos que ele é instalado como parte de um pacote VSIX.

## <a name="see-also"></a>Consulte também
- [Utilitário CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)