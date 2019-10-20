---
title: Comando Inspeção Rápida
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d78371b638b9a584ba27a1ed035cf188c3e66e0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655652"
---
# <a name="quick-watch-command"></a>Comando Inspeção Rápida
Exibe o texto selecionado ou especificado no campo Expressão da janela [QuickWatch](../../debugger/watch-and-quickwatch-windows.md). Você pode usar essa caixa de diálogo para calcular o valor atual de uma variável ou expressão reconhecida pelo depurador ou o conteúdo de um registro. Além disso, você pode alterar o valor de qualquer variável não const ou o conteúdo de qualquer registro.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Arguments

`text`\
Opcional. O texto a ser adicionado à caixa de diálogo **Inspeção Rápida**.

## <a name="remarks"></a>Comentários

Se `text` for omitido, o texto selecionado atualmente ou a palavra no cursor é adicionada à janela Inspeção.

## <a name="example"></a>Exemplo

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Consulte também

- [Definir uma inspeção nas variáveis usando as janelas Inspeção e QuickWatch no Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)