---
title: Depurando código gerenciado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
ms.assetid: fa3aff01-c271-4aa7-b5b1-def560471c84
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39076459f684aafce4e800ecad6341d120aac480
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691438"
---
# <a name="debugging-managed-code"></a>Depurando código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta seção aborda problemas e técnicas de depuração comuns para aplicativos gerenciados, ou aplicativos escritos em linguagens destinadas ao Common Language Runtime, como Visual Basic, C# e C++. As técnicas descritas aqui são técnicas de alto nível. Para obter mais informações, consulte [usando o depurador](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mensagens de diagnóstico na janela de Saída](../debugger/diagnostic-messages-in-the-output-window.md)  
 Descreve as classes <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>, com as quais você pode escrever mensagens de tempo de execução para a janela **Saída**. Essas classes incluem métodos de saída que permitem a saída de informações sem interromper a execução e a saída de informações que também interrompem a execução se uma condição especificada falhar.  
  
 [Asserções em código gerenciado](../debugger/assertions-in-managed-code.md)  
 Descreve asserções em código gerenciado, que testam condições que você especifica como argumentos para os métodos `Assert`. Além disso, este tópico fornece código de exemplo, informações sobre como usar os métodos de classe <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>, considerações sobre as versões de depuração e lançamento do código, efeitos colaterais, argumentos de declaração, personalização de comportamento de declaração e arquivos de configuração.  
  
 [Instruções Stop no Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
 Descreve a instrução `Stop`, que fornece uma alternativa para definir um ponto de interrupção. O código de exemplo também é fornecido, junto com comparações entre a instrução `Stop` e a instrução `End`, bem como a instrução `Stop` e `Assert`.  
  
 [Passo a passo: Depuração de um Windows Form](../debugger/walkthrough-debugging-a-windows-form.md)  
 Fornece instruções passo a passo para criar um Windows Form e depurar esse formulário. Um Windows Form, um componente padrão de um aplicativo gerenciado do Windows, é um dos aplicativos gerenciados mais comuns. Este passo a passo usa o Visual C # e o Visual Basic, mas as técnicas para criar um Windows Form com C++ geralmente são semelhantes.  
  
 [Depuração do método OnStart](../debugger/how-to-debug-the-onstart-method.md)  
 Fornece exemplos de código para permitir que você depure o método `OnStart` de um serviço gerenciado do Windows. Para depurar o método `OnStart` de um serviço do Windows, você deverá adicionar algumas linhas de código para simular o serviço.  
  
 [Depuração de modo misto](../debugger/debugging-mixed-mode-applications.md)  
 Discute aplicativos de modo misto de depuração. Isso significa qualquer aplicativo que combine código nativo com código gerenciado.  
  
 [Erro: Não é possível depurar porque um depurador de kernel está habilitado no sistema](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
 Descreve uma mensagem de erro que ocorre quando você tenta depurar o código gerenciado em um sistema [!INCLUDE[win7](../includes/win7-md.md)], [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)], [!INCLUDE[winxp](../includes/winxp-md.md)], [!INCLUDE[Win2kFamily](../includes/win2kfamily-md.md)] ou Windows NT que foi iniciado em modo de depuração.  
  
 [Otimização e depuração JIT](../debugger/jit-optimization-and-debugging.md)  
 Descreve os efeitos da otimização JIT na depuração.  
  
 [Depuração de LINQ e DLINQ](../debugger/debugging-linq.md)  
 Discute técnicas para depurar consultas LINQ.  
  
 [Passo a passo: Como depurar um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Descreve como usar as janelas de ferramentas de **Tarefas Paralelas** e **Pilhas Paralelas** para depurar um aplicativo paralelo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [IntelliTrace](../debugger/intellitrace.md)  
 Localizar os bugs mais rápido e de maneira mais fácil registrando o histórico de execução do seu aplicativo com IntelliTrace. Retroceda e avance pelos eventos e pelas chamadas registrados para examinar o estado do aplicativo nos pontos-chave em tempo. Depure seu código sem definir muitos pontos de interrupção ou reiniciar o aplicativo com tanta frequência. Exige o Visual Studio Ultimate.  
  
 [Rastreando e instrumentando aplicativos](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)  
 Descreve o rastreamento, uma maneira de monitorar a execução do aplicativo enquanto está em execução, e a instrumentação, que envolve a colocação de instruções de rastreamento em locais estratégicos em seu código. Este tópico também fornece links para uma introdução à instrumentação e ao rastreamento, alternâncias de rastreamento, ouvintes de rastreamento, código de rastreamento em um aplicativo, adição de instruções de rastreamento no código do aplicativo, e criando condicionalmente com <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>.  
  
 [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)  
 Descreve uma opção do vinculador que adiciona <xref:System.Diagnostics.DebuggableAttribute> ao código escrito com C++. Esse atributo é necessário para usar os recursos de depuração como, por exemplo, anexar com C++.  
  
 [Como depurar aplicativos de serviço do Windows](https://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2)  
 Fornece considerações para depurar aplicativos de serviço do Windows, incluindo configuração, anexação ao processo, depuração do código do método `OnStart` do serviço e o código no método principal, definindo pontos de interrupção e usando o Gerenciador de Controle de Serviços para iniciar, parar, pausar e retomar seu serviço.  
  
 [Depuração e criação de perfil](https://msdn.microsoft.com/library/4a04863e-2475-46f4-bc3f-3c11510c2a4b)  
 Discute a depuração de aplicativos do .NET Framework e os requisitos de configuração.  
  
 [Como depurar aplicativos de script e Web](../debugger/debugging-web-applications-and-script.md)  
 Descreve os problemas comuns de depuração e técnicas que você pode encontrar ao depurar aplicativos de script e Web.  
 Descrição de novos recursos de depuração adicionados nesta versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 [Como depurar a Página Inicial](../debugger/debugging-in-visual-studio.md)  
 Fornece links para as maiores seções de documentação de depuração. A informação inclui: novidades no depurador, configurações e preparação, pontos de interrupção, tratamentos de exceção, edição e continuação, depuração de código gerenciado, depuração de projetos do Visual C++, depuração de COM e ActiveX, depuração de DLLs, depuração de SQL e referências à interface do usuário.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Depurando Windows personalizado do Forms a controles em tempo de Design](https://msdn.microsoft.com/library/1fd83ccd-3798-42fc-85a3-6cba99467387)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)
