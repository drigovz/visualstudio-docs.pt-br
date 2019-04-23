---
title: Escolhendo uma estratégia de implementação do mecanismo de depuração | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117681"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Escolhendo uma estratégia de implementação de mecanismo de depuração
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a arquitetura de tempo de execução para determinar sua estratégia de implementação de (DES) do mecanismo de depuração. O mecanismo de depuração pode ser criado no processo para o programa a ser depurado, no processo no Gerenciador de depuração de sessão do Visual Studio (SDM) ou out-of-process para ambos. As diretrizes a seguir devem ajudar a escolher entre essas três estratégias.  
  
## <a name="guidelines"></a>Diretrizes  
 Embora seja possível para o DE ser out-of-process para o SDM e o programa a ser depurado, normalmente há nenhum motivo para fazer isso. Chamadas entre limites de processo são relativamente lentas.  
  
 Depurar mecanismos já são fornecidos para o ambiente de tempo de execução nativo do Win32 e para o ambiente do common language runtime. Se for necessário substituir o DE para qualquer um desses ambientes, você deve criar o DE processo com o SDM.  
  
 Caso contrário, você pode escolher entre a criação DE em processo para o SDM ou em processo para o programa a ser depurado. É importante considerar se o avaliador de expressão de precisa de acesso frequente para o repositório de símbolos do programa e se o repositório de símbolos pode ser carregado na memória para acesso rápido. Além disso, considere o seguinte:  
  
- Se não houver muitas chamadas entre o avaliador de expressão e o repositório de símbolos, ou se o repositório de símbolos pode ser lidos no espaço de memória do SDM, crie o DE em processo para o SDM. Você deve retornar o CLSID do mecanismo de depuração para o SDM quando ele se conecta ao seu programa. O SDM usa este CLSID para criar uma instância no processo de.  
  
- Se o DE deve chamar o programa para acessar o repositório de símbolos, crie o DE processo com o programa. Nesse caso, o programa cria a instância do DE.  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
