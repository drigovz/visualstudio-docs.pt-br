---
title: IDebugProgram2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e18aa5611e7440322e08828060714b4fad954b89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870430"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Obtém as propriedades do programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

#### <a name="parameters"></a>Parâmetros
 `ppProperty`

 [out] Retorna um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa as propriedades do programa.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 As propriedades retornadas por esse método são específicas para o programa. Se o programa precisa retornar mais de uma propriedade, em seguida, a [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto retornado por esse método é um recipiente de propriedades adicionais e chamar o [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método retorna um lista de todas as propriedades.

 Um programa pode expor qualquer número e tipo de propriedades adicionais que podem ser descritos por meio de `IDebugProperty2` interface. Um IDE pode exibir as propriedades adicionais do programa por meio de uma interface de usuário do navegador de propriedade genérica.

## <a name="see-also"></a>Consulte também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)