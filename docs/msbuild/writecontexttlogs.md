---
title: WriteContextTLogs | Microsoft Docs
description: Aprenda a sintaxe, os requisitos e o valor de retorno para WriteContextTLogs, que grava arquivos de log para o contexto atual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b44777f41c4fac3d36cb79222d48a93c5c1cf0b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887998"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Grava arquivos de log para o contexto atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
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

- [WriteAllTLogs](../msbuild/writealltlogs.md)