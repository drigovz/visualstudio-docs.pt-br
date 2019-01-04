---
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6aa97560982b49f4544589b18b72892c683d24e7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850512"
---
# <a name="seekstart"></a>SEEK_START
Especifica a posição da qual iniciar a busca em um fluxo de desmontagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>Membros  
 SEEK_START_BEGIN  
 Inicia a busca no início do documento atual.  
  
 SEEK_START_END  
 Inicia a busca no final do documento atual.  
  
 SEEK_START_CURRENT  
 Inicia a busca da posição atual do documento atual.  
  
 SEEK_START_CODECONTEXT  
 Inicia a busca no contexto do código fornecido do documento atual.  
  
 SEEK_START_CODELOCID  
 Inicia a busca no identificador de local de código fornecida. Identificadores de local de código são obtidos chamando [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [busca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Busca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)