---
title: IDebugDocument2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31eddcc07adc181e179c3f3edba669fff85fa565
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310272"
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

## <a name="parameters"></a>Parâmetros
`gnType`\
[in] Um valor a partir de [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) enumeração que determina o tipo de nome a ser retornado.

`pbstrFileName`\
[out] Retorna uma cadeia de caracteres que contém o nome do documento.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método pode, por exemplo, retornar o nome do documento como um título ou como um nome de arquivo ou até mesmo parte de um nome de arquivo.

## <a name="see-also"></a>Consulte também
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)