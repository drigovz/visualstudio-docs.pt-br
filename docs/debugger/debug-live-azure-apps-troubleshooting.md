---
title: Solucionar problemas de depuração de instantâneos | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27df4c097d829a4d28a77b9b1ad96eb389f4096c
ms.sourcegitcommit: dc12a7cb66124596089f01d3e939027ae562ede9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71962939"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Solução de problemas e problemas conhecidos da depuração de instantâneos no Visual Studio

Se as etapas descritas neste artigo não resolverem o problema, procure o problema na [comunidade de desenvolvedores](https://developercommunity.visualstudio.com/spaces/8/index.html) ou relate um novo problema escolhendo **ajuda** > **enviar comentários** > **relate um problema** no Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problema: "Attach Depurador de Instantâneos" encontra um erro de código de status HTTP

Se você vir o erro a seguir na janela de **saída** durante a tentativa de anexar, pode ser um problema conhecido listado abaixo. Experimente as soluções propostas e, se o problema continuar a persistir, entre em contato com o alias anterior.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) não autorizado

Esse erro indica que a chamada REST emitida pelo Visual Studio para o Azure usa uma credencial inválida. Um bug conhecido com o módulo fácil Azure Active Directory OAuth pode produzir esse erro.

Siga estas etapas:

* Certifique-se de que sua conta de personalização do Visual Studio tenha permissões para a assinatura do Azure e o recurso ao qual você está anexando. Uma maneira rápida de determinar isso é verificar se o recurso está disponível na caixa de diálogo de **Debug** > **Attach depurador de instantâneos...**  > **recurso do Azure** > **selecione existente**ou no Cloud Explorer.
* Se esse erro continuar a persistir, use um dos canais de comentários descritos no início deste artigo.

### <a name="403-forbidden"></a>(403) proibido

Esse erro indica que a permissão foi negada. Isso pode ser causado por muitos problemas diferentes.

Siga estas etapas:

* Verifique se sua conta do Visual Studio tem uma assinatura válida do Azure com as permissões de RBAC (controle de acesso baseado em função) necessárias para o recurso. Para AppService, verifique se você tem permissões para [consultar](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get) o plano do serviço de aplicativo que hospeda seu aplicativo.
* Verifique se o carimbo de data/hora do computador cliente está correto e atualizado. Os servidores com carimbos de data/hora em mais de 15 minutos do carimbo de hora da solicitação geralmente produzem esse erro.
* Se esse erro continuar a persistir, use um dos canais de comentários descritos no início deste artigo.

### <a name="404-not-found"></a>(404) não encontrado

Esse erro indica que o site não pôde ser encontrado no servidor.

Siga estas etapas:

* Verifique se você tem um site implantado e em execução no recurso de serviço de aplicativo ao qual você está anexando.
* Verifique se o site está disponível em https://@no__t -0resource\>.azurewebsites.net
* Verifique se o aplicativo Web personalizado em execução correta não retorna um código de status 404 quando acessado em https://@no__t -0resource\>.azurewebsites.net
* Se esse erro continuar a persistir, use um dos canais de comentários descritos no início deste artigo.

### <a name="406-not-acceptable"></a>(406) não aceitável

Esse erro indica que o servidor não pode responder ao tipo definido no cabeçalho Accept da solicitação.

Siga estas etapas:

* Verifique se seu site está disponível em https://@no__t -0resource\>.azurewebsites.net
* Verifique se o site não foi migrado para novas instâncias. Depurador de Instantâneos usa a noção de ARRAffinity para rotear solicitações para instâncias específicas que podem produzir esse erro intermitentemente.
* Se esse erro continuar a persistir, use um dos canais de comentários descritos no início deste artigo.

### <a name="409-conflict"></a>(409) conflito

Esse erro indica que a solicitação está em conflito com o estado atual do servidor.

Esse é um problema conhecido que ocorre quando um usuário tenta anexar Depurador de Instantâneos em um AppService que habilitou o ApplicationInsights. ApplicationInsights define as AppSettings com maiúsculas e minúsculas diferentes do Visual Studio, causando esse problema.

::: moniker range=">= vs-2019"
Resolvemos isso no Visual Studio 2019.
::: moniker-end

Siga estas etapas:

::: moniker range="vs-2017"

* Verifique na portal do Azure que AppSettings para SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) e InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) estão em maiúsculas. Caso contrário, atualize as configurações manualmente, o que força uma reinicialização do site.
::: moniker-end
* Se esse erro continuar a persistir, use um dos canais de comentários descritos no início deste artigo.

### <a name="500-internal-server-error"></a>(500) erro interno do servidor

Esse erro indica que o site está completamente inativo ou o servidor não pode manipular a solicitação. Depurador de Instantâneos só funciona em aplicativos em execução. [Application Insights depurador de instantâneos](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger) fornece instantâneos sobre exceções e pode ser a melhor ferramenta para suas necessidades.

### <a name="502-bad-gateway"></a>(502) gateway inadequado

Esse erro indica um problema de rede do lado do servidor e pode ser temporário.

Siga estas etapas:

* Tente aguardar alguns minutos antes de anexar o Depurador de Instantâneos novamente.
* Se esse erro continuar a persistir, use um dos canais de comentários descritos no início deste artigo.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: Snappoint não ativa

Se você vir um ícone de aviso ![ícone de aviso de snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "ícone de aviso de snappoint") com seu snappoint em vez de ver o ícone de snappoint regular, significa que o snappoint não está ativado.

![O snappoint não é ativado](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "O snappoint não é ativado")

