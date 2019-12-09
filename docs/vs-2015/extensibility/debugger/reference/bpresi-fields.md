---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 52a4b9719b03c353dd3933c16b6f494f19f9c6ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153196"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica as informações a serem recuperados sobre a resolução bem-sucedida de um ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membros  
 BPRESI_BPRESLOCATION  
 Inicialização/usar o `bpResLocation` campo (localização de resolução de ponto de interrupção) a [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estrutura.  
  
 BPRESI_PROGRAM  
 Inicialização/usar o `pProgram` campo do `BP_RESOLUTION_INFO` estrutura.  
  
 BPRESI_THREAD  
 Inicialização/usar o `pThread` campo do `BP_RESOLUTION_INFO` estrutura.  
  
 BPRESI_ALLFIELDS  
 Especifica todos os campos.  
  
## <a name="remarks"></a>Comentários  
 Passado para o [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) método para indicar quais campos da [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) são de estrutura a ser inicializado.  
  
 Esses sinalizadores também são usados para indicar quais campos do `BP_RESOLUTION_INFO` estrutura são usados e válidos quando essa estrutura é retornada.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
