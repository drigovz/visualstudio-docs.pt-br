---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728865"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Este método obtém informações estendidas sobre um campo.

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

## <a name="parameters"></a>parâmetros
`guidExtendedInfo`\
[em] Seleciona as informações a serem devolvidas. Os valores válidos são:

|Valor|Descrição|
|-----------|-----------------|
|`guidConstantValue`|O valor como uma seqüência de bytes.|
|`guidConstantType`|O tipo como uma assinatura de tipo.|

`prgBuffer`\
[fora] Retorna as informações estendidas.

`pdwLen`\
[dentro, fora] Retorna o tamanho das informações estendidas, em bytes.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Atualmente, este método retorna apenas o tipo ou valor de uma constante. O chamador deve liberar `prgBuffer` o buffer retornado ligando para a função do `CoTaskMemFree` COM (C++) ou <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>Confira também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
