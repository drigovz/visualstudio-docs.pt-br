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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709161"
---
# <a name="createpkgdef-utility"></a>Utilitário CreatePkgDef
Pega um arquivo .dll para uma extensão do Visual Studio como parâmetro e cria um arquivo *.pkgdef* para acompanhar o arquivo *.dll.* O arquivo *.pkgdef* contém todas as informações que de outra forma seriam escritas no registro do sistema quando a extensão for instalada.

> [!NOTE]
> A maioria dos modelos de projeto que estão incluídos no Visual Studio SDK criam automaticamente arquivos *.pkgdef* como parte do processo de compilação. Este documento destina-se àqueles que desejam criar pacotes manualmente ou converter pacotes existentes para usar a implantação *.pkgdef.*

## <a name="syntax"></a>Sintaxe

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumentos
**/out=&lt;FileName&gt;**\
Obrigatórios. Define o nome do arquivo de saída &lt; *.pkgdef* como FileName&gt;.

**/codebase**\
Opcional. Força o registro com o utilitário **CodeBase.**

**/montagem**\
Força o registro junto à concessionária **da Assembléia.**

**&lt;Assemblypath&gt;**\
O caminho do arquivo *.dll* a partir do qual você deseja gerar o *.pkgdef*.

## <a name="remarks"></a>Comentários
A implantação de extensão usando arquivos *.pkgdef* substitui os requisitos de registro de versões anteriores do Visual Studio.

::: moniker range=">=vs-2019"

Os arquivos *.pkgdef* devem ser instalados em um dos seguintes locais:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensões\\*

- *%vsinstalldir%\Common7\IDE\Extensões\\*

Se a pasta de instalação for *%localappdata%\Microsoft\Visual Studio\16.0\Extensões,\\*a extensão será reconhecida pelo Visual Studio, mas será desativada por padrão. O usuário pode habilitar a extensão usando **O Manage Extensions**.

Se a pasta de instalação for *%vsinstalldir%\Common7\IDE\Extensões,\\*a extensão será ativada por padrão.

> [!NOTE]
> A **ferramenta Gerenciar extensões** não pode ser usada para acessar uma extensão, a menos que seja instalada como parte de um pacote VSIX.

::: moniker-end

::: moniker range="vs-2017"

Os arquivos *.pkgdef* devem ser instalados em um dos seguintes locais:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensões\\*

- *%vsinstalldir%\Common7\IDE\Extensões\\*

Se a pasta de instalação for *%localappdata%\Microsoft\Visual Studio\15.0\Extensões,\\*a extensão será reconhecida pelo Visual Studio, mas será desativada por padrão. O usuário pode habilitar a extensão usando **Extensões e Atualizações**.

Se a pasta de instalação for *%vsinstalldir%\Common7\IDE\Extensões,\\*a extensão será ativada por padrão.

> [!NOTE]
> A ferramenta **Extensões e Atualizações** não pode ser usada para acessar uma extensão a menos que seja instalada como parte de um pacote VSIX.

::: moniker-end

## <a name="see-also"></a>Confira também
- [Utilitário CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
