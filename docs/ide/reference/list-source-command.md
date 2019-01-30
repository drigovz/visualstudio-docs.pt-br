---
title: Comando Listar Origem
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5348bd2533a10d98732911a6b7af5410e8ffe42
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031624"
---
# <a name="list-source-command"></a>Comando Listar Origem
Exibe as linhas de código-fonte especificadas.

## <a name="syntax"></a>Sintaxe

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Opções
 /Count:`number`

 Opcional. Especifica o número de linhas que serão mostradas.

 /Current

 Opcional. Mostra a linha atual.

 /File:`filename`

 Opcional. Caminho do arquivo a ser exibido. Se nenhum nome de arquivo for especificado, o comando mostrará o código-fonte da linha da instrução atual.

 /Line:`number`

 Opcional. Mostra um número de linha específico.

 /ShowLineNumbers:`yes|no`

 Opcional. Especifica se os números de linha devem ser exibidos.

## <a name="example"></a>Exemplo
 Este exemplo lista o código-fonte da linha 4 do arquivo Form1.vb, com números de linha visíveis.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)