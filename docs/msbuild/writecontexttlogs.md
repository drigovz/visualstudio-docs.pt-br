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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5c0793cc6d9f11cd1074c5cd0091687b154c069
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579465"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Grava arquivos de log para o contexto atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>parâmetros
[in] `intermediateDirectory`

 O diretório no qual deseja armazenar o log de acompanhamento.

[in] `tlogRootName`

 O nome raiz do nome do arquivo de log.

## <a name="return-value"></a>Valor retornado
 Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o contexto de acompanhamento foi criado.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *FileTracker. h*

## <a name="see-also"></a>Confira também
- [WriteAllTLogs](../msbuild/writealltlogs.md)