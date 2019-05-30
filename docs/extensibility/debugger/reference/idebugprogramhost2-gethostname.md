---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 851905a9ca642f029444a2f6c1adfdfe543fdf70
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351268"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Obtém o título, o nome amigável ou o nome do arquivo do processo de hospedagem desse programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Parâmetros
`dwType`\
[in] Um valor a partir de [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumeração.

`pbstrHostName`\
[out] Retorna o nome solicitado do processo de hospedagem.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Em uma implementação típica desse método, o `dwType` parâmetro será ignorado e um nome amigável do computador host é retornado. Outra implementação possível é transmitir o `dwType` parâmetro para uma chamada para o [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) método para obter o nome.

## <a name="see-also"></a>Consulte também
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)