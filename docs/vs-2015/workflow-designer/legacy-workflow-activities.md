---
title: Atividades de fluxo de trabalho herdadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6bdfb5e2a51a274bd5f0490954a2825a2e488c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302955"
---
# <a name="legacy-workflow-activities"></a>Atividades herdados de fluxo de trabalho
o [!INCLUDE[wf](../includes/wf-md.md)] inclui um conjunto padrão de atividades que fornecem funcionalidade para fluxo de controle, condições, manipulação de eventos, gerenciamento de estado e comunicação com aplicativos e serviços. Ao criar fluxos de trabalho, você pode usar sistema forneceu as atividades que são fornecidas por [!INCLUDE[wfd1](../includes/wfd1-md.md)], ou você pode criar suas próprias atividades personalizados.

 A tabela a seguir lista o conjunto de atividade de para fora da estrutura de [!INCLUDE[wf2](../includes/wf2-md.md)] . Muitas, mas não todas, essas atividades são representadas pelo designer de atividade que podem ser acessados de **Caixa de Ferramentas** de [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Para criar uma atividade, arraste o designer de **Caixa de Ferramentas** e solte-o na superfície de design.

|Atividade|Descrição|
|--------------|-----------------|
|[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)|Usado com a atividade **HandleExternalEventActivity** para comunicações de entrada e saída com um serviço local. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)|Usado para conter a lógica de limpeza para uma atividade composta cancelada antes de filhos de quaisquer atividades composto é executar concluído. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](https://go.microsoft.com/fwlink?LinkID=65026)|Permite que você adicione Visual Basic ou código em c ao fluxo de trabalho. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade CodeActivity](https://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65027)|Uma versão compensável do [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65051)|Uma versão compensável de **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65063).|
|[CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65052)|Permite que você chamar código para desfazer ou compensar operações já executadas pelo fluxo de trabalho quando ocorre um erro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053)|Um wrapper para uma ou mais atividades que executam compensação para uma atividade TransactionScopeActivity concluída [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)|Executa atividades filhas com base em uma condição que se aplica à própria atividade [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) e com base em condições que se aplicam separadamente a cada filho. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066).|
|[DelayActivity](https://go.microsoft.com/fwlink?LinkID=65028)|Permite que você crie os atrasos no fluxo de trabalho que são baseados em um intervalo de tempo limite. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade DelayActivity](https://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Envolve uma ou mais atividades que são executadas quando ocorre um evento especificado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018)|Fornece uma estrutura para associar eventos com uma atividade. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030)|Executa sua atividade filho principal simultaneamente com um [EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65070).|
|[FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)|Usado para manipular uma exceção de um tipo que você especificar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)|Representa uma atividade composta que tem uma lista ordenada de atividades filho do tipo [FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65031)|Usado em conjunto com a atividade [CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025) para comunicações de entrada e saída com um serviço local. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)|Testa uma condição em cada ramificação e executa atividades na primeira ramificação para a qual a condição é igual a **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)|Representa uma ramificação de um [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65035)|Permite que seu fluxo de trabalho para chamar um serviço Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65036)|Permite que seu fluxo de trabalho para chamar outro fluxo de trabalho. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65077).|
|[ListenActivity](https://go.microsoft.com/fwlink?LinkID=65037)|Uma atividade composta que contém apenas atividades filhas de [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029) . [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade ListenActivity](https://go.microsoft.com/fwlink?LinkID=65078).|
|[ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65038)|Fornece uma maneira de agendar duas ou mais ramificações de atividade **SequenceActivity** filho para processamento ao mesmo tempo. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019)|Uso representar um conjunto de regras. Uma regra consiste em circunstâncias e em ações resultantes. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65004).|
|[ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)|Cria várias instâncias de uma única atividade filho. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)|Fornece uma maneira simples de vincular várias juntos para atividades a execução sequencial. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Especifica uma transição para um novo estado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Representa um estado em um fluxo de trabalho do computador de estado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade StateActivity](https://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Usado em uma atividade [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) como um contêiner para atividades filhas que são executadas ao deixar a atividade **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Usado em uma atividade [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) como um contêiner para atividades filhas que são executadas ao inserir a atividade **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65006).|
|[SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65056)|Suspende a operação de seu fluxo de trabalho para ativar a intervenção no caso de alguma condição de erro que requer a atenção especial. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65057)|Executa sequencialmente atividades contidas em um domínio sincronizado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65058)|Permite que você terminar imediatamente a operação de seu fluxo de trabalho no caso de uma condição de erro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65086).|
|[ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65059)|Permite que você capturar exceções lançadas corporativos como parte de metadados do processo para um fluxo de trabalho. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65087).|
|[TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093)|Fornece uma estrutura para transações e manipulação de exceção. Para obter mais informações, consulte [usando a atividade TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65046)|Permite que você a modelagem a ocorrência de uma falha de serviço Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65089).|
|[WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65047)|Receber dados de um serviço Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65090).|
|[WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65048)|Responde a uma solicitação de serviço Web feita a um fluxo de trabalho. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65092).|
|[WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)|Permite que seu fluxo de trabalho para executar um loop até que uma condição seja satisfeita. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando a atividade WhileActivity](https://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] como criar atividades personalizadas, consulte [desenvolvendo atividades personalizadas](https://go.microsoft.com/fwlink?LinkID=65023) e [usando o designer de atividades herdadas](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>Nesta seção
 [Exibições de atividade (herdadas)](../workflow-designer/activity-views-legacy.md) Descreve as diferentes exibições de design de atividades.

 [Como: adicionar atividades à caixa de ferramentas (Herdado)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Mostra como adicionar atividades à caixa de ferramentas.

 [Como: criar uma condição de regra declarativa (herdada)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Mostra as etapas para criar uma condição de regra declarativa.

 [Como criar um conjunto de regras PolicyActivity (Herdado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Mostra as etapas para criar um conjunto de regras PolicyActivity.

 [Como implementar uma operação de contrato do WCF (Herdado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Mostra as etapas para implementar uma operação de contrato de [!INCLUDE[indigo2](../includes/indigo2-md.md)].

 [Como invocar uma operação de contrato do WCF (Herdado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Mostra as etapas para invocar uma operação de contrato de [!INCLUDE[indigo2](../includes/indigo2-md.md)].

## <a name="see-also"></a>Consulte também
 [Atividades de Windows Workflow Foundation](https://go.microsoft.com/fwlink?LinkID=65005) [desenvolvendo fluxos de trabalho](https://go.microsoft.com/fwlink?LinkID=65010) [desenvolvendo atividades de fluxo de trabalho](https://go.microsoft.com/fwlink?LinkID=65023)