---
title: Comando Ir para | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 454b51b6939a78cdaab8d29f51d30910024adbe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661211"
---
# <a name="go-to-command"></a>comando Ir para
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Move o cursor para a linha especificada.

## <a name="syntax"></a>Sintaxe

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumentos
 `linenumber` Opcional. Um inteiro que representa o número da linha para a qual ir.

## <a name="remarks"></a>Comentários
 A numeração de linha começa em um. Se o valor de `linenumber` for menor que um, a primeira linha será exibida. Se o valor de `linenumber` for maior que o número da última linha, a última linha será exibida.

 Se um valor para `linenumber` não for especificado, a caixa de diálogo **Ir para a Linha** será exibida.

 O alias para esse comando é GoToLn.

## <a name="example"></a>Exemplo

```
>Edit.GoTo 125
```

## <a name="see-also"></a>Consulte Também
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [janela](../../ide/reference/command-window.md) de comando [Localizar/comando caixa](../../ide/find-command-box.md) de comandos do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
