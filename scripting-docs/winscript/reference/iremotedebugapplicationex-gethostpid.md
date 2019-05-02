---
title: IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:GetHostPid
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d660cce006e7f84f1b1c01f1ec0a406b5c4b9df3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934581"
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid

Retorna a ID de processo para o aplicativo host.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetHostPid(
   DWORD*  dwHostPid
);
```

### <a name="parameters"></a>Parâmetros

`dwHostPid`

[out] O identificador de processo do host.

## <a name="return-value"></a>Valor de retorno

O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.

|Valor|Descrição|
|-----------|-----------------|
|`S_OK`|O método foi bem-sucedido.|

## <a name="remarks"></a>Comentários

Usado pelo IDE.

## <a name="see-also"></a>Consulte também

- [Interface IRemoteDebugApplicationEx](iremotedebugapplicationex-interface.md)