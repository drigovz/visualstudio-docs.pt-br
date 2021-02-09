---
title: Depurando código nativo | Microsoft Docs
description: Saiba mais sobre problemas comuns de depuração e técnicas de alto nível para aplicativos nativos no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 8f65cb1a373bdff95e068f78137edf5237ec2905
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872541"
---
# <a name="debugging-native-code"></a>Depurando código nativo
A seção aborda alguns problemas comuns de depuração e técnicas para aplicativos nativos. As técnicas abordadas nesta seção são de alto nível. Para obter a mecânica de uso do depurador do Visual Studio, consulte [primeira olhada no depurador](../debugger/debugger-feature-tour.md)).

## <a name="in-this-section"></a>Nesta seção
 [Como: depurar código otimizado](../debugger/how-to-debug-optimized-code.md) Fornece dicas para depurar código otimizado, especificamente, por que você deve depurar uma versão não otimizada do seu programa, configurações de otimização padrão para configurações de depuração e versão e dicas para localizar bugs que aparecem apenas em código otimizado (ativando a otimização em uma configuração de compilação de depuração).

 [DebugBreak e __debugbreak](../debugger/debugbreak-and-debugbreak.md) Descreve a função do Win32 `DebugBreak` e fornece um link para seu tópico de referência no Platform SDK. Também descreve o `__debugbreak` intrínseco.

 [Asserções de C/C++](../debugger/c-cpp-assertions.md) Discute instruções de asserção, como elas funcionam, os benefícios de usá-las (capturar erros lógicos, verificar os resultados de uma operação e testar condições de erro), sua interação com `_DEBUG` o e os tipos de asserções com suporte no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 [Como: depurar código de assembly embutido](../debugger/how-to-debug-inline-assembly-code.md) Fornece instruções curtas sobre como usar a janela de desmontagem para exibir as instruções do assembly e a janela de registros para exibir o conteúdo do registro e fornece links para tópicos relacionados a essas janelas.

 [Técnicas de depuração do MFC](../debugger/mfc-debugging-techniques.md) Vincula você à depuração de técnicas para programas MFC, incluindo: afxDebugBreak, a macro TRACE, detectar vazamentos de memória no MFC, asserções do MFC e reduzir o tamanho das compilações de depuração do MFC.

 [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md) Vincula você a técnicas de depuração para a biblioteca de Run-Time do C, incluindo o uso da biblioteca de depuração CRT, macros para relatórios, diferenças entre malloc e _malloc_dbg, gravação de funções de gancho de depuração e heap de depuração CRT.

 [Perguntas frequentes sobre depuração de código nativo](../debugger/debugging-native-code-faqs.md) Fornece respostas para perguntas frequentes sobre a depuração de programas em C++

 [Depuração com e ActiveX](../debugger/com-and-activex-debugging.md) Fornece informações sobre depuração de aplicativos COM e ActiveX, incluindo ferramentas que você pode usar para depuração COM e ActiveX.

 [Como: depurar código injetado](../debugger/how-to-debug-injected-code.md) Fornece orientação sobre o código de depuração que usa atributos. As instruções incluem como ativar a Anotação de Origem, como exibir o código injetado e como exibir o código de desmontagem no ponto de execução atual.

 [Walkthrough: Depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md) Descreve como usar as janelas de ferramentas de **tarefas paralelas** e de **pilhas paralelas** para depurar um aplicativo paralelo.

## <a name="related-sections"></a>Seções relacionadas
 [Preparar para depurar projetos C++](../debugger/debugging-preparation-visual-cpp-project-types.md) Fornece links para tópicos que descrevem como depurar os tipos de projeto nativos criados pelos modelos de projeto do C++.

 [Depuração de projetos de dll](../debugger/debugging-dll-projects.md) Fornece informações sobre como depurar DLLs nativas e gerenciadas.

 [Primeira olhada no depurador](../debugger/debugger-feature-tour.md) Fornece links para as seções maiores da documentação de depuração. A informação inclui: novidades no depurador, configurações e preparação, pontos de interrupção, tratamentos de exceção, edição e continuação, depuração de código gerenciado, depuração de código nativo, depuração de SQL e referências à interface do usuário.

## <a name="see-also"></a>Confira também

- [Segurança do depurador](../debugger/debugger-security.md)
- [Depurando no Visual Studio](../debugger/index.yml)