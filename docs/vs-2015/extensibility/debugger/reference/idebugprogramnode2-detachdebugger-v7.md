---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c60bc42895a0527f1638dada5a28a1631314e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838485"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Preterido. NÃO USE.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Uma implementação sempre deve retornar `E_NOTIMPL` .  
  
## <a name="remarks"></a>Comentários  
  
> [!WARNING]
> A partir do [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , esse método não é mais usado e sempre deve retornar `E_NOTIMPL` .  
  
 Esse método é chamado quando o depurador é encerrado inesperadamente. Quando esse método é chamado, o DE deve retomar o programa como se o usuário fosse desanexado dele. Não devem ser enviados mais eventos de depuração. O programa deve estar em um estado no qual é possível anexá-lo de outra instância do depurador.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
