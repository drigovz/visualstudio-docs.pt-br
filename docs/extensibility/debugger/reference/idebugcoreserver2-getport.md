---
title: 'IDebugCoreServer2:: GetPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d8368ccc159fb31941f975c36d165cd943fb113
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929960"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Recupera uma porta específica.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Parâmetros
`guidPort`\
no GUID da porta a ser recuperada.

`ppPort`\
fora Retorna um objeto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa a porta desejada.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. Retorna `E_PORTSUPPLIER_NO_PORT` se não houver nenhuma porta com o identificador fornecido.

## <a name="see-also"></a>Confira também
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
