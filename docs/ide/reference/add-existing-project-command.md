---
title: Comando Adicionar Projeto Existente
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008802546d87bd44137c6d13ee2aef802877e308
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595872"
---
# <a name="add-existing-project-command"></a>Comando Adicionar Projeto Existente
Adiciona um projeto existente à solução atual.

## <a name="syntax"></a>Sintaxe

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
`filename`\
Opcional. O caminho completo e nome do projeto, com a extensão, do projeto a adicionar à solução.

Se o argumento `filename` incluir espaços, ele deverá ficar entre aspas.

Se nenhum nome de arquivo for especificado, o comando abrirá a caixa de diálogo de arquivo para que o usuário possa escolher um projeto.

## <a name="remarks"></a>Comentários
O preenchimento automático tenta localizar o caminho e o nome do arquivo corretos enquanto você digita.

## <a name="example"></a>Exemplo
Este exemplo adiciona o projeto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], TestProject1, à solução atual.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Veja também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
