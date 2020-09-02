---
title: 'IDebugStackFrame2:: EnumProperties | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f92db2c2fbafcd5be991281d7da4f594dcfb2c85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164798"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cria um enumerador para propriedades associadas ao registro de ativação, como variáveis locais.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFieldSpec`  
 no Uma combinação de sinalizadores da enumeração [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) que especifica quais campos nas estruturas de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) enumeradas devem ser preenchidos.  
  
 `nRadix`  
 no A base a ser usada na formatação de qualquer informação numérica.  
  
 `refiid`  
 no Um GUID de um filtro usado para selecionar quais estruturas de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) devem ser enumeradas, como `guidFilterLocals` .  
  
 `dwTimeout`  
 no Tempo máximo, em milissegundos, a aguardar antes de retornar deste método. Use `INFINITE` para aguardar indefinidamente.  
  
 `pcelt`  
 fora Retorna o número de propriedades enumeradas. Isso é o mesmo que chamar o método [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) .  
  
 `ppEnum`  
 fora Retorna um objeto [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) que contém uma lista das propriedades desejadas.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Como esse método permite que todas as propriedades selecionadas sejam recuperadas com uma única chamada, ela é mais rápida do que chamar sequencialmente os métodos [Getdebugproperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) e [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [Getdebugproperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
