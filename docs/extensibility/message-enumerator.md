---
title: Enumerador de Mensagens | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702501"
---
# <a name="message-enumerator"></a>Enumerador de mensagens
Os seguintes sinalizadores `TEXTOUTPROC` são usados para a função, que é uma função de retorno de chamada que o IDE fornece quando chama o [SccOpenProject](../extensibility/sccopenproject-function.md) (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obter detalhes sobre a função de retorno de chamada).

 Se o IDE for solicitado a cancelar o processo, ele pode receber uma das mensagens de cancelamento. Neste caso, o plug-in `SCC_MSG_STARTCANCEL` de controle de origem usa para pedir ao IDE para exibir o botão **Cancelar.** Depois disso, qualquer conjunto de mensagens normais pode ser enviada. Se algum desses `SCC_MSG_RTN_CANCEL`retornos, então o plug-in encerra a operação e retorna. O plug-in `SCC_MSG_DOCANCEL` também pesquisa periodicamente para determinar se o usuário cancelou a operação. Quando todas as operações são feitas ou se o `SCC_MSG_STOPCANCEL`usuário tiver cancelado, o plug-in será enviado . Os `SCC_MSG_INFO`tipos , SCC_MSG_WARNING e SCC_MSG_ERROR são usados para mensagens que são exibidas na lista de rolagem de mensagens. `SCC_MSG_STATUS`é um tipo especial que indica que o texto deve aparecer em uma barra de status ou área de exibição temporária. Ele não permanece permanentemente na lista.

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
 SCC_MSG_RTN_CANCEL Retornar do retorno de chamada para indicar cancelar.

 SCC_MSG_RTN_OK Retorne de retorno para continuar.

 SCC_MSG_INFO Mensagem é informacional.

 SCC_MSG_WARNING Mensagem é um aviso.

 SCC_MSG_ERROR Mensagem é um erro.

 SCC_MSG_STATUS Message é destinado à barra de status.

 SCC_MSG_DOCANCEL Nenhum texto; O IDE retorna `SCC_MSG_RTN_OK` ou `SCC_MSG_RTN_CANCEL`.

 SCC_MSG_STARTCANCEL Inicia um loop de cancelamento.

 SCC_MSG_STOPCANCEL Pára o loop de cancelamento.

## <a name="see-also"></a>Confira também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
