---
title: Comando Listar Módulos
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86e479879051d38df1da3ed2677303a76ea2d289
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747906"
---
# <a name="list-modules-command"></a>Comando Listar Módulos
Lista os módulos do processo atual.

## <a name="syntax"></a>Sintaxe

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parâmetros
/Address:`yes|no`

Opcional. Especifica se os endereços de memória dos módulos devem ser exibidos. O valor padrão é `yes`.

/Name:`yes|no`

Opcional. Especifica se os nomes dos módulos devem ser exibidos. O valor padrão é `yes`.

/Order:`yes|no`

Opcional. Especifica se a ordem dos módulos deve ser exibida. O valor padrão é `no`.

/Path:`yes|no`

Opcional. Especifica se os caminhos dos módulos devem ser exibidos. O valor padrão é `yes`.

/Process:`yes|no`

Opcional. Especifica se os processos dos módulos devem ser exibidos. O valor padrão é `no`.

/SymbolFile:`yes|no`

Opcional. Especifica se os arquivos de símbolo dos módulos devem ser exibidos. O valor padrão é `no`.

/SymbolStatus:`yes|no`

Opcional. Especifica se os status de símbolo dos módulos devem ser exibidos. O valor padrão é `yes`.

/Timestamp:`yes|no`

Opcional. Especifica se os carimbos de data/hora dos módulos devem ser exibidos. O valor padrão é `no`.

/Version:`yes|no`

Opcional. Especifica se as versões dos módulos devem ser exibidas. O valor padrão é `no`.

## <a name="example"></a>Exemplo
Este exemplo lista os nomes, endereços e carimbos de data/hora do módulo para o processo atual.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Como usar a janela Módulos](../../debugger/how-to-use-the-modules-window.md)