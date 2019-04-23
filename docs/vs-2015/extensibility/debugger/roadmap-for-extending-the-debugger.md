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
ms.openlocfilehash: 59e12a90d241bf07a53cc98c91eef4cfc6d7d063
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050979"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roteiro para estender o depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta documentação fornece informações de referência e a guia para estender a [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] do depurador com o [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuração da documentação inclui exemplos, uma referência abrangente e representativos vários cenários que demonstram maneiras comuns de personalizar o depurador.  
  
 O compilador e sua saída determinam o que você precisa fazer para implementar a depuração em seu produto. Se seu compilador:  
  
- Direciona o sistema operacional nativo do Windows e grava um. Arquivo PDB, você pode depurar programas com o mecanismo de depuração de código nativo (DES), que é integrado ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Você não precisa implementar um avaliador de expressão DE. O avaliador de expressão foi escrito para a sintaxe da linguagem de programação C++.  
  
- Produz a Microsoft intermediate language (MSIL) de saída, você pode depurar programas com o mecanismo de depuração de código gerenciado DE, que também é integrado ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Portanto, você só precisa implementar um avaliador de expressão. Um avaliador de expressão de exemplo é fornecido para você. Para mais informações, consulte os seguintes tópicos:  
  
     [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Avaliar expressões](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexto da avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Avaliação de expressão no modo de interrupção](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Escrever um avaliador de expressão do Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Destinos de um proprietário de sistema operacional ou outro ambiente de tempo de execução, você precisa escrever seu próprio DE. Um tutorial que cria um simples DE usando COM ATL é fornecido. Para mais informações, consulte os seguintes tópicos:  
  
     [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: Criando um mecanismo de depuração usando COM ATL](http://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementar um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Amostras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
