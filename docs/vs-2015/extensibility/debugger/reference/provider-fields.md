---
title: PROVIDER_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ba0f7cb33ef0bf7fde63d53997d014536e46a85b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204972"
---
# <a name="providerfields"></a>PROVIDER_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica as propriedades associadas a um provedor de programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
typedef DWORD PROVIDER_FIELDS;  
```  
  
```csharp  
public enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
```  
  
## <a name="members"></a>Membros  
 PFIELD_PROGRAM_NODES  
 O `ProgramNodes` campo é válido.  
  
 PFIELD_IS_DEBUGGER_PRESENT  
 O `fIsDebuggerPresent` campo é válido.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são retornados na `Fields` membro a [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) estrutura para indicar quais campos da estrutura foram preenchidos explicitamente.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
