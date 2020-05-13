---
title: Roteiro para estender o Depurador | Microsoft Docs
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
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713143"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roteiro para a extensão do depurador
Esta documentação fornece informações de [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] guia e referência [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]para estender o depurador com o .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]a documentação de depuração inclui amostras, uma referência abrangente e vários cenários representativos que demonstram maneiras típicas de personalizar o depurador.

 O compilador e sua saída determinam o que é necessário para configurar a depuração em seu produto. Se o seu compilador:

- Visa o sistema operacional nativo do Windows e escreve um *. Arquivo PDB,* você pode depurar programas com o mecanismo de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuração de código nativo (DE), que é integrado em . Você não precisa implementar um DE ou um avaliador de expressão. O avaliador de expressão é escrito para a sintaxe da linguagem de programação C++.

- Produz a saída de linguagem intermediária da Microsoft (MSIL), você pode depurar programas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]com o depurador de código gerenciado de cepa DE, que também é integrado em . Assim, você só precisa implementar um avaliador de expressão. Um avaliador de expressão de amostra é fornecido para você. Para obter mais informações, consulte estes tópicos:

   [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Avaliando expressões](../../extensibility/debugger/evaluating-expressions.md)

   [Contexto de avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)

   [Avaliação de expressão no modo de quebra](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Escreva um avaliador de expressão em tempo de execução de linguagem comum](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- O alvo de um sistema operacional proprietário ou algum outro ambiente de tempo de execução, você precisa escrever seu próprio DE. Um tutorial que cria um DE simples usando ATL COM é fornecido. Para obter mais informações, consulte estes tópicos:

   [Crie um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Tutorial: Construa um mecanismo de depuração usando ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Implementar um fornecedor portuário](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Exemplos](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Confira também
- [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
