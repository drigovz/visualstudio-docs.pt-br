---
title: Comando Novo Arquivo
description: Saiba mais sobre o comando novo arquivo e como ele cria um novo arquivo e o abre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c800ce0ed130ed78f9537584c95a29a717f405fa
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304097"
---
# <a name="new-file-command"></a>Comando Novo Arquivo
Cria um novo arquivo e abre-o. O arquivo aparece na pasta Arquivos Diversos.

## <a name="syntax"></a>Sintaxe

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argumentos
`filename`

Opcional. Nome para o arquivo. Se nenhum nome for fornecido, será fornecido um nome padrão. Se nenhum nome de modelo for listado, será criado um arquivo de texto.

## <a name="switches"></a>Comutadores
/t:`templatename`\
Opcional. Especifica o tipo de arquivo a ser criado.

A sintaxe do argumento /t:`templatename` espelha as informações encontradas na Caixa de Diálogo Novo Arquivo. Insira o nome da categoria seguido por uma barra invertida (`\`) e o nome do modelo e coloque toda a cadeia de caracteres entre aspas.

Por exemplo, para criar um novo arquivo de origem [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], você inseriria o seguinte para o argumento /t:`templatename`.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

O exemplo acima indica que o modelo de Arquivo C++ está localizado na categoria no Visual C++ na caixa de diálogo **Novo Arquivo**.

/e:`editorname`\
Opcional. Nome do editor no qual o arquivo será aberto. Se o argumento for especificado, mas nenhum nome de editor for fornecido, a caixa de diálogo **Abrir com** será exibida.

A sintaxe do argumento /e:`editorname` usa os nomes de editor como eles são exibidos na Caixa de Diálogo Abrir com, entre aspas.

Por exemplo, para abrir um arquivo no editor de código-fonte, insira o seguinte para o argumento /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Exemplo
Este exemplo cria uma nova página da Web "test1.htm" e abre-a no editor de código-fonte.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Janela imediata](../../ide/reference/immediate-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
