---
title: Suporte ao serviço de idiomas para depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707429"
---
# <a name="language-service-support-for-debugging"></a>Suporte do serviço de linguagem para depuração
Um serviço de idioma pode fornecer recursos <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> que suportam um depurador através da interface. Esses recursos incluem validar pontos de interrupção e fornecer uma lista de expressões para a janela **Autos.**

 No entanto, você precisa ter um avaliador de expressão para depurar seu idioma. O avaliador de expressão é responsável por avaliar expressões para produzir valores durante a depuração. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte:

- [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Amostra de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Saída do compilador
 O tipo de compilador determina o que você precisa fazer para implementar a depuração para o seu idioma. Se o compilador tiver como alvo o sistema operacional Windows e escrever um arquivo .pdb, você poderá depurar programas com o mecanismo nativo de depuração de código integrado ao Visual Studio. Se o seu compilador produzir linguagem intermediária Microsoft (MSIL), você pode depurar programas com o mecanismo de depuração de código gerenciado, que também é integrado ao Visual Studio. Se o compilador tiver como alvo um sistema operacional proprietário ou um ambiente de tempo de execução diferente, você precisa escrever seu próprio mecanismo de depuração.

 Para obter mais informações sobre como implementar a depuração para o seu idioma, consulte [Getting Started](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) no Visual Studio Debugging SDK.
