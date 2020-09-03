---
title: Enumerador de mensagem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702501"
---
# <a name="message-enumerator"></a>Enumerador de mensagem
Os sinalizadores a seguir são usados para a `TEXTOUTPROC` função, que é uma função de retorno de chamada que o IDE fornece quando chama o [SccOpenProject](../extensibility/sccopenproject-function.md) (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obter detalhes sobre a função de retorno de chamada).

 Se o IDE for solicitado a cancelar o processo, ele poderá obter uma das mensagens de cancelamento. Nesse caso, o plug-in de controle do código-fonte usa `SCC_MSG_STARTCANCEL` para solicitar que o IDE exiba o botão **Cancelar** . Depois disso, qualquer conjunto de mensagens normais pode ser enviado. Se qualquer um desses retornos `SCC_MSG_RTN_CANCEL` , o plug-in encerrará a operação e retornará. O plug-in também pesquisa `SCC_MSG_DOCANCEL` periodicamente para determinar se o usuário cancelou a operação. Quando todas as operações forem concluídas, ou se o usuário tiver cancelado, o plug-in enviará `SCC_MSG_STOPCANCEL` . Os `SCC_MSG_INFO` tipos, SCC_MSG_WARNING e SCC_MSG_ERROR são usados para mensagens que são exibidas na lista de rolagem de mensagens. `SCC_MSG_STATUS` é um tipo especial que indica que o texto deve aparecer em uma barra de status ou área de exibição temporária. Ele não permanece permanentemente na lista.

## <a name="syntax"></a>Syntax

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
 SCC_MSG_RTN_CANCEL retornar do retorno de chamada para indicar cancelar.

 SCC_MSG_RTN_OK retornar do retorno de chamada para continuar.

 SCC_MSG_INFO mensagem é informativa.

 SCC_MSG_WARNING mensagem é um aviso.

 SCC_MSG_ERROR mensagem é um erro.

 SCC_MSG_STATUS mensagem é destinada à barra de status.

 SCC_MSG_DOCANCEL sem texto; O IDE retorna `SCC_MSG_RTN_OK` ou `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL inicia um loop de cancelamento.

 SCC_MSG_STOPCANCEL para o loop de cancelamento.

## <a name="see-also"></a>Confira também
- [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
