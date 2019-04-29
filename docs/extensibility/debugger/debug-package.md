---
title: Depurar pacote | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ba784f3a544b2f66f1f2c9c229f85477bf6c782
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890033"
---
# <a name="debug-package"></a>Pacote de depuração
O pacote de depuração é executado no shell do Visual Studio e manipula toda a interface do usuário. Ele consome as interfaces de depuração do Visual Studio e se comunica com o Gerenciador de sessão de depuração (SDM).

 Eventos de interrupção enviados por meio do SDM alternar o depurador do modo de execução para o modo de interrupção e altere o foco para o programa onde a quebra ocorreu. O pacote de depuração acompanha o quadro de pilha e o thread a partir das informações enviadas a ele pelos eventos.

 O pacote de depuração não tem idioma ou as dependências do ambiente de tempo de execução. Não é necessário implementar ou modificar o pacote de depuração.

 O pacote de depuração é implementado pelo *vsdebug.dll*.

## <a name="see-also"></a>Consulte também
- [Gerenciador de sessão de depuração](../../extensibility/debugger/session-debug-manager.md)
- [Quadros de pilha](../../extensibility/debugger/stack-frames.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)