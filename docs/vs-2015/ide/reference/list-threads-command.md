---
title: Comando Listar Threads | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc11479901785b19235e0962d3ae90e552e5b33b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671134"
---
# <a name="list-threads-command"></a>Comando Listar Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exibe uma lista dos threads no programa atual.

## <a name="syntax"></a>Sintaxe

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumentos
 `index` Opcional. Seleciona um thread pelo seu índice para o thread atual.

## <a name="remarks"></a>Comentários
 Quando especificado, o argumento `index` marca o thread indicado como o thread atual. Um asterisco (*) é exibido na lista ao lado do thread atual.

## <a name="example"></a>Exemplo

```
>Debug.ListThreads
```

## <a name="see-also"></a>Consulte Também
 [Lista](../../ide/reference/list-call-stack-command.md) de comandos da pilha de chamadas lista de [desmontagem comando](../../ide/reference/list-disassembly-command.md) [do Visual Studio comandos](../../ide/reference/visual-studio-commands.md) da [janela](../../ide/reference/command-window.md) de comando [Localizar/comandos caixa de comando](../../ide/find-command-box.md) do [Visual Studio alias do comando](../../ide/reference/visual-studio-command-aliases.md)
