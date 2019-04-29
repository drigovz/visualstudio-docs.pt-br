---
title: IDebugDocument2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f1ef243afd607a565e2c7a8e6f557f0b9906c86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875728"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Obtém o nome do documento em uma das várias formas.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

#### <a name="parameters"></a>Parâmetros
 `gnType`

 [in] Um valor a partir de [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) enumeração que determina o tipo de nome a ser retornado.

 `pbstrFileName`

 [out] Retorna uma cadeia de caracteres que contém o nome do documento.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método pode, por exemplo, retornar o nome do documento como um título ou como um nome de arquivo ou até mesmo parte de um nome de arquivo.

## <a name="see-also"></a>Consulte também
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)