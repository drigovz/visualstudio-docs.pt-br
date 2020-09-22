---
title: Gerenciando o carregamento de projetos em uma solução | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838320"
---
# <a name="managing-project-loading-in-a-solution"></a>Gerenciando o carregamento de projeto em uma solução
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As soluções do Visual Studio podem conter um grande número de projetos. O comportamento padrão do Visual Studio é carregar todos os projetos em uma solução no momento em que a solução é aberta e não permitir que o usuário acesse qualquer um dos projetos até que todos tenham terminado o carregamento. Quando o processo de carregamento do projeto durar mais de dois minutos, será exibida uma barra de progresso mostrando o número de projetos carregados e o número total de projetos. O usuário pode descarregar projetos enquanto trabalha em uma solução com vários projetos, mas esse procedimento tem algumas desvantagens: os projetos descarregados não são criados como parte de um comando de solução de recompilação, e as descrições do IntelliSense de tipos e membros de projetos fechados não são exibidas.  
  
 Os desenvolvedores podem reduzir os tempos de carregamento da solução e gerenciar o comportamento de carregamento do projeto criando um Gerenciador de carga de solução. O Gerenciador de carga de solução pode definir prioridades de carregamento de projeto diferentes para projetos específicos ou tipos de projeto, garantir que os projetos sejam carregados antes de iniciar uma compilação em segundo plano, atrasar o carregamento em segundo plano até que outras tarefas em segundo plano sejam concluídas e executar outras tarefas de gerenciamento de carga do projeto.  
  
## <a name="project-loading-priorities"></a>Prioridades de carregamento do projeto  
 O Visual Studio define quatro prioridades de carregamento de projeto diferentes:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (o padrão): quando uma solução é aberta, os projetos são carregados de forma assíncrona. Se essa prioridade for definida em um projeto descarregado depois que a solução já estiver aberta, o projeto será carregado no próximo ponto ocioso.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: quando uma solução é aberta, os projetos são carregados em segundo plano, permitindo que o usuário acesse os projetos conforme eles são carregados sem precisar aguardar até que todos os projetos sejam carregados.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: os projetos são carregados quando são acessados. Um projeto é acessado quando o usuário expande o nó do projeto no Gerenciador de Soluções, quando um arquivo pertencente ao projeto é aberto quando a solução é aberta porque está na lista de documentos abertos (persistido no arquivo de opções do usuário da solução) ou quando outro projeto que está sendo carregado tem uma dependência no projeto. Esse tipo de projeto não é carregado automaticamente antes de iniciar um processo de compilação; o Gerenciador de carga de solução é responsável por garantir que todos os projetos necessários sejam carregados. Esses projetos também devem ser carregados antes de iniciar uma localização/substituição nos arquivos em toda a solução.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: os projetos não devem ser carregados, a menos que o usuário o solicite explicitamente. Esse é o caso quando os projetos são explicitamente descarregados.  
  
## <a name="creating-a-solution-load-manager"></a>Criando um Gerenciador de carga de solução  
 Os desenvolvedores podem criar um Gerenciador de carga de solução implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e aconselhando o Visual Studio de que o Gerenciador de carga de solução está ativo.  
  
#### <a name="activating-a-solution-load-manager"></a>Ativando um Gerenciador de carga de solução  
 O Visual Studio permite apenas um Gerenciador de carga de solução em um determinado momento, portanto, você deve aconselhar o Visual Studio quando desejar ativar o Gerenciador de carga de solução. Se um segundo Gerenciador de carga de solução for ativado posteriormente, o Gerenciador de carga de solução será desconectado.  
  
 Você deve obter o <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> serviço e definir a <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Propriedade:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementando IVsSolutionLoadManager  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> método é chamado durante o processo de abertura da solução. Para implementar esse método, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> serviço para definir a prioridade de carga para o tipo de projeto que você deseja gerenciar. Por exemplo, o código a seguir define tipos de projeto C# para carregar em segundo plano:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> método é chamado quando o Visual Studio está sendo desligado ou quando um pacote diferente assumiu o como o Gerenciador de carga de solução ativo chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> com a <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propriedade.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estratégias para diferentes tipos de Gerenciador de carga de solução  
 Você pode implementar gerenciadores de carga de solução de maneiras diferentes, dependendo dos tipos de soluções que eles devem gerenciar.  
  
 Se o Gerenciador de carga de solução pretende gerenciar o carregamento da solução em geral, ele pode ser implementado como parte de um VSPackage. O pacote deve ser definido como AutoLoad adicionando o <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> no VSPackage com um valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . O Gerenciador de carga de solução pode ser ativado no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
