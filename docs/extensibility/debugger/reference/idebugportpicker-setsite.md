---
title: 'IDebugPortPicker:: SetSite | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c361291532a79e7e4dd466d07359f0fe9faf2be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958629"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Define o provedor de serviços.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>Parâmetros
`pSP`\
no Referência à interface do provedor de serviços.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método será chamado antes que quaisquer outros métodos sejam chamados.

## <a name="see-also"></a>Consulte também
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
