---
title: Comando Listar Threads
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b3ad3b30329d574145ce7de839a3e6c164df2d5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919088"
---
# <a name="list-threads-command"></a>Comando Listar Threads
Exibe uma lista dos threads no programa atual.

## <a name="syntax"></a>Sintaxe

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Arguments
`index`

Opcional. Seleciona um thread pelo seu índice para o thread atual.

## <a name="remarks"></a>Comentários
Quando especificado, o argumento `index` marca o thread indicado como o thread atual. Um asterisco (*) é exibido na lista ao lado do thread atual.

## <a name="example"></a>Exemplo

```
>Debug.ListThreads
```

## <a name="see-also"></a>Veja também

- [Comando List Call Stack](../../ide/reference/list-call-stack-command.md)
- [Comando List Disassembly](../../ide/reference/list-disassembly-command.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)