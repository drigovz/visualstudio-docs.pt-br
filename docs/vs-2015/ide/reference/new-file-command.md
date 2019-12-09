---
title: Comando Novo Arquivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8e0d25d585f518c854ad6176ae4ae7a5f27b22ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671959"
---
# <a name="new-file-command"></a>Comando Novo Arquivo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cria um novo arquivo e abre-o. O arquivo aparece na pasta Arquivos Diversos.

## <a name="syntax"></a>Sintaxe

```
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Arguments
 `filename` Opcional. Nome para o arquivo. Se nenhum nome for fornecido, será fornecido um nome padrão. Se nenhum nome de modelo for listado, será criado um arquivo de texto.

## <a name="switches"></a>Opções
 /t: `templatename` opcional. Especifica o tipo de arquivo a ser criado.

 A sintaxe do argumento /t:`templatename` espelha as informações encontradas na Caixa de Diálogo Novo Arquivo. Insira o nome da categoria seguido por uma barra invertida (`\`) e o nome do modelo e coloque toda a cadeia de caracteres entre aspas.

 Por exemplo, para criar um novo arquivo de origem [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], você inseriria o seguinte para o argumento /t:`templatename`.

```
/t:"Visual C++\C++ File (.cpp)"
```

 O exemplo acima indica que o modelo de Arquivo C++ está localizado na categoria no Visual C++ na caixa de diálogo **Novo Arquivo**.

 /e:`editorname` opcional. Nome do editor no qual o arquivo será aberto. Se o argumento for especificado, mas nenhum nome de editor for fornecido, a caixa de diálogo **Abrir com** será exibida.

 A sintaxe do argumento /e:`editorname` usa os nomes de editor como eles são exibidos na Caixa de Diálogo Abrir com, entre aspas.

 Por exemplo, para abrir um arquivo no editor de código-fonte, insira o seguinte para o argumento /e:`editorname`.

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Exemplo
 Este exemplo cria uma nova página da Web "test1.htm" e abre-a no editor de código-fonte.

```
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Veja também
 Janela de [comando](../../ide/reference/command-window.md) de [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) janela de pesquisa [imediata](../../ide/reference/immediate-window.md) [/comando](../../ide/find-command-box.md) do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
