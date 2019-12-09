---
title: Comando List Disassembly | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ff5e620d4c53889afe17274364d6f92936025d3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672734"
---
# <a name="list-disassembly-command"></a>Comando Listar Desmontagem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Inicia o processo de depuração e permite que você especifique como os erros são tratados.

## <a name="syntax"></a>Sintaxe

```
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Opções
 Cada opção pode ser invocada usando sua forma completa ou abreviada.

 /Count: `number` [ou]/c: `number` [ou]/length: `number` [ou]/l: `number` opcional. Número de instruções a serem exibidas. O valor padrão é 8.

 /EndAddress: `expression` [ou]/e: `expression` opcional. Endereço no qual interromper a desmontagem.

 /codebytes: `yes`&#124; `no` [ou]/bytes: `yes`&#124; `no` [ou]/B: `yes`&#124; `no` opcional. Indica se deve você deseja exibir bytes de código. O valor padrão é `no`.

 /Source: `yes`&#124; `no` [ou]/s: `yes`&#124; `no` opcional. Indica se deve você deseja exibir o código-fonte. O valor padrão é `no`.

 /symbolnames: `yes`&#124; `no` [ou]/names: `yes`&#124; `no` [ou]/N: `yes`&#124; `no` opcional. Indica se deve você deseja exibir os nomes de símbolos. O valor padrão é `yes`.

 [/linenumbers: `yes`&#124; `no`] Adicional. Habilita a exibição de números de linha associados ao código-fonte. A opção /source deve ter um valor de `yes` para usar a opção /linenumbers.

## <a name="example"></a>Exemplo

```
>Debug.ListDisassembly
```

## <a name="see-also"></a>Veja também
 [Lista](../../ide/reference/list-call-stack-command.md) [de comandos da](../../ide/reference/list-threads-command.md) pilha de chamadas de chamada de linha de comando do [Visual Studio comandos](../../ide/reference/visual-studio-commands.md) [da janela](../../ide/reference/command-window.md) de comando [Localizar/comandos caixa de comando](../../ide/find-command-box.md) do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
