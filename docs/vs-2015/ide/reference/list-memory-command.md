---
title: Comando Listar Memória | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2630402e03d1256f63e542818a9066745206d2c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672758"
---
# <a name="list-memory-command"></a>Comando Listar Memória
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exibe o conteúdo do intervalo de memória especificado.

## <a name="syntax"></a>Sintaxe

```
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Arguments
 `expression` Opcional. O endereço de memória do qual começar a exibir a memória.

## <a name="switches"></a>Opções
 /ANSI&#124;Unicode opcional. Exibe a memória como caracteres correspondentes aos bytes de memória, ANSI ou Unicode.

 /Count: `number` opcional. Determina quantos bytes de memória devem ser exibidos, começando em `expression`.

 /Format: `formattype` opcional. Tipo de formato para exibir informações de memória na janela **Memória**; pode ser OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bits) ou Double (64 bits). Se OneByte for usado, `/Unicode` ficará não disponível.

 /Hex&#124;assinado&#124;sem sinal opcional. Especifica o formato para exibir números: com sinal, sem sinal ou hexadecimal.

## <a name="remarks"></a>Comentários
 Em vez de escrever um comando **Debug.ListMemory** completo com todas as opções, você pode invocar o comando usando aliases predefinidos com determinadas opções predefinidas como valores especificados. Por exemplo, em vez de inserir:

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 você pode escrever:

```
>df /Count:30 /Unicode
```

 Veja uma lista dos aliases disponíveis para o comando **Debug.ListMemory**:

|Alias|Comando e opções|
|-----------|--------------------------|
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**db**|Debug.ListMemory /Format:OneByte|
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**dd**|Debug.ListMemory /Format:FourBytes|
|**df**|Debug.ListMemory /Format:Float|
|**dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Exemplo

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Veja também
 [Lista](../../ide/reference/list-call-stack-command.md) [de comandos da](../../ide/reference/list-threads-command.md) pilha de chamadas de chamada de linha de comando do [Visual Studio comandos](../../ide/reference/visual-studio-commands.md) [da janela](../../ide/reference/command-window.md) de comando [Localizar/comandos caixa de comando](../../ide/find-command-box.md) do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
