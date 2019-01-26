---
title: Enumerador de mensagem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fb85f727f4059e76bf5b73c71c0514a4c8cfc24
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969779"
---
# <a name="message-enumerator"></a>Enumerador de mensagem
Os sinalizadores a seguir são usados para o `TEXTOUTPROC` função, que é uma função de retorno de chamada que o IDE fornece quando ele chama o [SccOpenProject](../extensibility/sccopenproject-function.md) (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obter detalhes sobre o retorno de chamada função).  
  
 Se o IDE é solicitado para cancelar o processo, ele poderá receber uma das mensagens de cancelamento. Nesse caso, o controle de fonte usos de plug-in `SCC_MSG_STARTCANCEL` pedir o IDE para exibir o **Cancelar** botão. Depois disso, qualquer conjunto de mensagens normais pode ser enviado. Se qualquer um desses retorna `SCC_MSG_RTN_CANCEL`, em seguida, fecha a operação e retorna o plug-in. O plug-in também pesquisa `SCC_MSG_DOCANCEL` periodicamente para determinar se o usuário cancelou a operação. Quando todas as operações são executadas, ou se o usuário tiver cancelado, o plug-in envia `SCC_MSG_STOPCANCEL`. O `SCC_MSG_INFO`, SCC_MSG_WARNING, e os tipos SCC_MSG_ERROR são usados para mensagens que são exibidas na lista de rolagem de mensagens. `SCC_MSG_STATUS` é um tipo especial que indica que o texto deve aparecer em uma barra de status ou a área de exibição temporária. Ele não permanecem permanentemente na lista.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Membros  
 SCC_MSG_RTN_CANCEL  
 Retorno de chamada de retorno para indicar cancelamento.  
  
 SCC_MSG_RTN_OK  
 Retornar de retorno de chamada para continuar.  
  
 SCC_MSG_INFO  
 Mensagem é informativa.  
  
 SCC_MSG_WARNING  
 Mensagem é um aviso.  
  
 SCC_MSG_ERROR  
 Mensagem é um erro.  
  
 SCC_MSG_STATUS  
 Mensagem destina-se a barra de status.  
  
 SCC_MSG_DOCANCEL  
 Nenhum texto; Retorna de IDE `SCC_MSG_RTN_OK` ou `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Inicia um loop de cancelamento.  
  
 SCC_MSG_STOPCANCEL  
 Interrompe o loop de cancelamento.  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)