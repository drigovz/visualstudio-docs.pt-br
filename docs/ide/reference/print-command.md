---
title: Debug.Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567834"
---
# <a name="print-command"></a>Comando Imprimir

Avalia uma expressão ou exibe o texto especificado.

## <a name="syntax"></a>Sintaxe

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumentos

`text`

Obrigatórios. A expressão a ser avaliada ou o texto a ser exibido.

## <a name="remarks"></a>Comentários

Você pode usar o ponto de interrogação (?) como um alias para esse comando. Assim, por exemplo, o comando

```cmd
>Debug.Print expA
```

também pode ser escrito como

```cmd
? expA
```

As duas versões desse comando retornam o valor atual da expressão `expA`.

## <a name="example"></a>Exemplo

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Confira também

- [Comando Evaluate Statement](../../ide/reference/evaluate-statement-command.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
