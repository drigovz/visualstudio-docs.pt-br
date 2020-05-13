---
title: Interfaces principais | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737584"
---
# <a name="core-interfaces"></a>Interfaces principais
As seguintes interfaces são as interfaces principais [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]para estender o depurador usando o .

## <a name="discussion"></a>Discussão
 Essas interfaces são usadas principalmente para criar o mecanismo de depuração (DE). Eles são organizados aqui por categorias:

- [Interrupção](#Breakpoints)

- [Contextos](#Contexts)

- [Servidor principal](#CoreServer)

- [Motores de depuração](#DebugEngines)

- [Documentos](#Documents)

- [Eventos](#Events)

- [Expressões](#Expressions)

- [Memória](#Memory)

- [Módulos](#Modules)

- [Portas](#Ports)

- [Processos](#Processes)

- [Programas](#Programs)

- [Propriedades](#Properties)

- [Quadros de pilhas](#StackFrames)

- [Threads](#Threads)

- [Visualizadores de tipo](#TypeVisualizers)

  As entidades que podem implementar as interfaces são:

- Motor de depuração (DE)

- Fornecedor de Porta (PS)

- Avaliador de Expressão (EE)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>Interrupção
 Essas interfaces estão relacionadas à implementação e rastreamento de pontos de interrupção.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Representa um ponto de ruptura vinculado a um local de memória.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Enviado pelo DE quando um ponto de ruptura é vinculado a um local de memória.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Representa um resumo de verificação de documento para uma solicitação de ponto de ruptura.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Enviado pelo DE quando um ponto de ruptura não é vinculado a um local de memória.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Enviado pelo DE quando um ponto de ruptura é alcançado.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Representa um pedido de ponto de ruptura; usado na criação de um ponto de ruptura pendente.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Representa um pedido de ponto de ruptura; usado na criação de um ponto de ruptura pendente.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Representa a informação usada para vincular um ponto de ruptura.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Enviado pelo DE quando um ponto de ruptura é desvinculado de um local de memória.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Representa um ponto de ruptura inválido (devolvido por `IDebugBreakpointErrorEvent2`).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Representa as informações de resolução sobre um ponto de ruptura inválido.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Representa uma posição em uma função onde um ponto de ruptura é definido.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Representa um ponto de ruptura que deve ser vinculado; usado na criação de um ponto de ruptura vinculado.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Representa uma enumeração sobre um conjunto de pontos de interrupção vinculados.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Representa uma enumeração sobre um conjunto de pontos de interrupção que não poderiam ser vinculados a um local de memória.|

## <a name="contexts"></a><a name="Contexts"></a>Contextos
 Essas interfaces representam vários tipos de contextos dentro do programa que está sendo depurado.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Representa a posição inicial de uma instrução de código.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Estende a interface [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) para permitir a recuperação de interfaces de módulo e processo.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS.|Representa uma posição em um documento.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa o contexto em que se avalia uma expressão.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Representa o local de partida em memória de uma coleção de bytes.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa um contexto de quadro de pilha em um ponto de ruptura ou exceção.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa um contexto de quadro de pilha em um ponto de ruptura ou exceção.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Representa uma enumeração sobre um conjunto de contextos de código.|

## <a name="core-server"></a><a name="CoreServer"></a>Servidor principal
 Essas interfaces representam a máquina na qual um programa está sendo depurado. Estes são [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementados por, mas podem ser chamados por motores de depuração.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Fornece acesso a portos e fornecedores portuários, bem como informações sobre o computador.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Representa um [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) que suporta depuração remota.|

## <a name="debug-engines"></a><a name="DebugEngines"></a>Motores de depuração
 Essas interfaces representam motores de depuração e seus eventos associados.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Representa um motor de depuração personalizado.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Representa um mecanismo de depuração personalizado que suporta carregamento de símbolos, JustMyCode e exceções.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Enviado por cada nova instância do DE para indicar que está pronto para lidar com tarefas de depuração.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Representa um mecanismo de depuração personalizado que suporta programas de lançamento.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE|Representa um nó de programa que lida com vários motores de depuração.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Fornece uma maneira para o SDM obter uma interface para o mecanismo de depuração a partir de um quadro de rosca, programa ou pilha.|

## <a name="documents"></a><a name="Documents"></a>Documentos
 Essas interfaces representam documentos (arquivos de origem) e seus elementos associados.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Enviado pelo DE para solicitar um documento a ser aberto.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Representa um fluxo de instruções desmontadas de um documento.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS.|Representa um documento fornecido pelo DE, especificando um nome e um ID de classe (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE|Representa um resumo de verificação de um documento de depuração e permite passar a soma de verificação entre os componentes.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS.|Representa um contexto de documento, uma posição dentro de um documento correspondente a uma determinada declaração e contexto de código.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS.|Representa uma posição geral dentro de um documento.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Representa uma posição em um arquivo de origem como um deslocamento de caracteres.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS.|Representa um documento de texto fornecido pelo DE (derivado do [IDebugDocument2),](../../../extensibility/debugger/reference/idebugdocument2.md)fornecendo o texto real.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Enviado pelo DE para especificar alterações em um arquivo de origem que está na memória.|

## <a name="events"></a><a name="Events"></a>Eventos
 Essas interfaces representam todos os eventos que são enviados entre o DE e o Gerenciador de depuração de sessão (SDM).

| Interface | Implementado por | Descrição |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Enviado pelo DE para solicitar um documento a ser aberto. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | O mecanismo de depuração (DE) envia essa interface para o Gerenciador de depuração de sessão (SDM) para definir a mensagem da barra de status durante as cargas de símbolo. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Enviado pelo DE quando uma pausa no programa foi concluída. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Enviado pelo DE quando um ponto de ruptura é vinculado. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Enviado pelo DE quando um ponto de ruptura não é vinculado. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Enviado pelo DE quando um ponto de ruptura é alcançado. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Enviado pelo DE quando um ponto de ruptura é desvinculado. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Enviado pelo DE para determinar se ele deve parar em um local específico. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Enviado pelo DE para especificar alterações em um arquivo de origem que está na memória. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Enviado por cada nova instância do DE para indicar que está pronto para lidar com tarefas de depuração. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Enviado pelo DE para indicar que o programa que está sendo depurado está pronto para executar a primeira instrução. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Uma interface que é usada por outras interfaces de evento, que podem retornar um erro, para fornecer mensagens de erro leíveis por humanos. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE | Interface base da qual todas as outras interfaces de eventos são derivadas. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Representa uma interface implementada pelo SDM para a qual os eventos (expressos como objetos que implementam uma interface de evento em particular) são enviados. |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Enviado pelo DE quando ocorreu uma exceção no programa que está sendo depurado. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Enviado pelo DE quando uma avaliação de expressão assíncrona estiver completa. |
| IDebugFindSymbolEvent2 | | OBSOLETE. NÃO USE. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Enviado pelo DE ao processar para uma exceção interceptada foi concluído. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Enviado pelo DE quando um programa tiver concluído o carregamento. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Enviado pelo DE para que o IDE exiba uma mensagem informativa para o usuário. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Enviado pelo DE quando um módulo é carregado ou descarregado. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Sinaliza [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] a ui dedepurador para avisar o usuário de que os símbolos não poderiam ser localizados para o executável lançado. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Enviado pelo DE para que o IDE exiba uma seqüência arbitrária. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS. | Enviado por uma porta para comunicar eventos portuários a qualquer ouvinte. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE | Enviado pelo DE ou porto quando um processo foi criado. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE | Enviado pelo DE ou porto quando um processo foi destruído. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE | Enviado pelo DE ou porto quando um programa foi criado. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE | Enviado pelo DE ou porto quando um programa foi destruído. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Habilita um mecanismo de depuração para [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] substituir o comportamento padrão da ia quando você termina uma sessão de depuração. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Enviado do mecanismo de depuração (DE) para o gerenciador de depuração de sessão (SDM) quando o nome de um programa muda. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Enviado pelo DE quando uma nova `IDebugProperty2` propriedade (representada pela interface) foi criada. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Enviado pelo DE quando uma propriedade foi destruída. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Enviado pelo DE ao sair ou sobre uma função para que o valor de retorno possa ser exibido corretamente. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Permite que os mecanismos de depuração leiam as configurações métricas remotamente. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Enviado pelo DE quando um passo para dentro, sobre ou fora de uma instrução foi concluído. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Enviado pelo DE para indicar o sucesso ou falha dos símbolos de carregamento de um módulo. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Enviado pelo DE quando um segmento foi criado. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Enviado pelo DE quando um fio foi destruído. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Enviado pelo DE quando um segmento mudou seu nome. |

## <a name="expressions"></a>Expressões <a name="Expressions"></a>
 Essas interfaces representam expressões a serem avaliadas em um determinado contexto.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Representa uma expressão a ser avaliada. Obtido a partir da interface [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa um contexto no qual uma expressão é avaliada. Obtido a partir da interface [IDebugStackFrame2.](../../../extensibility/debugger/reference/idebugstackframe2.md)|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Enviado pelo DE quando uma avaliação de expressão assíncrona estiver completa.|

## <a name="memory"></a><a name="Memory"></a>Memória
 Essas interfaces representam seqüências de bytes na memória.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Representa uma seqüência de bytes na memória que podem ser lidos ou escritos para.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Representa um local em memória de uma seqüência de bytes.|

## <a name="modules"></a><a name="Modules"></a>Módulos
 Essas interfaces representam um módulo, que corresponde a um executável ou . Arquivo DLL.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Representa um único executável ou DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Representa um [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que suporta símbolos.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Enviado pelo DE quando um módulo é carregado ou descarregado.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Representa as informações do servidor de origem contidas em um arquivo PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Representa uma enumeração sobre um conjunto de módulos que são conhecidos por um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|

## <a name="ports"></a><a name="Ports"></a>Portas
 Essas interfaces representam portos e fornecedores portuários.

| Interface | Implementado por | Descrição |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Representa a porta padrão no computador local. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Habilita um mecanismo de depuração [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] que usa DCOM para pedir à ui para garantir que o firewall não bloqueie a depuração remota. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Representa um porto. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Enviado por uma porta para comunicar eventos portuários a qualquer ouvinte. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Representa uma porta que pode iniciar e encerrar processos. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Usado para registrar e cancelar programas com uma porta; permite que a porta rastreie programas atualmente em fase de depuração. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Representa uma ui personalizada para selecionar a porta. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Representa uma solicitação de uma porta a partir da qual uma nova porta será criada ou localizada. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Representa um fornecedor de portos. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Representa um fornecedor de portas que podem persistir (salvar em disco) informações sobre as portas que ele criou. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Habilita [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] que a ui exiba o texto dentro da seção Informações de **transporte** da caixa de diálogo **Anexar ao processo.** |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Permite consultar informações sobre o computador de destino. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Representa uma enumeração sobre um conjunto de portas. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Representa uma enumeração sobre um conjunto de fornecedores portuários. |

## <a name="processes"></a><a name="Processes"></a>Processos
 Essas interfaces representam processos, um único executável que contém um ou mais programas.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS|Representa um processo que está sendo executado em um computador.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS|Representa um processo que suporta ativamente a depuração (usada para substituir os métodos Step, Continue e Execute na interface [IDebugProgram2).](../../../extensibility/debugger/reference/idebugprogram2.md)|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE|Enviado pelo DE ou porto quando um processo foi criado.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE|Enviado pelo DE ou porto quando um processo foi destruído.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Representa um processo que deve acompanhar qual sessão está anexada a ela.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Representa uma enumeração de um conjunto de processos em uma porta.|

## <a name="programs"></a><a name="Programs"></a>Programas
 Essas interfaces representam programas, unidades lógicas de execução que não correspondem necessariamente a um executável físico ou módulo.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Representa um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que precisa trabalhar em conjunto com outros programas sendo depurados ao mesmo tempo.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE|Representa uma unidade lógica de execução.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE|Enviado pelo DE ou porto quando um programa foi criado.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE|Enviado pelo DE ou porto quando um programa foi destruído.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE|Representa um [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que pode ser manuseado por vários mecanismos de depuração.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Representa um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que deve ser capaz de rastrear qual sessão está anexada a ele.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE|Representa um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que pode retornar informações sobre o processo em que está sendo executado.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE|Representa um programa que pode ser depurado.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE|Permite que um nó de programa seja notificado de uma tentativa de anexar ao programa associado.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Fornece uma maneira para o SDM consultar um DE sobre os programas controlados por esse DE.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Usado por DEs para registrar programas com o SDM para mostrar que estão sendo depurados.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE|Representa um [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que pode empacotar interfaces através de limites de segmento ou processo.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE|Representa uma enumeração de um conjunto de programas.|

## <a name="properties"></a><a name="Properties"></a> Propriedades
 Essas interfaces representam propriedades, um valor associado a um contexto específico, geralmente o resultado de uma avaliação de expressão.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Representa um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que pode exibir seu valor de forma personalizada.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Representa um valor de um quadro de pilha, documento ou o resultado de uma avaliação de expressão.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Representa um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que suporta strings arbitrariamente longas.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Enviado pelo DE quando uma nova propriedade (representada pela interface [IDebugProperty2)](../../../extensibility/debugger/reference/idebugproperty2.md) foi criada.|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Enviado pelo DE quando uma propriedade foi destruída.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Representa uma referência a uma propriedade que pode existir fora de qualquer quadro de pilha em particular.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Representa uma enumeração sobre um conjunto de estruturas [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) que descrevem variáveis, registros, parâmetros e expressões.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Representa uma enumeração sobre um conjunto de estruturas [DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)|

## <a name="stack-frames"></a><a name="StackFrames"></a>Quadros de pilha
 Essas interfaces representam um quadro de pilha, um contexto no qual ocorreu um ponto de ruptura ou exceção.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa um contexto no qual ocorreu um ponto de ruptura ou exceção.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa um [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que pode lidar com exceções interceptadas.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Representa uma enumeração sobre o conjunto de estruturas [de CODE_PATH](../../../extensibility/debugger/reference/code-path.md) que especificam a seqüência de chamada de função usada para chegar a um quadro de pilha específico.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Representa uma enumeração sobre um conjunto de estruturas [FRAMEINFO,](../../../extensibility/debugger/reference/frameinfo.md) que descrevem quadros de pilha.|

## <a name="threads"></a><a name="Threads"></a>Tópicos
 Essas interfaces representam threads e seus eventos associados.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Representa um fio de execução.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Enviado pelo DE quando um segmento foi criado.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Enviado pelo DE quando um fio foi destruído.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Enviado pelo DE quando um segmento mudou seu nome.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Representa uma enumeração sobre um conjunto de tópicos.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>Visualizadores de tipo
 Essas interfaces fornecem suporte para visualizadores de tipo. Essas interfaces são tipicamente implementadas por um avaliador de expressão.

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Representa uma matriz de bytes a serem apresentados a um visualizador de tipo.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Fornece métodos para obter acesso aos dados a serem passados para um visualizador de tipo.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Representa uma propriedade que fornece acesso às implementações [do IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|

## <a name="see-also"></a>Confira também
- [Referência da API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Criar um mecanismo de depuração personalizado](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
