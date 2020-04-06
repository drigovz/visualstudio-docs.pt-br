---
title: Gerenciando o carregamento de projetos em uma solução | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702728"
---
# <a name="manage-project-loading-in-a-solution"></a>Gerenciar o carregamento de projetos em uma solução
As soluções do Visual Studio podem conter um grande número de projetos. O comportamento padrão do Visual Studio é carregar todos os projetos em uma solução no momento em que a solução é aberta, e não permitir que o usuário acesse qualquer um dos projetos até que todos eles tenham terminado o carregamento. Quando o processo de carregamento do projeto durará mais de dois minutos, uma barra de progresso é exibida mostrando o número de projetos carregados e o número total de projetos. O usuário pode descarregar projetos enquanto trabalha em uma solução com vários projetos, mas esse procedimento tem algumas desvantagens: os projetos descarregados não são construídos como parte de um comando Rebuild Solution, e as descrições do IntelliSense de tipos e membros de projetos fechados não são exibidas.

 Os desenvolvedores podem reduzir os tempos de carga da solução e gerenciar o comportamento de carregamento de projetos criando um gerenciador de carga de solução. O gerenciador de carga de soluções pode garantir que os projetos sejam carregados antes de iniciar uma compilação em segundo plano, atrasar o carregamento em segundo plano até que outras tarefas em segundo plano sejam concluídas e executar outras tarefas de gerenciamento de carga de projeto.

## <a name="create-a-solution-load-manager"></a>Crie um gerenciador de carga de soluções
 Os desenvolvedores podem criar um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> gerenciador de carga de soluções implementando e aconselhando o Visual Studio de que o gerenciador de carga de soluções está ativo.

### <a name="activate-a-solution-load-manager"></a>Ativar um gerenciador de carga de solução
 O Visual Studio permite apenas um gerenciador de carga de soluções em um determinado momento, então você deve aconselhar o Visual Studio quando quiser ativar o gerenciador de carga de soluções. Se um segundo gerenciador de carga de solução for ativado mais tarde, o gerenciador de carga da solução será desconectado.

 Você deve <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> obter o serviço e definir o [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) propriedade:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> método é chamado quando o Visual Studio está sendo desligado ou quando um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> pacote diferente assumiu como o gerenciador de carga de solução ativo ligando com o [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) propriedade.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estratégias para diferentes tipos de gerenciador de carga de soluções
 Você pode implementar os gerenciadores de carga de soluções de diferentes maneiras, dependendo dos tipos de soluções que eles estão destinados a gerenciar.

 Se o gerenciador de carga de solução for destinado a gerenciar o carregamento de soluções em geral, ele poderá ser implementado como parte de um VSPackage. O pacote deve ser configurado <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> para carregar automaticamente adicionando <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>o no VSPackage com um valor de . O gerenciador de carga de <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> solução pode então ser ativado no método.

> [!NOTE]
> Para obter mais informações sobre pacotes de carregamento automático, consulte [Loading VSPackages](../extensibility/loading-vspackages.md).

 Como o Visual Studio reconhece apenas o último gerenciador de carga de soluções a ser ativado, os gerentes gerais de carga de soluções devem sempre detectar se existe um gerenciador de carga existente antes de se ativarem. Se `GetProperty()` chamar o serviço de solução para [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null`retornos, não há um gerenciador de carga de solução ativo. Se ele não retornar nulo, verifique se o objeto é o mesmo que o gerenciador de carga da solução.

 Se o gerenciador de carga de solução for destinado a gerenciar apenas alguns <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>tipos de solução, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> o VSPackage poderá se inscrever em eventos de carga de solução (ligando), e usar o manipulador de eventos para ativar o gerenciador de carga de soluções.

 Se o gerenciador de carga de solução for destinado a gerenciar apenas soluções <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> específicas, as informações de ativação podem ser persistidas como parte do arquivo de solução, solicitando a seção de pré-solução.

 Os gestores específicos de carga <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> de soluções devem desativar-se no manipulador de eventos, a fim de não entrar em conflito com outros gerentes de carga de soluções.

 Se você precisar de um gerenciador de carga de solução apenas para persistir as propriedades globais <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> de carga de projeto (por exemplo, propriedades definidas em uma página de opções), você pode ativar o gerenciador de carga de solução no manipulador de eventos, persistir a configuração nas propriedades da solução e, em seguida, desativar o gerenciador de carga de solução.

## <a name="handle-solution-load-events"></a>Lidar com eventos de carga de soluções
 Para assinar eventos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> carga de solução, ligue quando ativar o gerenciador de carga de soluções. Se você <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>implementar, você pode responder a eventos que se relacionam com diferentes propriedades de carregamento de projetos.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Este evento é acionado antes de uma solução ser aberta.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Este evento é acionado depois que a solução é completamente carregada, mas antes que o carregamento do projeto de fundo comece novamente.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Este evento é acionado depois que uma solução é inicialmente totalmente carregada, quer haja ou não um gerenciador de carga de solução. Ele também é acionado após carga de fundo ou carga de demanda sempre que a solução fica totalmente carregada. Ao mesmo tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> é reativado.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Este evento é acionado antes do carregamento de um projeto (ou projetos). Para garantir que outros processos de fundo sejam `pfShouldDelayLoadToNextIdle` concluídos antes que os projetos sejam carregados, definido **como verdadeiro**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Este evento é acionado quando um lote de projetos está prestes a ser carregado. Se `fIsBackgroundIdleBatch` for verdade, os projetos devem ser carregados em segundo plano; se `fIsBackgroundIdleBatch` for falso, os projetos devem ser carregados sincronizadamente como resultado de uma solicitação do usuário, por exemplo, se o usuário expandir um projeto pendente no Solution Explorer. Você pode lidar com este evento para fazer um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>trabalho caro que de outra forma precisaria ser feito em .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Este evento é acionado após um lote de projetos ter sido carregado.

## <a name="detect-and-manage-solution-and-project-loading"></a>Detectar e gerenciar solução e carregamento de projetos
 Para detectar o estado de carga de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> projetos e soluções, ligue com os seguintes valores:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` `true` retorna se a solução e todos os `false`seus projetos forem carregados, caso contrário.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>) `var` `true` retorna se um lote de projetos estiver sendo carregado `false`em segundo plano, caso contrário .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>) `var` `true` retorna se um lote de projetos estiver sendo carregado sincronicamente como resultado de `false`um comando de usuário ou outra carga explícita, caso contrário .

- [__VSPROPID2. VSPROPID_IsSolutionClosing:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` `true` retorna se a solução estiver sendo `false`fechada, caso contrário.

- [__VSPROPID. VSPROPID_IsSolutionOpening:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>) `var` `true` retorna se uma solução estiver sendo `false`aberta, caso contrário.

Você também pode garantir que projetos e soluções sejam carregados ligando para um dos seguintes métodos:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: chamar este método força os projetos em uma solução para carregar antes que o método retorne.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: chamar este método `guidProject` força os projetos a carregar antes que o método retorne.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: chamar este método `guidProjectID` força o projeto a carregar antes que o método retorne.
