---
title: LAUNCH_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f209ed773a72c3925661bd81ecfe2685408b3189
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926733"
---
# <a name="launchflags"></a>LAUNCH_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica os sinalizadores de inicialização de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_LAUNCH_FLAGS {   
   LAUNCH_DEBUG      = 0x0000,  
   LAUNCH_NODEBUG    = 0x0001,  
   LAUNCH_ENABLE_ENC = 0x0002,  
   LAUNCH_MERGE_ENV  = 0x0004  
};  
typedef DWORD LAUNCH_FLAGS;  
```  
  
```csharp  
public enum enum_LAUNCH_FLAGS {   
   LAUNCH_DEBUG      = 0x0000,  
   LAUNCH_NODEBUG    = 0x0001,  
   LAUNCH_ENABLE_ENC = 0x0002,  
   LAUNCH_MERGE_ENV  = 0x0004  
};  
```  
  
## <a name="members"></a>Membros  
 LAUNCH_DEBUG  
 Inicia o processo de depuração.  
  
 LAUNCH_NODEBUG  
 Inicia o processo sem depurá-lo.  
  
 LAUNCH_ENABLE_ENC  
 PRETERIDO, NÃO USE.  
  
 LAUNCH_MERGE_ENV  
 Inicia o processo e mescla o ambiente com o host inicia.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados como um argumento para o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
