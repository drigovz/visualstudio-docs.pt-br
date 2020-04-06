---
title: Escolhendo uma estratégia de implementação do mecanismo de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739132"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Escolha uma estratégia de implementação do mecanismo de depuração
Use a arquitetura de tempo de execução para determinar a estratégia de implementação do mecanismo de depuração (DE). Você pode criar o mecanismo de depuração em processo para o programa que você está depurando. Crie o mecanismo de depuração em processo para o Gerenciador de depuração de sessão do Visual Studio (SDM). Ou, criar o motor de depuração fora de processo para ambos. As seguintes diretrizes devem ajudá-lo a escolher entre essas três estratégias.

## <a name="guidelines"></a>Diretrizes
 Embora seja possível que o DE esteja fora de processo tanto para o SDM quanto para o programa que você está depurando, normalmente não há razão para fazê-lo. As chamadas através dos limites do processo são relativamente lentas.

 Os motores de depuração já são fornecidos para o ambiente de tempo de execução nativo Win32 e para o ambiente de tempo de execução comum. Se você tiver que substituir o DE por qualquer ambiente, você deve criar o DE em processo com o SDM.

 Caso contrário, você cria o DE em processo para o SDM ou em processo para o programa que você está depurando. Você precisará considerar se o avaliador de expressão do DE requer acesso frequente à loja de símbolos do programa. Ou, se a loja de símbolos pode ser carregada na memória para acesso rápido. Além disso, considere as seguintes abordagens:

- Se não houver muitas chamadas entre o avaliador de expressão e o armazenamento de símbolos, ou se o armazenamento de símbolos puder ser lido no espaço de memória SDM, crie o DE em processo para o SDM. Você deve devolver o CLSID do mecanismo de depuração ao SDM quando ele se conectar ao seu programa. O SDM usa este CLSID para criar uma instância em processo do DE.

- Se o DE deve chamar o programa para acessar a loja de símbolos, crie o DE em processo com o programa. Neste caso, o programa cria a instância do DE.

## <a name="see-also"></a>Confira também
- [Extensibilidade do depurador visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
