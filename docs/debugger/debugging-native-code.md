---
title: Depurando código nativo | Microsoft Docs
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 59811e522268b7a9cb3993add76d2ace8dc3aada
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685489"
---
# <a name="debugging-native-code"></a>Depurando código nativo
A seção aborda alguns problemas comuns de depuração e técnicas para aplicativos nativos. As técnicas abordadas nesta seção são de alto nível. Para conhecer a mecânica de como usar o depurador do Visual Studio, consulte [primeiro, examine o depurador](../debugger/debugger-feature-tour.md)).

## <a name="in-this-section"></a>Nesta seção
 [Como: depurar um código otimizado](../debugger/how-to-debug-optimized-code.md) dá dicas para depurar o código otimizado, especificamente, por que depurar uma versão não otimizada do programa, as configurações padrão de otimização para configurações de depuração e versão e dicas para localizar bugs que somente aparecer em código otimizado (ativação de otimização em uma configuração de build de depuração).

 [DebugBreak e debugbreak](../debugger/debugbreak-and-debugbreak.md) descreve o Win32 `DebugBreak` de função e fornece um link para seu tópico de referência no SDK da plataforma. Também descreve o `__debugbreak` intrínseco.

 [Asserções C/C++](../debugger/c-cpp-assertions.md) discute as instruções de declaração, como eles funcionam, os benefícios de usá-las (capturando erros lógicos, verificando resultados de uma operação e testando condições de erro), sua interação com `_DEBUG`e os tipos de asserções com suporte no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Como: depurar código Assembly embutido](../debugger/how-to-debug-inline-assembly-code.md) fornece instruções curtas sobre como usar a janela de desmontagem para exibir as instruções de assembly e a janela registros para exibir conteúdo do registro e fornece links para tópicos sobre essas janelas.

 [Técnicas de depuração MFC](../debugger/mfc-debugging-techniques.md) Links para técnicas de depuração para programas MFC, incluindo: afxDebugBreak, a macro TRACE, detecção de memória perdas no MFC, MFC, asserções e reduzindo o tamanho da depuração do MFC se baseia.

 [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md) Links para técnicas de depuração para a biblioteca de tempo de execução C, incluindo o uso da biblioteca de depuração do CRT, macros para relatórios, as diferenças entre malloc e malloc_dbg, escrevendo funções de gancho de depuração e o heap de depuração do CRT.

 [Perguntas frequentes de código nativo de depuração](../debugger/debugging-native-code-faqs.md) fornece respostas para perguntas frequentes sobre a depuração de programas do Visual C++

 [Depuração de COM e ActiveX](../debugger/com-and-activex-debugging.md) fornece informações sobre aplicativos COM e ActiveX, inclusive ferramentas que você pode usar para COM e ActiveX a depuração.

 [Como: depurar código injetado](../debugger/how-to-debug-injected-code.md) fornece orientação sobre como depurar código que usa atributos. As instruções incluem como ativar a Anotação de Origem, como exibir o código injetado e como exibir o código de desmontagem no ponto de execução atual.

 [Passo a passo: Depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md) descreve como usar o **tarefas paralelas** e **pilhas paralelas** janelas para depurar um aplicativo paralelo.

## <a name="related-sections"></a>Seções relacionadas
 [Tipos de projeto do Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md) fornece links para tópicos que descrevem como depurar os tipos de projeto nativos criados pelos modelos de projeto do Visual C++.

 [Depurando projetos de DLL](../debugger/debugging-dll-projects.md) fornece informações sobre como depurar DLLs nativas e gerenciadas.

 [Primeiro, examine o depurador](../debugger/debugger-feature-tour.md) fornece links para as maiores seções da documentação de depuração. A informação inclui: novidades no depurador, configurações e preparação, pontos de interrupção, tratamentos de exceção, edição e continuação, depuração de código gerenciado, depuração de código nativo, depuração de SQL e referências à interface do usuário.

## <a name="see-also"></a>Consulte também
 [Segurança do depurador](../debugger/debugger-security.md) [depuração no Visual Studio](../debugger/index.md)