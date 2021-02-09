---
title: 'IDebugEngine3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f823f0087ee612a7850e000469271e0c2a778b62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887296"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Carrega (conforme necessário) símbolos para todos os módulos que estão sendo depurados por esse mecanismo de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parâmetros
 Nenhum.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna o código de erro.

## <a name="remarks"></a>Comentários
 Isso carrega os símbolos de depuração para todos os módulos referenciados por esse mecanismo de depuração. Os símbolos serão carregados somente se ainda não tiverem sido carregados. Os símbolos são pesquisados nos caminhos definidos por uma chamada para [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Confira também
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
