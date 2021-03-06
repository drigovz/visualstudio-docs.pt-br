---
title: Comando Listar Origem
description: Saiba mais sobre o comando de origem da lista e como ele exibe as linhas especificadas do código-fonte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4efd5ab0ddd94b17fa6a683366707d635f844bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919439"
---
# <a name="list-source-command"></a>Comando Listar Origem
Exibe as linhas de código-fonte especificadas.

## <a name="syntax"></a>Sintaxe

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Comutadores
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

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)