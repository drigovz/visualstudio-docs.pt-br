---
title: Comando Abrir Arquivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c8dcf35e4c045db0d9acd45e2eb307a31ba39f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671930"
---
# <a name="open-file-command"></a>Comando Abrir Arquivo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre um arquivo existente e permite que você especifique um editor.

## <a name="syntax"></a>Sintaxe

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Arguments
 `filename` Necessário. O caminho total ou parcial e o nome do arquivo a abrir. Caminhos que contêm espaços devem ser colocados entre aspas.

## <a name="switches"></a>Opções
 /e:`editorname` opcional. Nome do editor no qual o arquivo será aberto. Se o argumento for especificado, mas nenhum nome de editor for fornecido, a caixa de diálogo **Abrir com** será exibida.

 A sintaxe do argumento /e:`editorname` usa os nomes de editor como eles são exibidos na Caixa de Diálogo Abrir com, entre aspas.

 Por exemplo, para abrir um arquivo no editor de código-fonte, insira o seguinte para o argumento /e:`editorname`.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Comentários
 Conforme você digita um caminho, o preenchimento automático tenta localizar o caminho e o nome do arquivo corretos.

## <a name="example"></a>Exemplo
 Este exemplo abre o arquivo de estilo "Test1.css" no editor de código-fonte.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Veja também
 Janela de [comando](../../ide/reference/command-window.md) de [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) janela de pesquisa [imediata](../../ide/reference/immediate-window.md) [/comando](../../ide/find-command-box.md) do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
