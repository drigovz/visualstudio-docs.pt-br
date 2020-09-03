---
title: Comando Listar Registros | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3476244d3044eb80dbfce3559479421b012cc5fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659505"
---
# <a name="list-registers-command"></a>Comando Listar Registros
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exibe o valor dos registros selecionados e permite modificar a lista de registros a mostrar.

## <a name="syntax"></a>Sintaxe

```
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Comutadores
 /Display [{ `register`&#124;`registerGroup` }...] Exibe os valores do especificado `register` ou `registerGroup` . Se nenhum `register` ou `registerGroup` for especificado, a lista padrão de registros será exibida. Se nenhuma opção for especificada, o comportamento será o mesmo. Por exemplo:

 `Debug.ListRegisters /Display eax`

 é equivalente a

 `Debug.ListRegisters eax`

 /List exibe todos os grupos de registros na lista.

 /Watch [{ `register`&#124;`registerGroup` }...] Adiciona um ou mais `register` `registerGroup` valores ou à lista.

 /Unwatch [{ `register`&#124;`registerGroup` }...] Remove um ou mais `register` `registerGroup` valores da lista.

## <a name="remarks"></a>Comentários
 O alias `r` pode ser usado no lugar de `Debug.ListRegisters`.

## <a name="example"></a>Exemplo
 Este exemplo usa o alias `Debug.ListRegisters``r` para exibir os valores do registro de grupo `Flags`.

```
r /Display Flags
```

## <a name="see-also"></a>Consulte Também
 Conceitos básicos de depuração de [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [: janela de registros](../../debugger/debugging-basics-registers-window.md) [como: usar a janela de registros](../../debugger/how-to-use-the-registers-window.md)
