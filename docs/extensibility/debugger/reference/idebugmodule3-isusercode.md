---
title: 'IDebugModule3:: IsUserCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 435ec50ef5437e5aca5d3722a2041115882d15f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726836"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Recupera informações sobre se o módulo representa ou não o código do usuário.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Parâmetros
`pfUser`\
fora Diferente de zero ( `TRUE` ) se o módulo representar o código de usuário, zero ( `FALSE` ) se não tiver.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro.

## <a name="see-also"></a>Confira também
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
