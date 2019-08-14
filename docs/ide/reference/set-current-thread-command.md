---
title: Comando Definir Thread Atual
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ea652f04295871f9437d80555254caecab87a48
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926061"
---
# <a name="set-current-thread-command"></a>Comando Definir Thread Atual
Define o thread especificado como o thread atual.

## <a name="syntax"></a>Sintaxe

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Arguments
`index`

Necessário. Seleciona um thread por seu índice.

## <a name="example"></a>Exemplo

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Veja também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)