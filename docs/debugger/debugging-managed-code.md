---
title: Depurando código gerenciado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 14dc53413f646718b85ec9ea43d968dc9f64a96f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719308"
---
# <a name="debugging-managed-code"></a>Depurando código gerenciado

Esta seção aborda problemas e técnicas de depuração comuns para aplicativos gerenciados, ou aplicativos escritos em linguagens destinadas ao Common Language Runtime, como Visual Basic, C# e C++. As técnicas descritas aqui são técnicas de alto nível. [Introdução ao depurador](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>Nesta seção

[Mensagens de diagnóstico na janela de saída](../debugger/diagnostic-messages-in-the-output-window.md) descreve o <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> classes, com a qual você pode gravar mensagens de tempo de execução para o **saída** janela. Essas classes incluem métodos de saída que permitem a saída de informações sem interromper a execução e a saída de informações que também interrompem a execução se uma condição especificada falhar.

[Asserções em código gerenciado](../debugger/assertions-in-managed-code.md) descreve asserções em código gerenciado, que testam condições que você especifica como argumentos para `Assert` métodos. Além disso, este tópico fornece código de exemplo, informações sobre como usar os métodos de classe <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>, considerações sobre as versões de depuração e lançamento do código, efeitos colaterais, argumentos de declaração, personalização de comportamento de declaração e arquivos de configuração.

[Instruções Stop no Visual Basic](../debugger/stop-statements-in-visual-basic.md) descreve o `Stop` instrução, que fornece uma alternativa para definir um ponto de interrupção. O código de exemplo também é fornecido, junto com comparações entre a instrução `Stop` e a instrução `End`, bem como a instrução `Stop` e `Assert`.

[Passo a passo: Depurando um formulário do Windows](../debugger/walkthrough-debugging-a-windows-form.md) fornece instruções passo a passo para criar um Windows Form e depurar esse formulário. Um Windows Form, um componente padrão de um aplicativo gerenciado do Windows, é um dos aplicativos gerenciados mais comuns. Este passo a passo usa o Visual C # e o Visual Basic, mas as técnicas para criar um Windows Form com C++ geralmente são semelhantes.

[Depuração do método OnStart](../debugger/how-to-debug-the-onstart-method.md) fornece exemplos de código para permitir que você depure o `OnStart` método de um serviço Windows gerenciado. Para depurar o método `OnStart` de um serviço do Windows, você deverá adicionar algumas linhas de código para simular o serviço.

[Depuração de modo misto](../debugger/debugging-mixed-mode-applications.md) aborda a depuração de aplicativos de modo misto. Isso significa qualquer aplicativo que combine código nativo com código gerenciado.

[Erro: Não é possível depurar porque um depurador de kernel está habilitado no sistema](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md) descreve uma mensagem de erro que ocorre se você tentar depurar código gerenciado em um [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], ou Windows NT system que foi iniciado no modo de depuração.

[A otimização JIT e depuração](../debugger/jit-optimization-and-debugging.md) descreve os efeitos da otimização JIT na depuração.

[Depuração LINQ e DLINQ&lt;1}](../debugger/debugging-linq.md) discute técnicas para depurar consultas LINQ.

[Passo a passo: Depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md) descreve como usar o **tarefas paralelas** e **pilhas paralelas** janelas para depurar um aplicativo paralelo.

## <a name="related-sections"></a>Seções relacionadas

[IntelliTrace](../debugger/intellitrace.md) encontrar bugs mais rápidos e fácil, gravando o histórico de execução do seu aplicativo com o IntelliTrace. Retroceda e avance pelos eventos e pelas chamadas registrados para examinar o estado do aplicativo nos pontos-chave em tempo. Depure seu código sem definir muitos pontos de interrupção ou reiniciar o aplicativo com tanta frequência. Requer o Visual Studio Enterprise.

[Rastreamento e instrumentação de aplicativos](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications) descreve rastreamento, uma maneira para que você possa monitorar a execução do seu aplicativo enquanto ele está em execução e a instrumentação, que envolve colocar instruções de rastreamento em locais estratégicos no seu código. Este tópico também fornece links para uma introdução à instrumentação e ao rastreamento, alternâncias de rastreamento, ouvintes de rastreamento, código de rastreamento em um aplicativo, adição de instruções de rastreamento no código do aplicativo, e criando condicionalmente com <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) descreve uma opção de vinculador que adiciona <xref:System.Diagnostics.DebuggableAttribute> ao código escrito com C++. Esse atributo é necessário para usar os recursos de depuração como, por exemplo, anexar com C++.

[Depuração de aplicativos de serviço do Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) fornece considerações sobre a depuração de aplicativos de serviço do Windows, incluindo a configuração, anexação ao processo, depurar o código em que o serviço `OnStart` método e o código no principal método, definindo pontos de interrupção e usando o Gerenciador de controle de serviços para iniciar, pararem, pausam e continuam seu serviço.

[Depuração e criação de perfil](/dotnet/framework/debug-trace-profile/index) aborda os requisitos de configuração e depuração de aplicativos do .NET Framework.

[Depuração de scripts e aplicativos da Web](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications) descreve comuns de depuração de problemas e técnicas que você pode encontrar ao depurar aplicativos Web e script.

[O que há de novo no depurador no Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md) descrição dos novos recursos adicionados nesta versão de depuração [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Depurar página inicial](../debugger/debugger-feature-tour.md) fornece links para as maiores seções da documentação de depuração. A informação inclui: novidades no depurador, configurações e preparação, pontos de interrupção, tratamentos de exceção, edição e continuação, depuração de código gerenciado, depuração de projetos do Visual C++, depuração de COM e ActiveX, depuração de DLLs, depuração de SQL e referências à interface do usuário.

## <a name="see-also"></a>Consulte também

[Passo a passo: Depurando Windows personalizado do Forms a controles em tempo de Design](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[segurança do depurador](../debugger/debugger-security.md)
[depuração no Visual Studio](../debugger/index.md) 
 [ Primeiro, examine o depurador](../debugger/debugger-feature-tour.md)