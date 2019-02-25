---
title: Escolhendo uma estratégia de implementação do mecanismo de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2fb608acdad60f5387750045a15f8eba36e2375
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683201"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Escolha uma estratégia de implementação do mecanismo de depuração
Use a arquitetura de tempo de execução para determinar sua estratégia de implementação de (DES) do mecanismo de depuração. Você pode criar o debug mecanismo em processo para o programa que você está depurando. Crie o debug mecanismo em processo para o Gerenciador de depuração de sessão do Visual Studio (SDM). Ou crie a depuração mecanismo fora de processo para os dois. As diretrizes a seguir devem ajudá-lo a escolher entre essas três estratégias.

## <a name="guidelines"></a>Diretrizes
 Embora seja possível para o DE ser out-of-process para o SDM e o programa que você está depurando, normalmente há nenhum motivo para fazer isso. Chamadas entre limites de processo são relativamente lentas.

 Depurar mecanismos já são fornecidos para o ambiente de tempo de execução nativo do Win32 e para o ambiente de tempo de execução de linguagem comum. Se você precisa substituir o DE para qualquer ambiente, você deve criar o DE processo com o SDM.

 Caso contrário, você cria o DE em processo para o SDM ou em processo para o programa que você está depurando. Você precisará considerar se o avaliador de expressão de requer acesso frequente para o repositório de símbolos do programa. Ou, se o repositório de símbolos pode ser carregado na memória para acesso rápido. Além disso, considere as seguintes abordagens:

-   Se não houver muitas chamadas entre o avaliador de expressão e o repositório de símbolos, ou se o repositório de símbolos pode ser lidos no espaço de memória do SDM, crie o DE em processo para o SDM. Você deve retornar o CLSID do mecanismo de depuração para o SDM quando ele se conecta ao seu programa. O SDM usa este CLSID para criar uma instância no processo de.

-   Se o DE deve chamar o programa para acessar o repositório de símbolos, crie o DE processo com o programa. Nesse caso, o programa cria a instância do DE.

## <a name="see-also"></a>Consulte também
- [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)