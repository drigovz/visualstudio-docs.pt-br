---
title: IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551261414db9fab97f3e8c2a8fdbe518143d79c5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315192"
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
[no, out] Uma matriz que é preenchida com os bytes de atributo.

`pdwLen`\
[no, out] Especifica o número máximo de bytes a serem retornados no `ppBlob` de matriz e retorna o número de bytes realmente gravados na matriz.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Defina o `ppBlob` atributos de parâmetro para um valor null para retornar o número de bytes disponíveis. Em seguida, aloque uma matriz e passar a matriz em para o `ppBlob` parâmetro.

 Os bytes de atributo representam os dados brutos do atributo personalizado.

## <a name="see-also"></a>Consulte também
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)