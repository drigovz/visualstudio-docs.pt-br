---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59506af5ad48bd18c454f4c59367921eed1e679a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62924071"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Recupera uma interface de código gerenciado que representa o valor associado a este alias.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

#### <a name="parameters"></a>Parâmetros
 `ppUnk`

 [out] `IUnknown` interface que representa o valor associado a este alias. Essa interface pode ser consultada para o `ICorDebugValue` interface.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método se aplica somente aos valores gerenciados (o `ICorDebugValue` é uma interface disponíveis na [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] e é definido no [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK no arquivo cordebug. idl).

## <a name="see-also"></a>Consulte também
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)