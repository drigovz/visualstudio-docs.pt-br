---
title: WriteAllTLogs | Microsoft Docs
description: Aprenda a sintaxe, os requisitos e o valor de retorno para WriteAllTLogs, que grava logs de rastreamento para todos os threads e contextos.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65e0610c8148ab6ff32d8c19f6fd378ba46d76d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933590"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Grava logs de acompanhamento para todos os threads e os contextos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parâmetros

[in] `intermediateDirectory`

 O diretório no qual deseja armazenar o log de acompanhamento.

[in] `tlogRootName`

 O nome raiz do nome do arquivo de log.

## <a name="return-value"></a>Valor retornado

 Um **HRESULT** com o bit com **êxito** definido se o contexto de rastreamento foi criado.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Confira também

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)