---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e69435a319a9730af846a912cb3f90a12d4ac8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945777"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Compara dois arquivos. As diferenças são exibidas em uma janela especial do Visual Studio.

## <a name="syntax"></a>Sintaxe

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Arguments

- *SourceFile*

  Necessário. O caminho completo e o nome do primeiro arquivo a ser comparado.

- *TargetFile*

  Necessário. O caminho completo e o nome do segundo arquivo a ser comparado.

- *SourceDisplayName*

  Opcional. O nome de exibição do primeiro arquivo.

- *TargetDisplayName*

  Opcional. O nome de exibição do segundo arquivo.

## <a name="remarks"></a>Comentários

Se uma instância do IDE já estiver aberta, a comparação de arquivos aparecerá em uma guia no IDE do atual.

## <a name="example"></a>Exemplo

O primeiro exemplo compara dois arquivos sem alterar seus nomes de exibição. O segundo exemplo compara os arquivos alterando seus nomes de exibição. Os terceiro e quarto exemplos comparam dois arquivos, mas aplicam um alias somente ao primeiro ou ao segundo arquivo.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
