---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1bd63d6b53359cf3b86f5e3849cb18bd8367f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722223"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Obtém o título, nome amigável ou nome do arquivo do processo de hospedagem deste programa.

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

## <a name="parameters"></a>parâmetros
`dwType`\
[em] Um valor da [enumeração GETHOSTNAME_TYPE.](../../../extensibility/debugger/reference/gethostname-type.md)

`pbstrHostName`\
[fora] Retorna o nome solicitado do processo de hospedagem.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Em uma implementação típica `dwType` deste método, o parâmetro é ignorado e um nome amigável da máquina host é devolvido. Outra implementação possível `dwType` é passar o parâmetro para uma chamada para o método [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) para obter o nome.

## <a name="see-also"></a>Confira também
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
