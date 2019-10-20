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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c84a2dcd99ef7cff9b5f37a1c69f235582a7973
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666424"
---
# <a name="open-project-command"></a>Comando Abrir projeto

Abre uma solução ou um projeto existente.

## <a name="syntax"></a>Sintaxe

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Arguments

`filename`

Necessário. O caminho completo e o nome do arquivo do projeto ou da solução a serem abertos.

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

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)