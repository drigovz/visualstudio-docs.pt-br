---
title: Comando Imprimir
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31f604d6df45cb22d18401b5925867d5ab0e02b8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900880"
---
# <a name="print-command"></a>Comando Imprimir
Avalia uma expressão ou exibe o texto especificado.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.Print text
```

## <a name="arguments"></a>Arguments
 `text`

 Necessário. A expressão a ser avaliada ou o texto a ser exibido.

## <a name="remarks"></a>Comentários
 Você pode usar o ponto de interrogação (?) como um alias para esse comando. Assim, por exemplo, o comando

```cmd
>Debug.Print expA
```

 também podem ser gravado

```cmd
>? expA
```

 As duas versões desse comando retornarão o valor atual da expressão `expA`.

## <a name="example"></a>Exemplo

```cmd
>Debug.Print varA
```

## <a name="see-also"></a>Consulte também

- [Comando Evaluate Statement](../../ide/reference/evaluate-statement-command.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)