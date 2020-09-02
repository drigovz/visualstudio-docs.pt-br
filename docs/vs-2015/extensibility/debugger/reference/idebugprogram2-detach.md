---
title: IDebugProgram2::D Etach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Detach
helpviewer_keywords:
- IDebugProgram2::Detach
ms.assetid: 5e8d88b0-a8d4-4746-88c0-ad332ee73f33
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 922c3d4df6332fc5b9bc5b264c4d46b3f1b91805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62549318"
---
# <a name="idebugprogram2detach"></a>IDebugProgram2::Detach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Desanexa um mecanismo de depuração do programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um programa desanexado continua em execução, mas não faz mais parte da sessão de depuração. Nenhum evento de depuração de programas mais é enviado quando o mecanismo de depuração é desanexado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
