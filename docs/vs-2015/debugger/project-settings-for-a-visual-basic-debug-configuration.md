---
title: Configurações do projeto para uma configuração de depuração do Visual Basic | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75d45f4aacad052d587950e5656dd74f153eba21
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446149"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Definições do projeto para uma configuração de depuração do Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode alterar as configurações do projeto para uma configuração de depuração do [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] na janela **Páginas de Propriedades**, conforme discutido em [Configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md). As tabelas a seguir mostram onde localizar as configurações relacionadas ao depurador na janela **Páginas de Propriedades**.  
  
> [!WARNING]
> Este tópico não se aplica a aplicativos da Store. Consulte [iniciar uma sessão de depuração (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Guia Depurar  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|**Configuração**|Define o modo para compilar o aplicativo. Escolha entre **Ativo (depuração)**, **Depuração**, **Versão**, **Todas as Configurações**.|  
|**Iniciar ação**|Esse grupo de controles especifica a ação que ocorrerá quando você escolhe Iniciar do menu Depurar.<br /><br /> -   **Iniciar projeto** é o padrão e inicia o projeto de inicialização da depuração. Para obter mais informações, consulte [NIB como: Definir projetos de inicialização](http://msdn.microsoft.com/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Iniciar programa externo** permite que você inicie e anexe a um programa que não faz parte de um projeto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Iniciar navegador na URL** permite que você depure um aplicativo Web.|  
|**Argumentos de linha de comando**|Especifica argumentos de linha de comando para o programa ser depurado. O nome do comando é o nome do programa especificado em Iniciar programa externo. Se Iniciar Ação for definida para iniciar URL, os argumentos de linha de comando serão ignorados.|  
|**Diretório de Trabalho**|Especifica o diretório de trabalho do programa que está sendo depurado. No [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], o diretório de trabalho é o diretório a partir do qual o aplicativo é iniciado. O diretório de trabalho padrão é \bin\Debug ou \bin\Release, dependendo da configuração atual.|  
|**Usar computador remoto**|Quando a caixa de seleção está marcada, a depuração remota é habilitada. Na caixa de texto, digite o nome de um computador remoto no qual o aplicativo será executado para fins de depuração ou um [Nome do servidor Msvsmon](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). O local do EXE no computador remoto é especificado pela propriedade Caminho da Saída na guia Build. O local deve ser um diretório compartilhável no computador remoto.|  
|**Depuração de código não gerenciado**|Permite depurar chamadas para código Win32 nativo (não gerenciado) a partir do seu aplicativo gerenciado. Isso tem o mesmo efeito que selecionar Misto como Tipo de Depurador em um projeto do [!INCLUDE[vcprvc](../includes/vcprvc-md.md)].|  
|**Depuração do SQL Server**|Permite depuração de objetos de banco de dados do SQL Server.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Guia Compilar: pressione o botão Opções de Compilação Avançadas  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|**Habilitar otimizações**|Essa opção deve estar desmarcada. A otimização faz o código que é realmente executado ser diferente do código-fonte visto no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e, portanto, dificulta a depuração. Se o código estiver otimizado, os símbolos não serão carregados por padrão ao depurar com Apenas Meu Código.|  
|**Gerar informações de depuração**|Definida por padrão nas versões de depuração e lançamento, essa configuração (equivalente à opção /debug do compilador) cria informações de depuração em tempo de compilação. O depurador usa essas informações para mostrar nomes de variável e outras informações em um formato útil quando você estiver depurando. Se você compilar seu programa sem essas informações, a funcionalidade do depurador será limitada. Para obter mais informações, confira [/debug](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|**Definir a constante DEBUG**|A definição desse símbolo permite compilar de forma condicional as funções de saída da [classe Debug](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx). Com esse símbolo definido, os métodos da classe Debug geram saída para a [janela de saída](../ide/reference/output-window.md). Sem esse símbolo, os métodos da classe de depuração não são compilados e nenhuma saída será gerada. Esse símbolo deve ser definido na versão de depuração e não na versão de lançamento. Definir esse símbolo em uma versão de lançamento cria código desnecessário que deixa a execução do seu programa mais lenta.|  
|**Definir a constante TRACE**|Definir esse símbolo permite compilar de forma condicional as funções de saída da [classe Trace](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Com esse símbolo definido, os métodos da classe Trace geram saída para a [janela de saída](../ide/reference/output-window.md). Sem esse símbolo, os métodos da classe de rastreamento não são compilados e nenhuma saída de rastreamento será gerada. Esse símbolo é definido por padrão para as versões de depuração e lançamento.|  
  
## <a name="see-also"></a>Consulte também  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)
