---
title: Comando Avaliar Instrução | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657705"
---
# <a name="evaluate-statement-command"></a>Comando Avaliar Instrução
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avalia e exibe a instrução fornecida.

## <a name="syntax"></a>Sintaxe

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argumentos
 `text` Necessário. A instrução a ser avaliada.

## <a name="remarks"></a>Comentários
 A janela usada para inserir o comando **EvaluateStatement** determina se um sinal de igual (=) é interpretado como um operador de comparação ou um operador de atribuição.

 Na janela **Comando**, um sinal de igual (=) é interpretado como um operador de comparação. Dessa forma, por exemplo, se os valores das variáveis `a` e `b` forem diferentes, o comando

```
>Debug.EvaluateStatement(a=b)
```

 retornará um valor de `false`.

 Na janela **Imediato**, por outro lado, um sinal de igual (=) é interpretado como um operador de atribuição. Assim, por exemplo, o comando

```
>Debug.EvaluateStatement(a=b)
```

 atribuirá à variável `a` o valor da variável `b`.

## <a name="example"></a>Exemplo

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Consulte Também
 [Comando de impressão](../../ide/reference/print-command.md) [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [janela](../../ide/reference/command-window.md) de comando [Localizar/comando](../../ide/find-command-box.md) do [Visual Studio aliases de comando](../../ide/reference/visual-studio-command-aliases.md)
