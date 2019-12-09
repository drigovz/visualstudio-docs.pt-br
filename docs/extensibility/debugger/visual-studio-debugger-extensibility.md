---
title: Extensibilidade do depurador do Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58bfec6fa09f6450afb8170d60acad39edacd590
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982451"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidade do depurador do Visual Studio
O Visual Studio inclui um depurador de código-fonte totalmente interativo, fornecendo uma ferramenta poderosa e fácil de usar para o rastreamento de bugs em seu programa. O depurador tem suporte completo para Visual Basic, C#, C/C++e JavaScript. No entanto, com o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], que está disponível no [centro de download da Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), outras linguagens de programação podem ter suporte no depurador com os mesmos recursos avançados.

 O depurador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é o front-end comum (ou seja, a interface do usuário) para os componentes de depuração que, por sua vez, são específicos do idioma que está sendo depurado. Para novos idiomas, tudo o que é necessário para o suporte do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger é criar os componentes de back-end necessários, como um mecanismo DE depuração (DE). Esse ponto é onde o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] entra.

 O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] inclui uma referência completa a todos os elementos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] necessários para criar um novo DE. Além disso, há exemplos e tutoriais que ajudarão você a começar.

 Para obter um exemplo completo de um sistema de projeto de linguagem com suporte à depuração, consulte o [exemplo de IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 As seções a seguir descrevem como estender o depurador usando o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>Nesta seção
 [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Descreve o que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a depuração oferece e como instalar o SDK.

 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documenta o processo personalizado, de preparar seu programa para um DE para desanexar o DE.

 [Escrever um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Explica se você deve escrever um avaliador de expressão.

 [Escolher uma estratégia de implementação do mecanismo de depuração](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Discute como implementar o DE.

 [Referência](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) do Documenta a API de depuração de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 [Exemplos](../../extensibility/debugger/visual-studio-debugging-samples.md) Contém links para um exemplo de avaliador de expressão Common Language Runtime e um exemplo de mecanismo de depuração.
