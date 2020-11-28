---
title: Comando Listar Threads
description: Saiba mais sobre o comando listar threads e como ele exibe uma lista dos threads no programa atual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf7b3ed8b28a43c31efe68c6512f08883cb4187a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305262"
---
# <a name="list-threads-command"></a>Comando Listar Threads
Exibe uma lista dos threads no programa atual.

## <a name="syntax"></a>Sintaxe

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumentos
`index`

Opcional. Seleciona um thread pelo seu índice para o thread atual.

## <a name="remarks"></a>Comentários
Quando especificado, o argumento `index` marca o thread indicado como o thread atual. Um asterisco (*) é exibido na lista ao lado do thread atual.

## <a name="example"></a>Exemplo

```
>Debug.ListThreads
```

## <a name="see-also"></a>Confira também

- [Comando listar pilha de chamadas](../../ide/reference/list-call-stack-command.md)
- [Comando listar desmontagem](../../ide/reference/list-disassembly-command.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
