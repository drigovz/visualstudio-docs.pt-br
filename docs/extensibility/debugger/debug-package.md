---
title: Pacote Debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739024"
---
# <a name="debug-package"></a>Pacote de depuração
O pacote de depuração é executado no shell do Visual Studio e lida com toda a ui. Ele consome as interfaces de depuração do Visual Studio e se comunica com o Gerenciador de depuração de sessão (SDM).

 Quebrar eventos enviados através do SDM alternar o depurador do modo de execução para o modo de pausa e alterar o foco para o programa onde ocorreu a quebra. O pacote de depuração rastreia o quadro de pilha e o segmento a partir das informações enviadas pelos eventos.

 O pacote de depuração não tem dependências de ambiente de idioma ou tempo de execução. Não é necessário implementar ou modificar o pacote de depuração.

 O pacote de depuração é implementado por *vsdebug.dll*.

## <a name="see-also"></a>Confira também
- [Gerente de depuração de sessão](../../extensibility/debugger/session-debug-manager.md)
- [Quadros de pilha](../../extensibility/debugger/stack-frames.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
