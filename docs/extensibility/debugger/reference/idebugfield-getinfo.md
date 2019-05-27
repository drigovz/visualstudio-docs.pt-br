---
title: IDebugField::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d28db6824afe6230cc8e00fae8e144dc541af59
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212203"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Esse método obtém informações que pode ser exibidas sobre o campo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Parâmetros
`dwFields`\
[in] Uma combinação de [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) constantes que seleciona as informações a serem exibidos. Se o campo representa um símbolo, normalmente é o nome do símbolo e o tipo.

`pFieldInfo`\
[out] Retorna as informações no fornecido [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estrutura.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)