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
ms.openlocfilehash: 84f5e7db4b31607c05da32a09e5d691a85ef4173
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614827"
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
**/out=&lt;FileName&gt;**\
Necessário. Define o nome da *pkgdef* arquivo de saída &lt;FileName&gt;.

**/codebase**\
Opcional. Força o registro com o **CodeBase** utilitário.

**/assembly**\
Força o registro com o **Assembly** utilitário.

**&lt;AssemblyPath&gt;**\
O caminho da *. dll* arquivo do qual você deseja gerar o *pkgdef*.

## <a name="remarks"></a>Comentários
Implantação de extensão usando *pkgdef* arquivos substitui os requisitos de registro de versões anteriores do Visual Studio.

::: moniker range=">=vs-2019"

O *pkgdef* arquivos devem ser instalados em um dos seguintes locais:

- *%LocalAppData%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Se a pasta de instalação estiver *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*, a extensão é reconhecida pelo Visual Studio, mas é desabilitada por padrão. O usuário pode habilitar a extensão usando **gerenciar extensões**.

Se a pasta de instalação estiver *%vsinstalldir%\Common7\IDE\Extensions\\*, a extensão está habilitada por padrão.

> [!NOTE]
> O **gerenciar extensões** ferramenta não pode ser usada para acessar uma extensão, a menos que ele é instalado como parte de um pacote VSIX.

::: moniker-end

::: moniker range="vs-2017"

O *pkgdef* arquivos devem ser instalados em um dos seguintes locais:

- *%LocalAppData%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Se a pasta de instalação estiver *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*, a extensão é reconhecida pelo Visual Studio, mas é desabilitada por padrão. O usuário pode habilitar a extensão usando **extensões e atualizações**.

Se a pasta de instalação estiver *%vsinstalldir%\Common7\IDE\Extensions\\*, a extensão está habilitada por padrão.

> [!NOTE]
> O **extensões e atualizações** ferramenta não pode ser usada para acessar uma extensão, a menos que ele é instalado como parte de um pacote VSIX.

::: moniker-end

## <a name="see-also"></a>Consulte também
- [Utilitário CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
