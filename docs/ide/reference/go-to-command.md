---
title: comando Ir para
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 535906d8b8d7f8ba0c2984d22ceead18a0d47c2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569199"
---
# <a name="go-to-command"></a>comando Ir para
Move o cursor para a linha especificada.

## <a name="syntax"></a>Sintaxe

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumentos
`linenumber`\
Opcional. Um inteiro que representa o número da linha para a qual ir.

## <a name="remarks"></a>Comentários
A numeração de linha começa em um. Se o valor de `linenumber` for menor que um, a primeira linha será exibida. Se o valor de `linenumber` for maior que o número da última linha, a última linha será exibida.

Se um valor para `linenumber` não for especificado, a caixa de diálogo **Ir para a Linha** será exibida.

O alias para esse comando é GoToLn.

## <a name="example"></a>Exemplo

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
