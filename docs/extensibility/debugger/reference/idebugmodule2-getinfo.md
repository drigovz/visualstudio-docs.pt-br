---
title: IDebugModule2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c68c583702d7def5a7bff3ee40a9b8b2c537bb31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726956"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Obtém informações sobre este módulo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

## <a name="parameters"></a>parâmetros
`dwFields`\
[em] Uma combinação de [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) bandeiras da enumeração `pInfo` MODULE_INFO_FIELDS que especificam quais campos devem ser preenchidos.

`pInfo`\
[dentro, fora] Uma [estrutura MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) que é preenchida com uma descrição do módulo.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A estrutura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) contém o nome do módulo exibido na janela **Módulos.**

## <a name="see-also"></a>Confira também
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
