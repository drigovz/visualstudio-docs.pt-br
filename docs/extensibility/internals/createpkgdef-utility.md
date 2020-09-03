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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709161"
---
# <a name="createpkgdef-utility"></a>Utilitário CreatePkgDef
Usa um arquivo. dll para uma extensão do Visual Studio como um parâmetro e cria um arquivo *. pkgdef* para acompanhar o arquivo *. dll* . O arquivo *. pkgdef* contém todas as informações que, de outra forma, seriam gravadas no registro do sistema quando a extensão é instalada.

> [!NOTE]
> A maioria dos modelos de projeto incluídos no SDK do Visual Studio criam automaticamente arquivos *. pkgdef* como parte do processo de compilação. Este documento destina-se a aqueles que desejam criar pacotes manualmente ou converter pacotes existentes para usar a implantação do *. pkgdef*  .

## <a name="syntax"></a>Sintaxe

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumentos
**/out = &lt; nome do arquivo&gt;**\
Obrigatórios. Define o nome do arquivo de saída *. pkgdef* para &lt; filename &gt; .

**/codebase**\
Opcional. Força o registro com o utilitário **codebase** .

**/assembly**\
Força o registro com o utilitário **assembly** .

**&lt;AssemblyPath&gt;**\
O caminho do arquivo *. dll* do qual você deseja gerar o *. pkgdef*.

## <a name="remarks"></a>Comentários
A implantação de extensão usando arquivos *. pkgdef* substitui os requisitos de registro de versões anteriores do Visual Studio.

::: moniker range=">=vs-2019"

Os arquivos *. pkgdef* devem ser instalados em um dos seguintes locais:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Se a pasta de instalação for *%LocalAppData%\Microsoft\Visual \\ Studio\16.0\Extensions*, a extensão será reconhecida pelo Visual Studio, mas será desabilitada por padrão. O usuário pode habilitar a extensão usando **gerenciar extensões**.

Se a pasta de instalação *for \\ %VSINSTALLDIR%\Common7\IDE\Extensions*, a extensão será habilitada por padrão.

> [!NOTE]
> A ferramenta **gerenciar extensões** não pode ser usada para acessar uma extensão, a menos que ela seja instalada como parte de um pacote VSIX.

::: moniker-end

::: moniker range="vs-2017"

Os arquivos *. pkgdef* devem ser instalados em um dos seguintes locais:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Se a pasta de instalação for *%LocalAppData%\Microsoft\Visual \\ Studio\15.0\Extensions*, a extensão será reconhecida pelo Visual Studio, mas será desabilitada por padrão. O usuário pode habilitar a extensão usando **extensões e atualizações**.

Se a pasta de instalação *for \\ %VSINSTALLDIR%\Common7\IDE\Extensions*, a extensão será habilitada por padrão.

> [!NOTE]
> A ferramenta **extensões e atualizações** não pode ser usada para acessar uma extensão, a menos que ela seja instalada como parte de um pacote VSIX.

::: moniker-end

## <a name="see-also"></a>Confira também
- [Utilitário CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
