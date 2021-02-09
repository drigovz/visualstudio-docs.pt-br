---
title: 'IEnumDebugCustomAttributes:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::GetCount
helpviewer_keywords:
- IEnumDebugCustomAttributes::GetCount
ms.assetid: fafe826f-4ebf-4572-b2a3-d5dd2916c12f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1323af9d9d673e3d452882adff95b74213d7ad57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929265"
---
# <a name="ienumdebugcustomattributesgetcount"></a>IEnumDebugCustomAttributes::GetCount
Obtém o número de atributos personalizados em um enumerador.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCount( 
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parâmetros
`pcelt`\
fora Retorna o número de elementos na enumeração.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método não faz parte da interface de enumeração com personalizada que especifica que apenas `Next` , `Clone` , `Skip` e `Reset` precisam ser implementados.

## <a name="see-also"></a>Confira também
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
