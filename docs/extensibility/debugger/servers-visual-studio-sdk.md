---
title: Servidores (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 109c24935511f98e5eb3b5d83270960e5a0c6855
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905538"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (SDK do Visual Studio)
Na arquitetura do depurador, uma *server*:  
  
-   É um contêiner de portas e os fornecedores de porta e comunica as portas e fornecedores de porta para o Gerenciador de sessão de depuração (SDM) e mecanismos de depuração.  
  
-   Pode identificar-se por nome e enumerar suas portas e os fornecedores de porta.  
  
-   É representado por um [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interface, que só é implementada pelo Visual Studio (uma instância de um servidor para cada instância de execução do Visual Studio).  
  
## <a name="see-also"></a>Consulte também  
 [Portas](../../extensibility/debugger/ports.md)   
 [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)