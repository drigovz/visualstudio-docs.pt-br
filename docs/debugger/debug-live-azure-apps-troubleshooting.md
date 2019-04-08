---
title: Solucionar problemas de depuração de instantâneos | Microsoft Docs
ms.custom: seodec18
ms.date: 11/07/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b7916cbd3a7faa633baf53a18686779dc2b386c
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857756"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Solução de problemas e problemas conhecidos da depuração de instantâneos no Visual Studio

Se as etapas descritas neste artigo não resolverem seu problema, entre em contato com snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: o snappoint não é ativado

Se você vir um ícone de aviso ![ícone de aviso de snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "ícone de aviso de snappoint") com seu snappoint em vez de ver o ícone de snappoint regular, significa que o snappoint não está ativado.

![O snappoint não é ativado](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "O snappoint não é ativado")

Siga estas etapas:

1. Verifique se que você tem a mesma versão do código-fonte usada para criar e implantar seu app.isua1. Verifique se que você está carregando os símbolos corretos para sua implantação. Para isso, exiba a janela **Módulos** durante a depuração de instantâneos e verifique se a coluna Arquivo de Símbolos mostra um arquivo .pdb carregado para o módulo que você está depurando. O Depurador de Instantâneos tentará baixar automaticamente e usar os símbolos em sua implantação.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: os símbolos não são carregados quando eu abro um instantâneo

Se você vir a janela a seguir, significa que os símbolos não foram carregados.

