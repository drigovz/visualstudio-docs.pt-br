---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f0eb7cab3b1bc764f663cd647811928510281e8
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432009"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Abre o arquivo especificado em uma instância existente do Visual Studio.

## <a name="syntax"></a>Sintaxe

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Arguments

- *File1*

  Opcional. O arquivo a ser aberto em uma instância existente do Visual Studio. Se não existir nenhuma instância do Visual Studio, uma nova instância será criada com um layout de janela simplificado, e a ferramenta abrirá *File1* na nova instância.

- *FileN*

  Opcional. Um ou mais arquivos adicionais a serem abertos na instância existente do Visual Studio.

## <a name="remarks"></a>Comentários

Quando um arquivo não é especificado, uma instância existente do Visual Studio fica em destaque. Se nenhum arquivo for especificado e não existir nenhuma instância do Visual Studio, a ferramenta criará uma instância com um layout de janela simplificado.

Se a instância existente do Visual Studio estiver em estado modal, o arquivo será aberto na instância existente quando o Visual Studio sair do estado modal. Por exemplo, essa situação pode ocorrer quando a [caixa de diálogo Opções](../../ide/reference/options-dialog-box-visual-studio.md) estiver aberta.

Se mais de uma instância do Visual Studio estiver aberta, o arquivo será aberto na instância aberta mais recentemente.

## <a name="example"></a>Exemplo

O primeiro exemplo abre o arquivo `MyFile.cs` em uma instância existente do Visual Studio. Se não existir nenhuma instância do Visual Studio, a ferramenta abrirá o arquivo em uma nova instância. O segundo exemplo é semelhante, com exceção de que ela abre três arquivos em vez de apenas um.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
