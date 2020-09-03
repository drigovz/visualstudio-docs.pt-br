---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205017"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contém informações sobre um processo.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Membros  
 Campos  
 Uma combinação de sinalizadores da enumeração de [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) que especifica quais campos são preenchidos.  
  
 bstrFileName  
 O nome do caminho completo do processo. Equivalente a chamar o método [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) com o parâmetro `GN_FILENAME` .  
  
 bstrBaseName  
 O nome do arquivo e a extensão do processo. Equivalente a chamar o `IDebugProcess2::Getname` método com o parâmetro `GN_BASENAME` .  
  
 bstrTitle  
 O título do processo, se houver. Equivalente a chamar o `IDebugProcess2::Getname` método com o parâmetro `GN_TITLE` .  
  
 ProcessId  
 A estrutura de [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) que identifica o processo. Equivalente a chamar o método [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) .  
  
 dwSessionId  
 O identificador da sessão de depuração em que esse processo está sendo executado.  
  
 bstrAttachedSessionName  
 O nome da sessão anexada. Equivalente a chamar o método [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) .  
  
 CreationTime  
 A hora em que o processo foi criado.  
  
 Flags  
 Uma combinação de sinalizadores da enumeração [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) que especificam as propriedades do processo.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o método [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) onde está preenchida.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
