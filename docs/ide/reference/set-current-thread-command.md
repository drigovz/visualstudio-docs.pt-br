---
title: Comando Definir Thread Atual
description: Saiba mais sobre o comando Set Current thread e como ele define o thread especificado como o thread atual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2cb58bf8751eb4299ecede18bac83770c3a7df96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957732"
---
# <a name="set-current-thread-command"></a>Comando Definir Thread Atual
Define o thread especificado como o thread atual.

## <a name="syntax"></a>Sintaxe

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Argumentos
`index`

Obrigatório. Seleciona um thread por seu índice.

## <a name="example"></a>Exemplo

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)