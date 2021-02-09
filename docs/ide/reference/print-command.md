---
title: Debug.Print
description: Saiba mais sobre o comando Imprimir e como ele avalia uma expressão ou exibe o texto especificado.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08150654a7a4f062555a1d12382b9d51aacca25f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932027"
---
# <a name="print-command"></a>Comando Imprimir

Avalia uma expressão ou exibe o texto especificado.

## <a name="syntax"></a>Sintaxe

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumentos

`text`

Obrigatório. A expressão a ser avaliada ou o texto a ser exibido.

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
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
