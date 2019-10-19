---
title: Comando Listar Origem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f13689b6e3ac4db2d58c1def3a5d0dd05c219f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672329"
---
# <a name="list-source-command"></a>Comando Listar Origem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exibe as linhas de código-fonte especificadas.

## <a name="syntax"></a>Sintaxe

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Opções
 /Count: `number` opcional. Especifica o número de linhas que serão mostradas.

 /Current opcional. Mostra a linha atual.

 /File: `filename` opcional. Caminho do arquivo a ser exibido. Se nenhum nome de arquivo for especificado, o comando mostrará o código-fonte da linha da instrução atual.

 /Line: `number` opcional. Mostra um número de linha específico.

 /ShowLineNumbers: `yes|no` opcional. Especifica se os números de linha devem ser exibidos.

## <a name="remarks"></a>Comentários

## <a name="example"></a>Exemplo
 Este exemplo lista o código-fonte da linha 4 do arquivo Form1.vb, com números de linha visíveis.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Veja também
 [Janela de comando](../../ide/reference/command-window.md) de [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
