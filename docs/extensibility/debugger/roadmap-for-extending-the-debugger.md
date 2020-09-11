---
title: Roteiro para estender o depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d97a7edd62540d12a0a60d15b3179ca0a623c26
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011821"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roteiro para estender o depurador
Esta documentação fornece informações de guia e referência para estender o [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] depurador com o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a documentação de depuração inclui exemplos, uma referência abrangente e vários cenários representativos que demonstram maneiras típicas de personalizar o depurador.

 Seu compilador e sua saída determinam o que é necessário para configurar a depuração em seu produto. Se o seu compilador:

- Tem como alvo o sistema operacional Windows nativo e grava um *. Arquivo PDB* , você pode depurar programas com o mecanismo de depuração de código nativo (de), que é integrado ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Você não precisa implementar um avaliador DE expressão. O avaliador de expressão é escrito para a sintaxe da linguagem de programação C++.

- Produz a saída da MSIL (Microsoft Intermediate Language), você pode depurar programas com o mecanismo DE depuração DE código gerenciado DE, que também é integrado ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Portanto, você só precisa implementar um avaliador de expressão. Um avaliador de expressão de exemplo é fornecido para você. Para obter mais informações, consulte estes tópicos:

   [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Avaliando expressões](../../extensibility/debugger/evaluating-expressions.md)

   [Contexto de avaliação da expressão](../../extensibility/debugger/expression-evaluation-context.md)

   [Avaliação de expressão no modo de interrupção](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Gravar um avaliador de expressão de Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Tem como alvo um sistema operacional proprietário ou algum outro ambiente de tempo de execução, você precisa escrever seus próprios. Um tutorial que cria uma simples DE usar COM ATL é fornecido. Para obter mais informações, consulte estes tópicos:

   [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Tutorial: criar um mecanismo de depuração usando o COM ATL](/previous-versions/bb147024(v=vs.90))

   [Implementar um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Amostras](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Veja também
- [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)