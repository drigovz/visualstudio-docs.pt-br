---
title: 'IDebugField:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 911556cb615e373d620b496fb31e5d6093b7cc37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869928"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Esse método obtém informações estendidas sobre um campo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Parâmetros
`guidExtendedInfo`\
no Seleciona as informações a serem retornadas. Os valores válidos são:

|Valor|Descrição|
|-----------|-----------------|
|`guidConstantValue`|O valor como uma sequência de bytes.|
|`guidConstantType`|O tipo como uma assinatura de tipo.|

`prgBuffer`\
fora Retorna as informações estendidas.

`pdwLen`\
[entrada, saída] Retorna o tamanho das informações estendidas, em bytes.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Atualmente, esse método retorna apenas o tipo ou o valor de uma constante. O chamador deve liberar o buffer retornado no `prgBuffer` chamando a função de com `CoTaskMemFree` (C++) ou <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>Consulte também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
