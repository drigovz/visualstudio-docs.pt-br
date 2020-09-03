---
title: Suporte ao serviço de linguagem para depuração | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c61f7fa7e698e2c01cadb1dbb36a321c6e656e35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194993"
---
# <a name="language-service-support-for-debugging"></a>Suporte do serviço de linguagem para depuração
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um serviço de linguagem pode fornecer recursos que dão suporte a um depurador por meio da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interface. Esses recursos incluem validação de pontos de interrupção e fornecimento de uma lista de expressões para a janela de **automóveis** .  
  
 No entanto, você precisa ter um avaliador de expressão para depurar seu idioma. O avaliador de expressão é responsável por avaliar expressões para produzir valores durante a depuração. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte:  
  
- [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
- [Exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Saída do compilador  
 O tipo de compilador determina o que você precisa fazer para implementar a depuração para seu idioma. Se o seu compilador tiver como alvo o sistema operacional Windows e gravar um arquivo. pdb, você poderá depurar programas com o mecanismo de depuração de código nativo integrado ao Visual Studio. Se o seu compilador produzir a MSIL (Microsoft Intermediate Language), você poderá depurar programas com o mecanismo de depuração de código gerenciado, que também é integrado ao Visual Studio. Se o seu compilador tiver como alvo um sistema operacional proprietário ou um ambiente de tempo de execução diferente, você precisará escrever seu próprio mecanismo de depuração.  
  
 Para obter mais informações sobre como implementar a depuração para seu idioma, consulte [introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) no SDK de depuração do Visual Studio.
