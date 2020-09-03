---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7700670774dcb38b054cf28275f64c0c3046f741
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205036"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especificou o tipo de informações a serem recuperadas para um processo.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Membros  
 PIF_FILE_NAME  
 Inicializar/usar o `bstrFileName` campo da estrutura de [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 PIF_BASE_NAME  
 Inicializar/usar o `bstrBaseName` campo da `PROCESS_INFO` estrutura.  
  
 PIF_TITLE  
 Inicializar/usar o `bstrTitle` campo da `PROCESS_INFO` estrutura.  
  
 PIF_PROCESS_ID  
 Inicializar/usar o `ProcessId` campo da `PROCESS_INFO` estrutura.  
  
 PIF_SESSION_ID  
 Inicializar/usar o `dwSessionId` campo da `PROCESS_INFO` estrutura.  
  
 PIF_ATTACHED_SESSION_NAME  
 Inicializar/usar o `bstrAttachedSessionName` campo da `PROCESS_INFO` estrutura.  
  
 PIF_CREATION_TIME  
 Inicializar/usar o `CreationTime` campo da `PROCESS_INFO` estrutura.  
  
 PIF_FLAGS  
 Inicializar/usar o `Flags` campo da `PROCESS_INFO` estrutura.  
  
 PIF_ALL  
 Preenche todos os campos.  
  
## <a name="remarks"></a>Comentários  
 Passado para o método [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) para indicar quais campos da estrutura de [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) devem ser inicializados.  
  
 Também usado no `Fields` campo da `PROCESS_INFO` estrutura para indicar quais campos são usados e válidos.  
  
 Esses sinalizadores podem ser combinados com uma operadora de bits `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
