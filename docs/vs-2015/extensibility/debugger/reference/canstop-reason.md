---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 277164ea3dfcdabbe24622bb5148ebd75d54f8c9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58921774"
---
# <a name="canstopreason"></a>CANSTOP_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Usado para determinar se um programa pode interromper a execução depois de atingir um ponto específico na execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Membros  
 CANSTOP_ENTRYPOINT  
 Especifica o ponto de entrada de um determinado programa.  
  
 CANSTOP_STEPIN  
 Especifica a entrar em uma função.  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método para confirmar com a sessão de depuração SDM (Gerenciador de), se ele for okey parar depois de atingir o ponto de entrada do programa, ou depois de passar para uma função ou método.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
