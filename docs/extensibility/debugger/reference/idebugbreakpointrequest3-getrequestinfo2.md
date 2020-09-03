---
title: 'IDebugBreakpointRequest3:: GetRequestInfo2 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5febf664da9cd69dbd88b70056d9eac953bf581
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734840"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
Esse método obtém as informações de solicitação de ponto de interrupção que descrevem essa solicitação de ponto de interrupção.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetRequestInfo2(
   BPREQI_FIELDS      dwFields,
   BP_REQUEST_INFO2*  bBPRequestInfo
);
```

```csharp
int GetRequestInfo2(
   enum_BPREQI_FIELDS  dwFields,
   BP_REQUEST_INFO2[]  bBPRequestInfo
);
```

## <a name="parameters"></a>Parâmetros
`dwFields`\
no Uma combinação de sinalizadores da enumeração [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) que determina quais campos do `pBPRequestInfo` devem ser preenchidos.

`bBPRequestInfo`\
fora A estrutura de [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) a ser preenchida.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro.

## <a name="remarks"></a>Comentários
 Há mais informações nesta solicitação do que é retornado do método [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .

## <a name="see-also"></a>Confira também
- [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
