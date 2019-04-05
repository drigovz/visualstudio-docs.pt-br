---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d471a73205383f0f23c5016872712a3ba2c578d6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924140"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica como interpretar uma ID de processo na [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Membros  
 AD_PROCESS_ID_SYSTEM  
 ID do processo é um identificador de sistema. Use o `ProcessId.dwProcessId` campo do [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura.  
  
 AD_PROCESS_ID_GUID  
 ID do processo é um GUID. Use o `ProcessId.guidProcessId` campo do `AD_PROCESS_ID` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Usado para o `ProcessIdType` membro do [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura para identificar o tipo de ID do processo que está contido na estrutura. Determina como interpretar o `ProcessId` union na estrutura.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
