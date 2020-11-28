---
title: Comando Listar Módulos
description: Saiba mais sobre o comando list modules e como ele lista os módulos para o processo atual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa0c3f6445a22ee80457e8a7f9f24fb7008f77ed
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305306"
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

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Como usar a janela Módulos](../../debugger/how-to-use-the-modules-window.md)
