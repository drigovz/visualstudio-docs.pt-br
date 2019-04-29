---
title: Suporte do serviço de linguagem para depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b42e11974a0522b8f4a6553c5606197915617d38
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860066"
---
# <a name="language-service-support-for-debugging"></a>Suporte do serviço de linguagem para depuração
Um serviço de linguagem pode fornecer recursos que dão suporte a um depurador por meio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interface. Esses recursos incluem a validação de pontos de interrupção e fornecendo uma lista de expressões para o **automóveis** janela.

 No entanto, você precisa ter um avaliador de expressão para depurar seu idioma. O avaliador de expressão é responsável por avaliar expressões para produzir valores durante a depuração. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte:

- [Avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Saída do compilador
 O tipo do compilador determina o que você precisa fazer para implementar a depuração para seu idioma. Se o compilador direciona o sistema operacional Windows e grava um arquivo. PDB, você pode depurar programas com o mecanismo que é integrado ao Visual Studio de depuração de código nativo. Se o compilador produz Microsoft intermediate language (MSIL), você pode depurar programas com o código gerenciado, depuração engine, que também é integrado ao Visual Studio. Se seu compilador se destina a um sistema operacional proprietário ou um ambiente de tempo de execução diferente, você precisa escrever seu próprio mecanismo de depuração.

 Para obter mais informações sobre a implementação de depuração para seu idioma, consulte [guia de Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) no SDK do Visual Studio de depuração.