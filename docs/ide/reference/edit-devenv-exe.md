---
title: -Edit (devenv.exe)
description: Saiba como usar a opção de linha de comando Editar devenv para abrir um arquivo especificado em uma instância existente do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45d0b1342ea0e53c4897881ebb5cfee0a7241d6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882069"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Abre o arquivo especificado em uma instância existente do Visual Studio.

## <a name="syntax"></a>Sintaxe

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argumentos

- *Arquivo1*

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

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
