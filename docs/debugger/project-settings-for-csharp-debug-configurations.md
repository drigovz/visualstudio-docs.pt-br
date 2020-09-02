---
title: Configurações de projeto para uma configuração de depuração em C# | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5108e195e5df245c72436752316e8ee91781e7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62903951"
---
# <a name="project-settings-for--c-debug-configurations"></a>Configurações do projeto para configurações de depuração do C#

Você pode alterar as configurações de depuração do projeto C# na [guia Depurar](#debug-tab) e na [guia compilar](#build-tab) das páginas de propriedades do projeto.

Para abrir as páginas de propriedades, selecione o projeto no **Gerenciador de soluções** e, em seguida, selecione o ícone **Propriedades** ou clique com o botão direito do mouse no projeto e selecione **Propriedades**.

Para obter mais informações, consulte [debug and Release Configurations](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Essas configurações não se aplicam aos aplicativos .NET Core, ASP.NET ou UWP. Para definir configurações de depuração para aplicativos UWP, consulte [iniciar uma sessão de depuração para um aplicativo UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Guia Depurar

|Configuração|Descrição|
|-------------------------------------| - |
| **Configuração** | Define o modo para compilar o aplicativo. Selecione **ativo (depuração)**, **depurar**, **liberar**ou **todas as configurações** na lista suspensa. |
| **Iniciar ação** | Especifica a ação quando você seleciona **Iniciar** em uma configuração de depuração.<br />- **Iniciar projeto** é o padrão e inicia o projeto de inicialização para depuração. Para obter mais informações, consulte [escolher o projeto de inicialização](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Iniciar programa externo** inicia e anexa a um aplicativo que não faz parte de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto. Para obter mais informações, consulte [anexar a processos em execução com o depurador](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Iniciar navegador com URL** permite depurar um aplicativo Web. |
| **Opções**  >  de inicialização **Argumentos de linha de comando** | Especifica argumentos de linha de comando para o aplicativo que está sendo depurado. O nome do comando é o nome do aplicativo especificado em **Iniciar programa externo**. |
| **Opções**  >  de inicialização **Diretório de trabalho** | Especifica o diretório de trabalho do aplicativo que está sendo depurado. No C#, o diretório de trabalho é *\bin\Debug* por padrão.
| **Opções**  >  de inicialização **Usar computador remoto**|Para depuração remota, selecione essa opção e insira o nome do destino de depuração remota ou um [nome de servidor Msvsmon](../debugger/remote-debugging.md). <br />O local de um aplicativo no computador remoto é especificado pela propriedade **caminho de saída** na guia **Compilar** . O local deve ser um diretório compartilhável no computador remoto.
| **Mecanismo**  >  do depurador **Habilitar depuração de código não gerenciado** | Debugs chama o código nativo (não gerenciado) do Win32 do aplicativo gerenciado. |
| **Mecanismo**  >  do depurador **Habilitar depuração de SQL Server** | Debugs SQL Server objetos de banco de dados. |

## <a name="build-tab"></a>Guia Compilação

|Configuração|Descrição|
|-------------|-----------------|
|**Geral**  >  **Símbolos de compilação condicional**|Defina as constantes de depuração e rastreamento, se selecionado.<br /><br /> Essas constantes habilitam a compilação condicional da [Classe Debug](/dotnet/api/system.diagnostics.debug) e da [Classe Trace](/dotnet/api/system.diagnostics.trace). Com essas constantes definidas, os métodos da classe Debug e Trace geram saída para a [Janela de Saída](../ide/reference/output-window.md). Sem essas constantes, os métodos da classe Debug e Trace não são compilados e nenhuma saída será gerada.<br /><br />Normalmente, a depuração é definida na versão de depuração de uma compilação e indefinida na versão de lançamento. O rastreamento é definido nas versões de depuração e de lançamento.|
|**Geral**  >  **Otimizar código**|A menos que um bug apareça apenas em código otimizado, deixe essa configuração desmarcada para compilações de depuração. O código otimizado é mais difícil de depurar, pois as instruções não correspondem diretamente às instruções no código-fonte.|
|**Saída**  >  do **Caminho de saída**|Normalmente definido como *bin\Debug* para depuração.|
|Botão **avançado**|Para obter informações sobre opções de depuração avançadas, consulte [caixa de diálogo Configurações avançadas de compilação (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). O formato portátil para arquivos de símbolo (*. pdb*) é um formato de plataforma cruzada recente para aplicativos .NET Core.

## <a name="see-also"></a>Confira também
- [Configurações e preparação do depurador](../debugger/debugger-settings-and-preparation.md)