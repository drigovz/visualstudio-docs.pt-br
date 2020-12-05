---
title: Definir processo atual
description: Saiba mais sobre o comando Set Current Process e como ele define o processo especificado como o processo ativo no depurador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b6a5c2f010b60546fe1ece16f66bf437d2dc633
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616572"
---
# <a name="set-current-process"></a>Definir processo atual
Define o processo especificado como o processo ativo no depurador.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumentos
`index`

Obrigatórios. O índice do processo.

## <a name="remarks"></a>Comentários
Você pode se conectar a vários processos quando está depurando, mas somente um processo está ativo no depurador em um determinado momento. Você pode usar o comando `SetCurrentProcess` para definir o processo ativo.

## <a name="example"></a>Exemplo

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
