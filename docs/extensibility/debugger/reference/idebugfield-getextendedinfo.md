---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0321dfbdc719d8e155bb1ee035032e2862bb90e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873858"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Esse método obtém informações estendido sobre um campo.

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

#### <a name="parameters"></a>Parâmetros
 `guidExtendedInfo`

 [in] Seleciona as informações a serem retornados. Os valores válidos são:

|Valor|Descrição|
|-----------|-----------------|
|`guidConstantValue`|O valor como uma sequência de bytes.|
|`guidConstantType`|O tipo como uma assinatura de tipo.|

 `prgBuffer`

 [out] Retorna as informações estendidas.

 `pdwLen`

 [no, out] Retorna o tamanho das informações estendidas, em bytes.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Atualmente, esse método retorna apenas o tipo ou valor de uma constante. O chamador deve liberar o buffer retornado no `prgBuffer` chamando do COM `CoTaskMemFree` função (C++) ou <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).

## <a name="see-also"></a>Consulte também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)