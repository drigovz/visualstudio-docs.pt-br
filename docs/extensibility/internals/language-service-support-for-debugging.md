---
title: Suporte ao serviço de linguagem para depuração | Microsoft Docs
description: Saiba mais sobre os recursos do serviço de linguagem na interface IVsLanguageDebugInfo que fornecem suporte para depuração no Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c17b11ce3639664a8097abeaa2a2de9a6faaadc7
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205158"
---
# <a name="language-service-support-for-debugging"></a>Suporte do serviço de linguagem para depuração
Um serviço de linguagem pode fornecer recursos que dão suporte a um depurador por meio da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interface. Esses recursos incluem validação de pontos de interrupção e fornecimento de uma lista de expressões para a janela de **automóveis** .

 No entanto, você precisa ter um avaliador de expressão para depurar seu idioma. O avaliador de expressão é responsável por avaliar expressões para produzir valores durante a depuração. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte:

- [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Saída do compilador
 O tipo de compilador determina o que você precisa fazer para implementar a depuração para seu idioma. Se o seu compilador tiver como alvo o sistema operacional Windows e gravar um arquivo. pdb, você poderá depurar programas com o mecanismo de depuração de código nativo integrado ao Visual Studio. Se o seu compilador produzir a MSIL (Microsoft Intermediate Language), você poderá depurar programas com o mecanismo de depuração de código gerenciado, que também é integrado ao Visual Studio. Se o seu compilador tiver como alvo um sistema operacional proprietário ou um ambiente de tempo de execução diferente, você precisará escrever seu próprio mecanismo de depuração.

 Para obter mais informações sobre como implementar a depuração para seu idioma, consulte [introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) no SDK de depuração do Visual Studio.
