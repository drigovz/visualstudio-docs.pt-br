---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf58c25611fd52c6e8db8e8210101e1c80153275
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844532"
---
# <a name="diff"></a>/Diff
Compara dois arquivos. As diferenças são exibidas em uma janela especial do Visual Studio.

## <a name="syntax"></a>Sintaxe

```cmd
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>Arguments
 `SourceFile`

 Necessário. O caminho completo e o nome do primeiro arquivo a ser comparado.

 `TargetFile`

 Necessário. O caminho completo e o nome do segundo arquivo a ser comparado

 `SourceDisplayName`

 Opcional. O nome de exibição do primeiro arquivo.

 `TargetDisplayName`

 Opcional. O nome de exibição do segundo arquivo.