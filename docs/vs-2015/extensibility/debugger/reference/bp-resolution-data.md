---
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4e266d1b5d0976ebc910a8228a3724f80001b5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153315"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Descreve o resultado da Associação de um ponto de interrupção de dados.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```csharp  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## <a name="members"></a>Membros  
 `bstrDataExpr`  
 A expressão de dados que foi associada.  
  
 `bstrFunc`  
 O nome da função em que o ponto de interrupção de dados está associado (se houver).  
  
 `bstrImage`  
 O nome do módulo (MyModule.dll, por exemplo) que o ponto de interrupção de dados está associado.  
  
 `dwFlags`  
 Um valor da enumeração [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) , que descreve como o ponto de interrupção de dados é implementado.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é um membro da estrutura de [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , que, por sua vez, é um membro da estrutura de [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) retornada pelo método [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
