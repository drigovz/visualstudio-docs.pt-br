---
title: Comando Adicionar Novo Item
description: Saiba como usar o comando Adicionar novo item para adicionar um novo item de solução ou conjunto de quadros à solução atual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 37742f1a9adda219e359d734b80f44679509ee03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846329"
---
# <a name="add-new-item-command"></a>Comando Adicionar Novo Item
Adiciona um novo item de solução, como um .htm, .css, .txt ou conjunto de quadros à solução atual e a abre.

## <a name="syntax"></a>Sintaxe

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumentos
`filename`\
Opcional. O nome de arquivo e o caminho do item a ser adicionado à solução.

## <a name="switches"></a>Comutadores
/t: `templatename`\
Opcional. Especifica o tipo de arquivo a ser criado. Se nenhum nome de modelo for fornecido, um arquivo de texto será criado por padrão.

A sintaxe do argumento /t:`templatename` espelha as informações encontradas na caixa de diálogo **Adicionar Novo Item de Solução**. É necessário inserir a categoria completa seguida pelo tipo de arquivo, separando o nome da categoria do tipo de arquivo por uma barra invertida (`\`) e delimitando toda a cadeia de caracteres entre aspas.

Por exemplo, para criar um novo arquivo de texto, insira o seguinte para o argumento /t:`templatename`.

```cmd
/t:"General\Style Sheet"
```

/e: `editorname`\
Opcional. O nome do editor no qual o arquivo será aberto. Se o argumento for especificado, mas nenhum nome de editor for fornecido, a caixa de diálogo **Abrir com** será exibida.

A sintaxe do argumento /e:`editorname` usa os nomes de editor como eles são exibidos na **Caixa de diálogo Abrir Com**, entre aspas.

Por exemplo, para abrir uma folha de estilos no editor de código-fonte, insira o seguinte para o argumento /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Exemplo
Esse exemplo adiciona um novo item de solução, MyHTMLpg, à solução atual.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
