---
title: Comando Adicionar Novo Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6237ace96799961683b0b0431f5dad3ab679e24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670205"
---
# <a name="add-new-item-command"></a>Comando Adicionar Novo Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Adiciona um novo item de solução, como um .htm, .css, .txt ou conjunto de quadros à solução atual e a abre.

## <a name="syntax"></a>Sintaxe

```
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Arguments
 `filename` Opcional. O nome de arquivo e o caminho do item a ser adicionado à solução.

## <a name="switches"></a>Opções
 /t: `templatename` Opcional. Especifica o tipo de arquivo a ser criado. Se nenhum nome de modelo for fornecido, um arquivo de texto será criado por padrão.

 A sintaxe do argumento /t:`templatename` espelha as informações encontradas na caixa de diálogo **Adicionar Novo Item de Solução**. É necessário inserir a categoria completa seguida pelo tipo de arquivo, separando o nome da categoria do tipo de arquivo por uma barra invertida (`\`) e delimitando toda a cadeia de caracteres entre aspas.

 Por exemplo, para criar um novo arquivo de texto, insira o seguinte para o argumento /t:`templatename`.

```
/t:"General\Style Sheet"
```

 /e: `editorname` Opcional. O nome do editor no qual o arquivo será aberto. Se o argumento for especificado, mas nenhum nome de editor for fornecido, a caixa de diálogo **Abrir com** será exibida.

 A sintaxe do argumento /e:`editorname` usa os nomes de editor como eles são exibidos na **Caixa de diálogo Abrir Com**, entre aspas.

 Por exemplo, para abrir uma folha de estilos no editor de código-fonte, insira o seguinte para o argumento /e:`editorname`.

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Exemplo
 Esse exemplo adiciona um novo item de solução, MyHTMLpg, à solução atual.

```
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Veja também
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [janela](../../ide/reference/command-window.md) de comando [Localizar/comando caixa](../../ide/find-command-box.md) de comandos do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
