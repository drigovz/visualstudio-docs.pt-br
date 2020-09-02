---
title: 'IDebugProgram2:: Terminate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4673259e4a8ca0d4354037efbc35b63bedfcbc96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146339"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Encerra o programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se possível, o programa será encerrado e descarregado do processo; caso contrário, o mecanismo de depuração (DE) executará qualquer limpeza necessária.  
  
 Esse método ou o método [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) é chamado pelo IDE, normalmente em resposta ao usuário que está interrompendo toda a depuração. A implementação desse método deve, de preferência, encerrar o programa dentro do processo. Se isso não for possível, o DE deve impedir que o programa execute mais nenhum nesse processo (e faça qualquer limpeza necessária). Se o `IDebugProcess2::Terminate` método foi chamado pelo IDE, todo o processo será encerrado em algum momento depois que o `IDebugProgram2::Terminate` método for chamado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Encerrar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
