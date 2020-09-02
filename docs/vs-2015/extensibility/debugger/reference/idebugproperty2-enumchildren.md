---
title: 'IDebugProperty2:: EnumChildren | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cd5b29978b6b67cc80e95b86603b0caf487c26c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164950"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera uma lista dos filhos da propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 no Uma combinação de sinalizadores da enumeração [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) que especifica quais campos nas estruturas de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) enumeradas devem ser preenchidos.  
  
 `dwRadix`  
 no Especifica a base a ser usada na formatação de qualquer informação numérica.  
  
 `guidFilter`  
 no GUID do filtro usado com os `dwAttribFilter` parâmetros e `pszNameFilter` para selecionar quais `DEBUG_PROPERTY_INFO` filhos devem ser enumerados. Por exemplo, `guidFilterLocals` filtros para variáveis locais.  
  
 `dwAttribFilter`  
 no Uma combinação de sinalizadores da enumeração [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que especifica que tipo de objetos enumerar, por exemplo, `DBG_ATTRIB_METHOD` para todos os métodos que podem ser filhos dessa propriedade. Usado em combinação com os `guidFilter` `pszNameFilter` parâmetros e.  
  
 `pszNameFilter`  
 no O nome do filtro usado com os `guidFilter` parâmetros e `dwAttribFilter` para selecionar quais `DEBUG_PROPERTY_INFO` filhos devem ser enumerados. Por exemplo, definir esse parâmetro como "MyX" filtros para todos os filhos com o nome "MyX".  
  
 `dwTimeout`  
 no Especifica o tempo máximo, em milissegundos, a aguardar antes de retornar desse método. Use `INFINITE` para aguardar indefinidamente.  
  
 `ppEnum`  
 fora Retorna um objeto [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) que contém uma lista das propriedades filho.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