Siga estas etapas:

1. Verifique se você tem a mesma versão do código-fonte que foi usada para criar e implantar seu aplicativo. Verifique se que você está carregando os símbolos corretos para sua implantação. Para isso, exiba a janela **Módulos** durante a depuração de instantâneos e verifique se a coluna Arquivo de Símbolos mostra um arquivo .pdb carregado para o módulo que você está depurando. O Depurador de Instantâneos tentará baixar automaticamente e usar os símbolos em sua implantação.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: Os símbolos não são carregados quando abro um instantâneo

Se você vir a janela a seguir, significa que os símbolos não foram carregados.

![Os símbolos não são carregados](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Os símbolos não são carregados")

Siga estas etapas:

- Clique em **Alterar Configurações de Símbolo…** nesta página. Nas configurações **Depuração > Símbolos**, adicione um diretório de cache de símbolos. Reinicie a depuração de instantâneos depois que o caminho de símbolos for definido.

   Os símbolos ou arquivos .pdb disponíveis em seu projeto devem corresponder à sua implantação do Serviço de Aplicativo. A maioria das implantações (implantação por meio do Visual Studio, CI/CD com Azure Pipelines ou Kudu etc.) publicará os arquivos de símbolos no seu Serviço de Aplicativo. A definição do diretório de cache de símbolos permite que o Visual Studio use esses símbolos.

   ![Configurações de símbolo](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Configurações de símbolo")

- Como alternativa, se sua organização usa um servidor de símbolos ou deixa os símbolos em um caminho diferente, use as configurações de símbolo para carregar os símbolos corretos para sua implantação.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: Não consigo ver a opção "Attach Depurador de Instantâneos" no Cloud Explorer

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

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: Vejo apenas instantâneos restritos no Ferramentas de Diagnóstico

![Snappoint limitado](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Snappoint limitado")

Siga estas etapas:

- Instantâneos ocupam pouca memória, mas têm um custo de confirmação. Se o Depurador de Instantâneos detectar que o servidor está sob carga pesada de memória, ele não fará a captura de instantâneos. Para excluir instantâneos já capturados, interrompa a sessão do Depurador de Instantâneos e tente novamente.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problema: A depuração de instantâneo com várias versões do Visual Studio me dá erros

O Visual Studio 2019 requer uma versão mais recente do Depurador de Instantâneos extensão de site em seu serviço de Azure App.  Esta versão não é compatível com a versão mais antiga do Depurador de Instantâneos a extensão de site usada pelo Visual Studio 2017.  Você receberá o erro a seguir se tentar anexar o Depurador de Instantâneos no Visual Studio 2019 a um serviço Azure App que foi previamente depurado pelo Depurador de Instantâneos no Visual Studio 2017:

![Incompatível depurador de instantâneos extensão do site do visual studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "incompatível depurador de instantâneos extensão do site Visual Studio 2019")

Por outro lado, se você usar o Visual Studio 2017 para anexar o Depurador de Instantâneos a um serviço de Azure App que foi previamente depurado pelo Depurador de Instantâneos no Visual Studio 2019, você obterá o seguinte erro:

![Incompatível depurador de instantâneos extensão do site do visual studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "incompatível depurador de instantâneos extensão do site Visual Studio 2017")

Para corrigir esse problema, exclua as seguintes configurações de aplicativo no portal do Azure e anexe o Depurador de Instantâneos novamente:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problema: Estou tendo problemas de depuração de instantâneo e preciso habilitar mais logs

### <a name="enable-agent-logs"></a>Habilitar logs de agente

Para habilitar e desabilitar o registro em log do agente em log, abra o Visual Studio, navegue até *Ferramentas > Opções > Depurador de instantâneos > Habilitar registro em log do agente*. Se *Excluir logs de agente antigos no início da sessão* também estiver habilitado, cada anexo bem-sucedido do Visual Studio excluirá os logs de agente anteriores.

Logs de agente podem ser encontrados nos seguintes locais:

- Serviços de Aplicativos:
  - Navegue até o site do Kudu do Serviço de Aplicativo (ou seja, seu serviçodeaplicativo.**scm**.azurewebsites.net) e vá até o Console de Depuração.
  - Os logs de agente são armazenados no seguinte diretório:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - Entre em sua VM, os logs de agente são armazenados da seguinte maneira:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Navegue até o diretório a seguir: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Habilitar logs de instrumentação/Profiler

Logs de instrumentação podem ser encontrados nos seguintes locais:

- Serviços de Aplicativos:
  - O log de erros é enviado automaticamente para o D:\Home\LogFiles\eventlog.xml, os eventos são marcados com `<Provider Name="Instrumentation Engine" />` ou "pontos de interrupção de produção"
- VM/VMSS:
  - Entre em sua VM e abra o Visualizador de Eventos.
  - Abra o seguinte modo de exibição: *Logs do Windows > aplicativo*.
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

- [Depurando no Visual Studio](../debugger/index.yml)
- [Depurar aplicativos ASP.NET ao vivo usando o Depurador de Instantâneos](../debugger/debug-live-azure-applications.md)
- [Depurar conjuntos de dimensionamento de máquinas Machines\Virtual virtuais do ASP.NET do Azure em tempo real usando o Depurador de Instantâneos](../debugger/debug-live-azure-virtual-machines.md)
- [Debug Live ASP.NET Azure kubernetes usando o Depurador de Instantâneos](../debugger/debug-live-azure-kubernetes.md)
- [Perguntas frequentes sobre depuração de instantâneos](../debugger/debug-live-azure-apps-faq.md)
