---
title: Comando Set Radix | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 050cbe6e639f4177694d9af3ecbc0b768065b7d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665415"
---
# <a name="set-radix-command"></a>Comando Definir Base
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Define ou retorna a base numérica usada para exibir valores inteiros.

## <a name="syntax"></a>Sintaxe

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Arguments
 `10` ou `16` ou `hex` ou `dec` opcional. Indica o decimal (10 ou dez) ou hexadecimal (16 ou hexa). Se um argumento for omitido, o valor base atual será retornado.

## <a name="example"></a>Exemplo
 Este exemplo define o ambiente para exibir valores inteiros em formato hexadecimal.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>Veja também
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [janela](../../ide/reference/command-window.md) de comando [Localizar/comando caixa](../../ide/find-command-box.md) de comandos do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
