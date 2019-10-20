---
title: Comando Listar Memória
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb5e6181c2dbe9a79b2ab1d0859722de324d768e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610690"
---
# <a name="list-memory-command"></a>Comando Listar Memória
Exibe o conteúdo do intervalo de memória especificado.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Arguments
`expression`

Opcional. O endereço de memória do qual começar a exibir a memória.

## <a name="switches"></a>Opções
/ANSI&#124;Unicode

Opcional. Exibe a memória como caracteres correspondentes aos bytes de memória, ANSI ou Unicode.

/Count:`number`

Opcional. Determina quantos bytes de memória devem ser exibidos, começando em `expression`.

/Format:`formattype`

Opcional. Tipo de formato para exibir informações de memória na janela **Memória**; pode ser OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bits) ou Double (64 bits). Se OneByte for usado, `/Unicode` ficará não disponível.

/Hex&#124;Signed&#124;Unsigned

Opcional. Especifica o formato para exibir números: com sinal, sem sinal ou hexadecimal.

## <a name="remarks"></a>Comentários
Em vez de escrever um comando **Debug.ListMemory** completo com todas as opções, você pode invocar o comando usando aliases predefinidos com determinadas opções predefinidas como valores especificados. Por exemplo, em vez de inserir:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

você pode escrever:

```cmd
>df /Count:30 /Unicode
```

Veja uma lista dos aliases disponíveis para o comando **Debug.ListMemory**:

|Alias|Comando e opções|
|-----------| - |
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**db**|Debug.ListMemory /Format:OneByte|
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**dd**|Debug.ListMemory /Format:FourBytes|
|**df**|Debug.ListMemory /Format:Float|
|**dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Exemplo

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Consulte também

- [Comando List Call Stack](../../ide/reference/list-call-stack-command.md)
- [Comando List Threads](../../ide/reference/list-threads-command.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)