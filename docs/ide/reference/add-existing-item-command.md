---
title: Comando Adicionar Item Existente
description: Saiba mais sobre o comando Adicionar item existente e como ele adiciona um arquivo existente a uma solução atual e o abre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59d1e032150035258df4b1cc88253cefc555d826
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871022"
---
# <a name="add-existing-item-command"></a>Comando Adicionar Item Existente
Adiciona um arquivo existente à solução atual e abre-o.

## <a name="syntax"></a>Sintaxe

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumentos
`filename`\
Obrigatórios. O caminho completo e o nome do arquivo, com a extensão, do item a adicionar à solução atual. Se o caminho do arquivo ou o nome do arquivo contiver espaços, coloque todo o caminho entre aspas.

## <a name="switches"></a>Comutadores
/e: `editorname`\
Opcional. Nome do editor no qual o arquivo será aberto. Se o argumento for especificado, mas nenhum nome de editor for fornecido, a caixa de diálogo **Abrir com** será exibida.

A sintaxe do argumento /e:`editorname` usa os nomes de editor como eles são exibidos na **Caixa de diálogo Abrir Com**, entre aspas. Por exemplo, para abrir uma folha de estilos no editor de código-fonte, insira o seguinte para o argumento /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Comentários
O preenchimento automático tenta localizar o caminho e o nome do arquivo corretos enquanto você digita.

## <a name="example"></a>Exemplo
Este exemplo adiciona o arquivo, Form1.frm, à solução atual.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
