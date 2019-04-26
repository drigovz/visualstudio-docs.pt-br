---
title: Comando Definir Quadro de Pilha Atual
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9eea69dc4d2931f66d4c6769667e23bdfb4eecf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934523"
---
# <a name="set-current-stack-frame-command"></a>Comando Definir Quadro de Pilha Atual
Permite definir um registro de ativação específico.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Arguments
 `index`

 Necessário. Seleciona um registro de ativação pelo seu índice.

## <a name="example"></a>Exemplo

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)