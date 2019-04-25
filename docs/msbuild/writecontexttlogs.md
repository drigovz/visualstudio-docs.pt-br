---
title: WriteContextTLogs | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 722d8c42786a7aaa2daae293b96f7926abcc90ca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777838"
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
 Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o contexto de acompanhamento foi criado.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Consulte também
- [WriteAllTLogs](../msbuild/writealltlogs.md)