> [!NOTE]
> Para obter mais informações sobre o carregamento automático de pacotes, consulte [carregando VSPackages](../extensibility/loading-vspackages.md).  
  
 Como o Visual Studio reconhece apenas o último Gerenciador de carga de solução a ser ativado, os gerentes de carga de solução geral devem sempre detectar se há um Gerenciador de carga existente antes da ativação. Se chamar GetProperty () no serviço de solução para <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> retornar `null` , não haverá nenhum Gerenciador de carga de solução ativo. Se não retornar NULL, verifique se o objeto é o mesmo que o seu Gerenciador de carga de solução.  
  
 Se o Gerenciador de carga de solução pretende gerenciar apenas alguns tipos de solução, o VSPackage pode assinar eventos de carga de solução (chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) e usar o manipulador de eventos para <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> ativar o Gerenciador de carga de solução.  
  
 Se o Gerenciador de carga de solução pretende gerenciar apenas soluções específicas, as informações de ativação podem persistir como parte do arquivo de solução. Para fazer isso, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> a seção de pré-solução.  
  
 Os gerenciadores de carga de solução específicos devem ser desativados no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> manipulador de eventos, a fim de não entrar em conflito com outros gerenciadores de carga de solução.  
  
 Se você precisar de um Gerenciador de carga de solução apenas para persistir as prioridades de carregamento do projeto global (por exemplo, propriedades definidas em uma página de opções), você pode ativar o Gerenciador de carga da solução no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> manipulador de eventos, persistir a configuração nas propriedades da solução e desativar o Gerenciador de carga da solução.  
  
## <a name="handling-solution-load-events"></a>Manipulando eventos de carga de solução  
 Para assinar eventos de carga de solução, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando você ativar seu Gerenciador de carga de solução. Se você implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , poderá responder a eventos relacionados a prioridades de carregamento de projeto diferentes.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Isso é acionado antes de uma solução ser aberta. Você pode usá-lo para alterar a prioridade de carregamento do projeto para os projetos na solução.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Isso é acionado após a solução ser completamente carregada, mas antes do carregamento do projeto em segundo plano começar novamente. Por exemplo, um usuário pode ter acessado um projeto cuja prioridade de carregamento é LoadIfNeeded ou o Gerenciador de carga de solução pode ter alterado uma prioridade de carregamento do projeto para BackgroundLoad, o que iniciaria uma carga em segundo plano desse projeto.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Isso é disparado depois que uma solução é inicialmente carregada totalmente, independentemente de existir ou não um Gerenciador de carregamento de solução. Ele também é acionado após carga em segundo plano ou carga de demanda sempre que a solução é totalmente carregada. Ao mesmo tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> é reativada.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Isso é acionado antes do carregamento de um projeto (ou projetos). Para garantir que outros processos em segundo plano sejam concluídos antes de os projetos serem carregados, defina `pfShouldDelayLoadToNextIdle` como **true**.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Isso é acionado quando um lote de projetos está prestes a ser carregado. Se `fIsBackgroundIdleBatch` for true, os projetos serão carregados em segundo plano; se `fIsBackgroundIdleBatch` for false, os projetos serão carregados de forma síncrona como resultado de uma solicitação de usuário, por exemplo, se o usuário expandir um projeto pendente no Gerenciador de soluções. Você pode implementar isso para fazer um trabalho caro que, caso contrário, precisaria ser feito no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Isso é acionado após o carregamento de um lote de projetos.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Detectando e gerenciando a solução e o carregamento do projeto  
 Para detectar o estado de carga de projetos e soluções, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> com os seguintes valores:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se a solução e todos os seus projetos são carregados, caso contrário `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se um lote de projetos estiver sendo carregado em segundo plano no momento, caso contrário `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` retorna `true` se um lote de projetos está sendo carregado de forma síncrona como resultado de um comando de usuário ou outra carga explícita, caso contrário `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` retorna `true` se a solução está sendo fechada no momento, caso contrário `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` retorna `true` se uma solução está sendo aberta no momento; caso contrário, `false` .  
  
  Você também pode garantir que projetos e soluções sejam carregados (não importa quais são as prioridades de carga do projeto) chamando um dos seguintes métodos:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: chamar esse método força os projetos em uma solução a serem carregados antes que o método seja retornado.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: chamar esse método força os projetos `guidProject` a serem carregados antes que o método retorne.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: chamar esse método força o projeto a `guidProjectID` carregar antes que o método retorne.  
  
> [!NOTE]
> . Por padrão, somente os projetos que têm a carga de demanda e as prioridades de carga em segundo plano são carregados, mas se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> sinalizador for passado para o método, todos os projetos serão carregados, exceto aqueles marcados para serem carregados explicitamente.
