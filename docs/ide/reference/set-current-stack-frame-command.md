---
title: Comando Definir Quadro de Pilha Atual
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a4fa39ad3ce07792819544738185164fef8c985
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844519"
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