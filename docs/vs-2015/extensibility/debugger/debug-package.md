---
title: Depurar pacote | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dda8b1ac6eaa2cd5352d441600ae720c3aac321c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181298"
---
# <a name="debug-package"></a>Pacote de depuração
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O pacote de depuração é executado no Shell do Visual Studio e manipula toda a interface do usuário. Ele consome as interfaces de depuração do Visual Studio e se comunica com o SDM (Session Debug Manager).  
  
 Eventos de interrupção enviados por meio do SDM alternam o depurador do modo de execução para o modo de interrupção e alteram o foco para o programa em que ocorreu a interrupção. O pacote de depuração rastreia o quadro de pilha e o thread das informações enviadas a ele pelos eventos.  
  
 O pacote de depuração não tem nenhuma linguagem ou dependências de ambiente de tempo de execução. Não é necessário implementar ou modificar o pacote de depuração.  
  
 O pacote de depuração é implementado pelo vsdebug.dll.  
  
## <a name="see-also"></a>Consulte Também  
 [Gerenciador de depuração de sessão](../../extensibility/debugger/session-debug-manager.md)   
 [Quadros de pilha](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
