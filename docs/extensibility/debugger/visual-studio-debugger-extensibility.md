---
title: Extensibilidade do depurador do Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df9d1bccb2147d8416555099f3493ceac8c21b4b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704794"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidade do depurador do Visual Studio
O Visual Studio inclui um depurador de código fonte totalmente interativas, fornecendo uma ferramenta poderosa e fácil de usar para rastrear bugs em seu programa. O depurador tem suporte completo ao Visual Basic, c#, C/C++ e JavaScript. No entanto, com o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], que é disponível do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), outras linguagens de programação podem ter suporte no depurador com os mesmos recursos avançados.

 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador é o front-end comum (ou seja, a interface do usuário) para os componentes de depuração que são, por sua vez, específicas da linguagem que está sendo depurada. Para novas linguagens, tudo o que é necessário para dar suporte ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador é criar os componentes de back-end necessários, como um mecanismo de depuração (DES). Esse ponto é onde o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] chega.

 O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] inclui uma referência completa a todos os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementos necessários para criar DE um novo. Além disso, há exemplos e tutoriais que ajudarão você a começar.

 Para obter um exemplo completo de um sistema de projeto de linguagem com suporte à depuração, consulte o [exemplo de IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 As seções a seguir descrevem como estender o depurador usando o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>Nesta seção
 [Introdução ao](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) descreve o que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ofertas e como instalar o SDK de depuração.

 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) documenta o processo DE personalizado, de preparação de seu programa para a DE para desanexar o DE.

 [Escrever um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) explica se você deve escrever um avaliador de expressão.

 [Escolha uma estratégia de implementação do mecanismo de depuração](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) discute como implementar seu DE.

 [Referência](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) documentos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API de depuração.

 [Exemplos de](../../extensibility/debugger/visual-studio-debugging-samples.md) contém links para uma amostra do avaliador de expressão comum language runtime e um exemplo de mecanismo de depuração.
