---
title: Extensibilidade do Debugger do Estúdio Visual | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712507"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidade do depurador visual studio
O Visual Studio inclui um depurador de código-fonte totalmente interativo, fornecendo uma ferramenta poderosa e fácil de usar para rastrear bugs em seu programa. O depurador tem suporte completo para Visual Basic, C#, C/C++ e JavaScript. No entanto, com o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], que está disponível no Microsoft Download [Center](https://www.microsoft.com/download/details.aspx?id=21835), outras linguagens de programação podem ser suportadas no depurador com os mesmos recursos ricos.

 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador é o front-end comum (ou seja, a interface do usuário) para os componentes de depuração que são, por sua vez, específicos para o idioma que está sendo depurado. Para novos idiomas, tudo o que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é necessário para o suporte do depurador é criar os componentes back-end necessários, como um mecanismo de depuração (DE). Este ponto é [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] onde o entra.

 O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] inclui uma referência [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] completa a todos os elementos necessários para criar um novo DE. Além disso, há amostras e tutoriais que ajudarão a começar.

 Para obter uma amostra completa de um sistema de projeto de linguagem com suporte à depuração, consulte a [amostra IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 As seções a seguir descrevem como estender [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]o depurador usando o .

## <a name="in-this-section"></a>Nesta seção
 [Comece](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Descreve o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que a Depuração oferece e como instalar o SDK.

 [Crie um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documenta o processo de DE personalizado, desde a preparação do seu programa para um DE até o desapego do DE.

 [Escreva um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Explica se você deve escrever um avaliador de expressão.

 [Escolha uma estratégia de implementação do mecanismo de depuração](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Discute como implementar seu DE.

 [Referência](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documenta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a API de depuração.

 [Amostras](../../extensibility/debugger/visual-studio-debugging-samples.md) Contém links para uma amostra avaliadora de expressão em tempo de execução comum e uma amostra de mecanismo de depuração.
