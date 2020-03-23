---
title: Comando Abrir Projeto
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97c1034fbbafa04af2d62526fdbb48812d64e050
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565806"
---
# <a name="open-project-command"></a>Comando Abrir projeto

Abre uma solução ou um projeto existente.

## <a name="syntax"></a>Sintaxe

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argumentos

`filename`

Obrigatórios. O caminho completo e o nome do arquivo do projeto ou da solução a serem abertos.

> [!NOTE]
> A sintaxe do argumento `filename` requer que os caminhos que contêm espaços usem aspas.

## <a name="remarks"></a>Comentários

O preenchimento automático tenta localizar o caminho e o nome do arquivo corretos enquanto você digita.

Esse comando não está disponível durante a depuração.

## <a name="example"></a>Exemplo

O exemplo a seguir abre o projeto do Visual Basic **Test1**:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela de comando](../../ide/reference/command-window.md)
- [Caixa de encontrar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
