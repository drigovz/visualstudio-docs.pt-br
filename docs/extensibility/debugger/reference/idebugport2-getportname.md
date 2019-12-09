---
title: 'IDebugPort2:: getportname | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortName
helpviewer_keywords:
- IDebugPort2::GetPortName
ms.assetid: 4478b3d5-aa30-4105-8d05-e3bae2f8917a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0a382a77693fc8839721c0cdd139af2dd5208c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727717"
---
# <a name="idebugport2getportname"></a>IDebugPort2::GetPortName
Obtém o nome da porta.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPortName( 
   BSTR* pbstrName
);
```

```csharp
int GetPortName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parâmetros
`pbstrName`\
fora Retorna o nome da porta.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)