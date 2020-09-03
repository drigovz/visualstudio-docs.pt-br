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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183465"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Escolhendo uma estratégia de implementação de mecanismo de depuração
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a arquitetura de tempo de execução para determinar sua estratégia DE implementação do mecanismo DE depuração. O mecanismo de depuração pode ser criado em processo para o programa a ser depurado, em processo para o SDM (Gerenciador de depuração de sessão) do Visual Studio, ou fora de processo para ambos. As diretrizes a seguir devem ajudá-lo a escolher entre essas três estratégias.  
  
## <a name="guidelines"></a>Diretrizes  
 Embora seja possível que o DE seja fora do processo para o SDM e o programa a ser depurado, normalmente não há motivo para isso. Chamadas entre limites de processo são relativamente lentas.  
  
 Os mecanismos de depuração já são fornecidos para o ambiente de tempo de execução nativo do Win32 e para o ambiente de Common Language Runtime. Se for necessário substituir o de para qualquer um desses ambientes, você deverá criar o DE em processo com o SDM.  
  
 Caso contrário, você pode escolher entre criar o DE em processo para o SDM ou em processo para o programa a ser depurado. É importante considerar se o avaliador de expressão de DE precisa de acesso frequente ao armazenamento de símbolos do programa e se o armazenamento de símbolos pode ser carregado na memória para acesso rápido. Considere também o seguinte:  
  
- Se não houver muitas chamadas entre o avaliador de expressão e o armazenamento de símbolos, ou se o repositório de símbolos puder ser lido no espaço de memória do SDM, crie o DE em processo para o SDM. Você deve retornar o CLSID do mecanismo de depuração para o SDM quando ele for anexado ao seu programa. O SDM usa esse CLSID para criar uma instância em processo do de.  
  
- Se o DE precisar chamar o programa para acessar o armazenamento de símbolo, crie o DE em processo com o programa. Nesse caso, o programa cria a instância do de.  
  
## <a name="see-also"></a>Consulte Também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
