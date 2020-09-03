---
title: Extensibilidade do depurador do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73983663"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidade do depurador do Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O Visual Studio inclui um depurador de código-fonte totalmente interativo, fornecendo uma ferramenta poderosa e fácil de usar para o rastreamento de bugs em seu programa. O depurador tem suporte completo Visual Basic, C#, C/C++ e JavaScript. No entanto, com o [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , que está disponível no [centro de download da Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), outras linguagens de programação podem ter suporte no depurador com os mesmos recursos avançados.  
  
 O [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurador é o front-end comum (ou seja, a interface do usuário) para os componentes de depuração que, por sua vez, são específicos do idioma que está sendo depurado. Para novos idiomas, tudo o que é necessário para o suporte pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurador é criar os componentes de back-end necessários, como um mecanismo de depuração (de). É aí que [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] entra o.  
  
 O [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] inclui uma referência completa a todos os [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] elementos necessários para criar um novo de. Além disso, há exemplos e tutoriais que ajudarão você a começar.  
  
 Para obter um exemplo de ponta a ponta de um sistema de projeto de linguagem com suporte para depuração, consulte o [exemplo de IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 As seções a seguir descrevem como estender o depurador usando o [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Descreve o que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a depuração oferece e como instalar o SDK.  
  
 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documenta o processo personalizado, de preparar seu programa para um DE para desanexar o DE.  
  
 [Escrevendo um avaliador de expressão do CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explica se você deve escrever um avaliador de expressão.  
  
 [Escolher uma estratégia de implementação do mecanismo de depuração](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Discute como implementar o DE.  
  
 [Referência](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documenta a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API de depuração.  
  
 [Amostras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contém links para um exemplo de avaliador de expressão Common Language Runtime e um exemplo de mecanismo de depuração.
