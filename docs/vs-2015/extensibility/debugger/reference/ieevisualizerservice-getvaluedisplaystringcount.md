---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6785be367430443f92a9cc54a2d636582053228e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192102"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Recupera o número de cadeias de caracteres a ser exibida para a propriedade especificada ou o campo de valor.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

#### <a name="parameters"></a>Parâmetros
 `displayKind`

 [in] O valor dos [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) enumeração.

 `propertyOrField`

 [in] Uma [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface que representa uma propriedade ou campo.

 `pcelt`

 [out] Retorna o número de cadeias de caracteres de valor para exibir.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)