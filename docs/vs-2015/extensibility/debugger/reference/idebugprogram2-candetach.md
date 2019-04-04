---
title: IDebugProgram2::CanDetach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a7f8bbabbba54cc7705aedc6e7f12ca1bffc924
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922082"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se um mecanismo de depuração (DES) poderá desanexar do programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se desanexar retorna `S_OK`; caso contrário, retorna um código de erro. Retorna `S_FALSE` se a DE não é possível desanexar do programa.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
