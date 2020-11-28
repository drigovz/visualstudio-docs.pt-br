---
title: comando Ir para
description: Saiba mais sobre o comando go to e como ele move o cursor para a linha especificada.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b0ef161cb8108ed3244c263ee51fee4251fc05d8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305204"
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
