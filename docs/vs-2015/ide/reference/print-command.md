---
title: Comando Print | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662154"
---
# <a name="print-command"></a>Comando Imprimir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avalia uma expressão ou exibe o texto especificado.

## <a name="syntax"></a>Sintaxe

```
Debug.Print text
```

## <a name="arguments"></a>Argumentos
 `text` Necessário. A expressão a ser avaliada ou o texto a ser exibido.

## <a name="remarks"></a>Comentários
 Você pode usar o ponto de interrogação (?) como um alias para esse comando. Assim, por exemplo, o comando

```
>Debug.Print expA
```

 também podem ser gravado

```
>? expA
```

 As duas versões desse comando retornarão o valor atual da expressão `expA`.

## <a name="example"></a>Exemplo

```
>Debug.Print varA
```

## <a name="see-also"></a>Consulte Também
 [Comando avaliar instrução](../../ide/reference/evaluate-statement-command.md) [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [janela de comando](../../ide/reference/command-window.md) [Localizar/comandos caixa](../../ide/find-command-box.md) de comando [Visual Studio aliases de comando](../../ide/reference/visual-studio-command-aliases.md)
