---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84c36d08c7ad907006eb9f41d2f6e2c9cd77e7bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196038"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cria um ponto de interrupção pendente no mecanismo de depuração (DES).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBPRequest`  
 [in] Uma [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) objeto que descreve o ponto de interrupção pendente para criar.  
  
 `ppPendingBP`  
 [out] Retorna um [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa o ponto de interrupção pendente.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Normalmente retorna `E_FAIL` se o `pBPRequest` parâmetro não corresponde a qualquer linguagem compatível com o dos se o `pBPRequest` parâmetro é inválido ou incompleto.  
  
## <a name="remarks"></a>Comentários  
 Um ponto de interrupção pendente é essencialmente uma coleção de todas as informações necessárias para associar um ponto de interrupção no código. O ponto de interrupção pendente retornado desse método não está associado ao código até que o [associar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) método é chamado.  
  
 Para cada pendente do ponto de interrupção conjuntos de dados do usuário, o Gerenciador de sessão de depuração (SDM) chama esse método em cada DE anexado. É responsabilidade DE verificar se o ponto de interrupção é válido para programas em execução em que DE.  
  
 Quando o usuário define um ponto de interrupção em uma linha de código, a Alemanha é gratuita associar o ponto de interrupção para a linha mais próxima do documento que corresponde a esse código. Isso torna possível para o usuário definir um ponto de interrupção na primeira linha de uma instrução de várias linha, mas associá-lo na última linha (em que todo o código é atribuído nas informações de depuração).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um simples `CProgram` objeto. Implementação do `IDebugEngine2::CreatePendingBreakpoint` poderia, em seguida, encaminhar todas as chamadas para essa implementação do método em cada programa.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [associar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
