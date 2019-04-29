---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a55328c4148aa911d86b8f2daf05ba84a50ff444
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867970"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Esse método altera o objeto que representa o visualizador.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

#### <a name="parameters"></a>Parâmetros
 `pNewObject`

 [in] O objeto a ser definido.

 `error`

 [out] Se houver um erro ao configurar o objeto, essa cadeia de caracteres contém a mensagem de erro.

 `pException`

 [out] Se houver um erro, esse objeto contém as informações de exceção.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Cabe ao implementador para determinar como as informações de erro são retornadas. No entanto, é possível que alguns os chamadores podem ser somente olhada para ver se um objeto de exceção foi retornado, sabemos que existe foi um erro, portanto, esse método sempre deve retornar um objeto de exceção se ocorreu um erro. A cadeia de caracteres de erro também deve ser fornecida, caso o chamador deseja tornar usá-lo.

## <a name="see-also"></a>Consulte também
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)