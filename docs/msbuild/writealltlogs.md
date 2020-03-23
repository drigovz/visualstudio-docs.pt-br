---
title: WriteAllTLogs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eadb30ee25b1182be5deb12feebd5ef280ebf4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630672"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Grava logs de acompanhamento para todos os threads e os contextos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>parâmetros

[in] `intermediateDirectory`

 O diretório no qual deseja armazenar o log de acompanhamento.

[in] `tlogRootName`

 O nome raiz do nome do arquivo de log.

## <a name="return-value"></a>Valor retornado

 Um **HRESULT** com o **conjunto de bits BEM SUCEDIDO** se o contexto de rastreamento foi criado.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Confira também

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)