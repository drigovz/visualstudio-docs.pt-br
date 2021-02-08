---
title: Depurar pacote | Microsoft Docs
description: Saiba como o pacote de depuração é executado no Shell do Visual Studio e manipula a interface do usuário consumindo as interfaces de depuração e se comunicando com o Gerenciador de depuração de sessão.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e5296a77e835ab291bce7a77e3f0cb09eb6bcf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840841"
---
# <a name="debug-package"></a>Pacote de depuração
O pacote de depuração é executado no Shell do Visual Studio e manipula toda a interface do usuário. Ele consome as interfaces de depuração do Visual Studio e se comunica com o SDM (Session Debug Manager).

 Eventos de interrupção enviados por meio do SDM alternam o depurador do modo de execução para o modo de interrupção e alteram o foco para o programa em que ocorreu a interrupção. O pacote de depuração rastreia o quadro de pilha e o thread das informações enviadas a ele pelos eventos.

 O pacote de depuração não tem nenhuma linguagem ou dependências de ambiente de tempo de execução. Não é necessário implementar ou modificar o pacote de depuração.

 O pacote de depuração é implementado pelo *vsdebug.dll*.

## <a name="see-also"></a>Consulte também
- [Gerenciador de depuração de sessão](../../extensibility/debugger/session-debug-manager.md)
- [Quadros de pilha](../../extensibility/debugger/stack-frames.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
