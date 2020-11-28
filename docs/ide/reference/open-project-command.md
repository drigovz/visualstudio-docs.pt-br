---
title: Comando Abrir Projeto
description: Saiba mais sobre o comando Abrir projeto e como ele abre um projeto ou uma solução existente.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ce00713cbfe862c5788a0131c99ba4c5750bb600
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304139"
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
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
