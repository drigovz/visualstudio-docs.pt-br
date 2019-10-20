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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c437b91fea5e3087de8b22cb72a2f20ad421bead
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610479"
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

## <a name="see-also"></a>Consulte também

- [Comando List Call Stack](../../ide/reference/list-call-stack-command.md)
- [Comando List Disassembly](../../ide/reference/list-disassembly-command.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)