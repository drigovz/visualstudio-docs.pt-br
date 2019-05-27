---
title: IDebugPort2::GetPortId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortId
helpviewer_keywords:
- IDebugPort2::GetPortId
ms.assetid: 837cb924-c113-4224-aa86-3e02b33dfa70
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa07d9b77706e2f4f8dbd754622dd14fc90c1000
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209251"
---
# <a name="idebugport2getportid"></a>IDebugPort2::GetPortId
Obtém o identificador de porta.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPortId( 
   GUID* pguidPort
);
```

```csharp
int GetPortId( 
   out Guid pguidPort
);
```

## <a name="parameters"></a>Parâmetros
`pguidPort`\
[out] Retorna o GUID que identifica a porta.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)