---
title: IDebugProperty2::EnumChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721515"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Recupera uma lista dos filhos da propriedade.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>parâmetros
`dwFields`\
[em] Uma combinação de bandeiras da enumeração [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) que especifica quais campos nas estruturas [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) enumeradas devem ser preenchidos.

`dwRadix`\
[em] Especifica o radix a ser usado na formatação de qualquer informação numérica.

`guidFilter`\
[em] GUID do filtro utilizado `dwAttribFilter` `pszNameFilter` com os `DEBUG_PROPERTY_INFO` parâmetros para selecionar quais crianças devem ser enumeradas. Por exemplo, `guidFilterLocals` filtros para variáveis locais.

`dwAttribFilter`\
[em] Uma combinação de bandeiras da enumeração [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que especifica que tipo `DBG_ATTRIB_METHOD` de objetos enumerar, por exemplo, para todos os métodos que podem ser filhos desta propriedade. Usado em combinação `guidFilter` `pszNameFilter` com os parâmetros.

`pszNameFilter`\
[em] O nome do filtro `guidFilter` usado `dwAttribFilter` com os `DEBUG_PROPERTY_INFO` parâmetros para selecionar quais crianças devem ser enumeradas. Por exemplo, definir este parâmetro para filtros "MyX" para todas as crianças com o nome "MyX".

`dwTimeout`\
[em] Especifica o tempo máximo, em milissegundos, para esperar antes de retornar deste método. Use `INFINITE` para esperar indefinidamente.

`ppEnum`\
[fora] Retorna um objeto [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contendo uma lista das propriedades do filho.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro.

## <a name="see-also"></a>Confira também
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
