---
title: 'IDebugClassField:: EnumBaseClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8648890e030799b985a4e917be8caf85292528a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947093"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Cria um enumerador para as classes base dessa classe.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`ppEnum`\

fora Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa a lista de classes base. Retorna um valor nulo se não houver nenhuma classe base.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK, retornará S_SH_NO_BASE_CLASSES se não houver nenhuma classe base (e o `ppEnum` parâmetro for definido como um valor nulo); caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 As classes base no objeto enumerador são especificadas na ordem da classe base mais imediata (ou mais derivada) para a classe base mais remota. Por exemplo, considerando as classes C++:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 A enumeração retornaria as classes base na ordem `Level2` , `Level1` , `Root` .

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
