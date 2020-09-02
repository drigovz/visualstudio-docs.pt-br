---
title: Roteiro para estender o depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695952"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roteiro para estender o depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta documentação fornece informações de guia e referência para estender o [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] depurador com o [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a documentação de depuração inclui exemplos, uma referência abrangente e vários cenários representativos que demonstram maneiras típicas de personalizar o depurador.  
  
 Seu compilador e sua saída determinam o que você precisa fazer para implementar a depuração em seu produto. Se o seu compilador:  
  
- Tem como alvo o sistema operacional Windows nativo e grava um. Arquivo PDB, você pode depurar programas com o mecanismo DE depuração de código nativo (DE), que é integrado ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Você não precisa implementar um avaliador DE expressão. O avaliador de expressão é escrito para a sintaxe da linguagem de programação C++.  
  
- Produz a saída da MSIL (Microsoft Intermediate Language), você pode depurar programas com o mecanismo DE depuração DE código gerenciado DE, que também é integrado ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Portanto, você só precisa implementar um avaliador de expressão. Um avaliador de expressão de exemplo é fornecido para você. Para obter mais informações, consulte estes tópicos:  
  
     [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Avaliando expressões](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexto da avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Avaliação de expressão no modo de interrupção](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Escrever um avaliador de expressão do Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Tem como alvo um sistema operacional proprietário ou algum outro ambiente de tempo de execução, você precisa escrever seus próprios. Um tutorial que cria uma simples DE usar COM ATL é fornecido. Para obter mais informações, consulte estes tópicos:  
  
     [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: Criando um mecanismo de depuração usando o COM ATL](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementar um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Amostras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
