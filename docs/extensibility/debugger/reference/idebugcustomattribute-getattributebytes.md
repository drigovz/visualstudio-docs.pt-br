---
title: 'IDebugCustomAttribute:: GetAttributeBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe0db0267898b54837cd9d05e39b0ddce97d21cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928452"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Obtém as informações de atributo como um blob de bytes.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Parâmetros
`ppBlob`\
[entrada, saída] Uma matriz que é preenchida com os bytes de atributo.

`pdwLen`\
[entrada, saída] Especifica o número máximo de bytes a serem retornados na `ppBlob` matriz e retorna o número de bytes gravados na matriz.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Defina o `ppBlob` parâmetro como um valor nulo para retornar o número de bytes de atributos disponíveis. Em seguida, aloque uma matriz e passe essa matriz no para o `ppBlob` parâmetro.

 Os bytes de atributo representam os dados brutos do atributo personalizado.

## <a name="see-also"></a>Confira também
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
