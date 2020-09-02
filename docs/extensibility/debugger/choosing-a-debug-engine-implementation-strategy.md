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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739132"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Escolher uma estratégia de implementação do mecanismo de depuração
Use a arquitetura de tempo de execução para determinar sua estratégia DE implementação do mecanismo DE depuração. Você pode criar o mecanismo de depuração em processo para o programa que você está depurando. Crie o mecanismo de depuração em processo para o SDM (Gerenciador de depuração de sessão) do Visual Studio. Ou crie o mecanismo de depuração fora do processo para ambos. As diretrizes a seguir devem ajudá-lo a escolher entre essas três estratégias.

## <a name="guidelines"></a>Diretrizes
 Embora seja possível que o DE seja fora do processo para o SDM e o programa que você está Depurando, normalmente não há motivo para isso. Chamadas entre limites de processo são relativamente lentas.

 Os mecanismos de depuração já são fornecidos para o ambiente de tempo de execução nativo do Win32 e para o ambiente de tempo de execução de idioma comum. Se for necessário substituir o de um dos ambientes, você deverá criar o DE em processo com o SDM.

 Caso contrário, você criará o DE em processo para o SDM ou em processo para o programa que você está depurando. Você precisará considerar se o avaliador de expressão de DE requer acesso frequente ao armazenamento de símbolos do programa. Ou, se o armazenamento de símbolos puder ser carregado na memória para acesso rápido. Além disso, considere as seguintes abordagens:

- Se não houver muitas chamadas entre o avaliador de expressão e o armazenamento de símbolos, ou se o repositório de símbolos puder ser lido no espaço de memória do SDM, crie o DE em processo para o SDM. Você deve retornar o CLSID do mecanismo de depuração para o SDM quando ele for anexado ao seu programa. O SDM usa esse CLSID para criar uma instância em processo do de.

- Se o DE precisar chamar o programa para acessar o armazenamento de símbolo, crie o DE em processo com o programa. Nesse caso, o programa cria a instância do de.

## <a name="see-also"></a>Confira também
- [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
