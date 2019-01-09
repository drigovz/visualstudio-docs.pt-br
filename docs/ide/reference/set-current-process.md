---
title: Definir processo atual
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c01c399dc76d1b328443edef27edd9a921b1b9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855277"
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