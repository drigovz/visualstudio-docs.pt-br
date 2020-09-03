---
title: 'IDebugObject:: IsReadOnly | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19546550f916e9d42adf634b0d85958ce9697d28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726420"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Determina se este objeto é somente leitura.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Parâmetros
`pfIsReadOnly`\
fora Retornará um valor diferente de zero ( `TRUE` ) se esse objeto for somente leitura; caso contrário, retornará zero ( `FALSE` ).

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um objeto somente leitura não pode ter seu valor alterado depois de ser criado.

## <a name="see-also"></a>Confira também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
