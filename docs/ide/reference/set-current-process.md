---
title: Definir processo atual
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d8c313eebc8623156dd7a575060397ee6e16a9d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748643"
---
# <a name="set-current-process"></a>Definir processo atual
Define o processo especificado como o processo ativo no depurador.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Arguments
`index`

Necessário. O índice do processo.

## <a name="remarks"></a>Comentários
Você pode se conectar a vários processos quando está depurando, mas somente um processo está ativo no depurador em um determinado momento. Você pode usar o comando `SetCurrentProcess` para definir o processo ativo.

## <a name="example"></a>Exemplo

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)