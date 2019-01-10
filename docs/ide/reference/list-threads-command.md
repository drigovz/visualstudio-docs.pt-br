---
title: Comando Listar Threads
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1a914ffcd242626b0f519ab541c4c381a4597da
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846133"
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