---
title: Comando Abrir Projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99596442f3aef9e4cb2d890438d29b96cdf4f083
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671915"
---
# <a name="open-project-command"></a>Comando Abrir Projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre um projeto existente.

## <a name="syntax"></a>Sintaxe

```
File.OpenProject filename
```

## <a name="arguments"></a>Argumentos
 `filename` Necessário. O nome de arquivo e caminho completo do projeto a abrir.

 A sintaxe para o argumento `filename` requer que os caminhos que contêm espaços usem aspas.

## <a name="remarks"></a>Comentários
 O preenchimento automático tenta localizar o caminho e o nome do arquivo corretos enquanto você digita.

 Esse comando não está disponível durante a depuração.

## <a name="example"></a>Exemplo
 Este exemplo abre o projeto [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], Test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Consulte Também
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [janela](../../ide/reference/command-window.md) de comando [Localizar/comando caixa](../../ide/find-command-box.md) de comandos do [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
