---
title: Comando Listar Registros
description: Saiba mais sobre o comando listar registros e como ele exibe o valor dos registros selecionados e permite que você modifique a lista de registros a serem mostrados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0168f8e4b6c04ea0d6b675ce6c280bd8140971b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919562"
---
# <a name="list-registers-command"></a>Comando Listar Registros
Exibe o valor dos registros selecionados e permite modificar a lista de registros a mostrar.

## <a name="syntax"></a>Sintaxe

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Comutadores
/Display [{`register`&#124;`registerGroup`}...]

Exibe os valores do `register` ou `registerGroup` especificado. Se nenhum `register` ou `registerGroup` for especificado, a lista padrão de registros será exibida. Se nenhuma opção for especificada, o comportamento será o mesmo. Por exemplo:

`Debug.ListRegisters /Display eax`

é equivalente a

`Debug.ListRegisters eax`

/List

Exibe todos os grupos de registros na lista.

/Watch [{`register`&#124;`registerGroup`}...]

Adiciona um ou mais valores `register` ou `registerGroup` à lista.

/Unwatch [{`register`&#124;`registerGroup`}...]

Remove um ou mais valores `register` ou `registerGroup` da lista.

## <a name="remarks"></a>Comentários
O alias `r` pode ser usado no lugar de `Debug.ListRegisters`.

## <a name="example"></a>Exemplo
Este exemplo usa o alias `Debug.ListRegisters``r` para exibir os valores do registro de grupo `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Noções básicas sobre depuração: janela Registros](../../debugger/debugging-basics-registers-window.md)
- [Como usar a janela Registros](../../debugger/how-to-use-the-registers-window.md)