![Os símbolos não são carregados](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Os símbolos não são carregados")

Siga estas etapas:

- Clique em **Alterar Configurações de Símbolo…** nesta página. Nas configurações **Depuração > Símbolos**, adicione um diretório de cache de símbolos. Reinicie a depuração de instantâneos depois que o caminho de símbolos for definido.

   Os símbolos ou arquivos .pdb disponíveis em seu projeto devem corresponder à sua implantação do Serviço de Aplicativo. A maioria das implantações (implantação por meio do Visual Studio, CI/CD com Azure Pipelines ou Kudu etc.) publicará os arquivos de símbolos no seu Serviço de Aplicativo. A definição do diretório de cache de símbolos permite que o Visual Studio use esses símbolos.

   ![Configurações de símbolo](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Configurações de símbolo")

- Como alternativa, se sua organização usa um servidor de símbolos ou deixa os símbolos em um caminho diferente, use as configurações de símbolo para carregar os símbolos corretos para sua implantação.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: não consigo ver a opção "Anexar Depurador de Instantâneos" no Cloud Explorer

Siga estas etapas:

- Verifique se o componente do Depurador de Instantâneos está instalado. Abra o Instalador do Visual Studio e marque o componente **Depurador de Instantâneos** na carga de trabalho do Azure.
::: moniker range="< vs-2019"
- Verifique se há suporte para o seu aplicativo. Atualmente, há suporte apenas para aplicativos ASP.NET (4.6.1+) e ASP.NET Core (2.0+) implementados nos Serviços de Aplicativos do Azure.
::: moniker-end
::: moniker range=">= vs-2019"
- Verifique se há suporte para o seu aplicativo:
  - Serviços de Aplicativos do Azure – Aplicativos ASP.NET em execução no .NET Framework 4.6.1 ou posterior.
  - Serviços de Aplicativos do Azure – Aplicativos ASP.NET Core em execução no .NET Core 2.0 ou posterior no Windows.
  - Máquinas Virtuais do Azure (e conjunto de dimensionamento de máquinas virtuais) – aplicativos ASP.NET em execução no .NET Framework 4.6.1 ou posterior.
  - Máquinas Virtuais do Azure (e conjunto de dimensionamento de máquinas virtuais) – aplicativos ASP.NET Core em execução no .NET Core 2.0 ou posterior no Windows.
  - Serviços de Kubernetes do Azure – Aplicativos ASP.NET Core em execução no .NET Core 2.2 ou posterior no Debian 9.
  - Serviços de Kubernetes do Azure – Aplicativos ASP.NET Core em execução no .NET Core 2.2 ou posterior no Alpine 3.8.
  - Serviços de Kubernetes do Azure – Aplicativos ASP.NET Core em execução no .NET Core 2.2 ou posterior no Ubuntu 18.04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: vejo apenas instantâneos limitados nas Ferramentas de Diagnóstico

![Snappoint limitado](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Snappoint limitado")

Siga estas etapas:

- Instantâneos ocupam pouca memória, mas têm um custo de confirmação. Se o Depurador de Instantâneos detectar que o servidor está sob carga pesada de memória, ele não fará a captura de instantâneos. Para excluir instantâneos já capturados, interrompa a sessão do Depurador de Instantâneos e tente novamente.

## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problema: a depuração de instantâneos com várias versões do Visual Studio apresenta erros

O VS 2019 requer uma versão mais recente da extensão de site do Depurador de Instantâneos no seu Serviço de Aplicativo do Azure.  Esta versão não é compatível com a versão mais antiga da extensão de site do Depurador de Instantâneos usada pelo VS 2017.  Se você tentar anexar o Depurador de Instantâneos no VS de 2019 para um Serviço de Aplicativos do Azure depurado anteriormente pelo Depurador de Instantâneos no VS 2017, verá o seguinte erro:

![Extensão de site do Depurador de Instantâneos incompatível no VS 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Extensão de site do Depurador de Instantâneos incompatível no VS 2019")

Por outro lado, se você usar o VS 2017 para anexar o Depurador de Instantâneos em um Serviço de Aplicativo do Azure depurado anteriormente pelo Depurador de Instantâneos no VS 2019, receberá o seguinte erro:

![Extensão de site do Depurador de Instantâneos incompatível no VS 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Extensão de site do Depurador de Instantâneos incompatível no VS 2017")

Para corrigir esse problema, exclua as seguintes configurações de aplicativo no portal do Azure e anexe o Depurador de Instantâneos novamente:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problema: estou com problemas para depurar instantâneos e preciso habilitar mais registro em log

### <a name="enable-agent-logs"></a>Habilitar logs de agente

Para habilitar e desabilitar o registro em log do agente em log, abra o Visual Studio, navegue até *Ferramentas > Opções > Depurador de instantâneos > Habilitar registro em log do agente*. Se *Excluir logs de agente antigos no início da sessão* também estiver habilitado, cada anexo bem-sucedido do Visual Studio excluirá os logs de agente anteriores.

Logs de agente podem ser encontrados nos seguintes locais:

- Serviços de Aplicativos:
  - Navegue até o site do Kudu do Serviço de Aplicativo (ou seja, seu serviçodeaplicativo.**scm**.azurewebsites.net) e vá até o Console de Depuração.
  - Os logs de agente são armazenados no seguinte diretório: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - Entre na sua VM; os logs de agente estão armazenados da seguinte maneira: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Navegue até o diretório a seguir: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Habilitar logs de instrumentação/Profiler

Logs de instrumentação podem ser encontrados nos seguintes locais:

- Serviços de Aplicativos:
  - Logs de erros são enviados automaticamente para D:\Home\LogFiles\eventlog.xml, eventos são marcados com <<Nome do provedor="Mecanismos de instrumentação" //>> ou "Pontos de interrupção de produção"
- VM/VMSS:
  - Entre em sua VM e abra o Visualizador de Eventos.
  - Abra a exibição a seguir: *Logs do Windows > Aplicativo*.
  - *Filtrar Log Atual* por *Origem do Evento* usando *Pontos de Interrupção de Produção* ou *Mecanismo de Instrumentação*.
- AKS
  - Logs de mecanismo de instrumentação em /tmp/diag/log.txt /tmp/diag/log.txt (defina MicrosoftInstrumentationEngine_FileLogPath no DockerFile)
  - Log de ponto de interrupção de produção em /tmp/diag/shLog.txt

## <a name="known-issues"></a>Problemas Conhecidos

- Atualmente, não há suporte para a depuração de instantâneos com vários clientes do Visual Studio no mesmo Serviço de Aplicativo.
- Otimizações Roslyn IL não têm suporte total em projetos ASP.NET Core. Para alguns projetos ASP.NET Core, talvez não seja possível ver algumas variáveis ou usar algumas variáveis em instruções condicionais.
- Variáveis especiais, como *$FUNCTION* ou *$CALLER*, não podem ser avaliadas em instruções condicionais ou logpoints para projetos ASP.NET Core.
- A depuração de instantâneos não funciona nos Serviços de Aplicativos com [Cache Local](/azure/app-service/app-service-local-cache) ativado.
- Atualmente, não há suporte para Aplicativos de API de depuração de instantâneos.

## <a name="site-extension-upgrade"></a>Atualização de extensão de site

A depuração de instantâneos e o Application Insights dependem de um ICorProfiler, que é carregado no processo do site e causa problemas de bloqueio de arquivo durante a atualização. Esse processo é recomendável para garantir que não haja tempo de inatividade em seu site de produção.

- Crie um [Slot de implantação](/azure/app-service/web-sites-staged-publishing) dentro de seu Serviço de Aplicativo e implante seu site no slot.
- Troque o Slot com a produção do Cloud Explorer no Visual Studio ou do portal do Azure.
- Interrompa o site do Slot. Levará alguns segundos para eliminar o processo de w3wp.exe do site de todas as instâncias.
- Atualize a extensão de site do Slot no site do Kudu ou no portal do Azure (*Folha de Serviço de Aplicativo > Ferramentas de Desenvolvimento > Extensões > Atualização*).
- Inicie o site do Slot. Recomendamos que você visite o site para aquecê-lo novamente.
- Troque o Slot com a produção.

## <a name="see-also"></a>Consulte também

- [Depurando no Visual Studio](../debugger/index.md)
- [Depurar aplicativos ASP.NET dinâmicos usando o Depurador de Instantâneos](../debugger/debug-live-azure-applications.md)
- [Depurar Máquinas Virtuais ASP.NET Azure\Conjuntos de Dimensionamento de VMs dinâmicos usando o Depurador de Instantâneos](../debugger/debug-live-azure-virtual-machines.md)
- [Depurar Kubernetes ASP.NET dinâmicos usando o Depurador de Instantâneos](../debugger/debug-live-azure-kubernetes.md)
- [Perguntas frequentes sobre depuração de instantâneo](../debugger/debug-live-azure-apps-faq.md)