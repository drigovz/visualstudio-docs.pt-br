---
title: Set Current Process | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c362d3f5dda5015e91ac88dd8f0abd60a185ba72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665474"
---
# <a name="set-current-process"></a>Definir processo atual
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Define o processo especificado como o processo ativo no depurador.

## <a name="syntax"></a>Sintaxe

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumentos
 `index` Necessário. O índice do processo.

## <a name="remarks"></a>Comentários
 Você pode se conectar a vários processos quando está depurando, mas somente um processo está ativo no depurador em um determinado momento. Você pode usar o comando `SetCurrentProcess` para definir o processo ativo.

## <a name="example"></a>Exemplo

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Consulte Também
 [Comando de](../../ide/reference/command-window.md) [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) para o [Visual Studio Command alias](../../ide/reference/visual-studio-command-aliases.md)
