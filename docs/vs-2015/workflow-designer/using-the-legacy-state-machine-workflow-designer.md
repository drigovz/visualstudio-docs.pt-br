---
title: Usando o computador de estado herdado Designer de Fluxo de Trabalho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 77bb2c7abb49dbf6fe973ebc80f8340000e4afbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845999"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Usando o computador de estado herdado Designer de Fluxo de Trabalho
Ao criar um novo projeto de fluxo de trabalho de máquina de estado no [!INCLUDE[vs2010](../includes/vs2010-md.md)] que tem como alvo o [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] , você pode optar por usar o **aplicativo de estado do console de fluxo** de trabalho de máquina ou o modelo de projeto herdado da biblioteca de fluxo de **trabalho** de máquina de estado. Se você escolher um desses modelos de projeto do computador de estado, o designer do computador de estado é apresentado como a interface do usuário herdado do designer de fluxo de trabalho. Para obter informações sobre os modelos de projeto de máquina de estado herdado, consulte [como criar estado aplicativos de console de fluxo de trabalho (Herdado)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) e [como criar uma biblioteca de fluxo de trabalho de estado (herdada)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Um fluxo de trabalho do computador de estado consiste em um conjunto de estados. Um estado denotado é como um estado inicial. Cada estado pode receber um determinado conjunto de eventos. Baseado em um evento, uma transição pode ser feita para outro estado. O fluxo de trabalho do computador de estado pode ter um estado final. Quando uma transição é feita ao estado final, o fluxo de trabalho completa.

## <a name="state-machine-designer-views"></a>Modos de exibição do designer do computador de estado
 O designer do computador de estado é um designer de forma livre, o que significa que as atividades podem ser movidos para o redor livremente na superfície de design. O designer de máquina de estado tem duas exibições: modo de exibição de *estado* e exibição *orientada por evento* .

 Modo de estado mostra as atividades de estado e as atividades corretamente eventos que podem ser contidas dentro de uma atividade de estado. Nesta exibição, as transições de um estado para outro são representadas por linhas que estendem de atividade de baseada em um estado para outro estado. Você também pode criar transições desenhando a linha você mesmo. Para desenhar a transição, selecione a atividade de baseada e em seguida, selecione uma das alças da atividade e arraste-a. Esta ação desenha uma linha. Esta linha é anexada no estado de destino, indicando uma transição entre estados.

 Para acessar a exibição orientada evento, clique duas vezes em uma atividade de baseada. O designer que aparece é bem como o designer sequencial de fluxo de trabalho. Na parte superior do designer, uma barra de navegação mostra a hierarquia de atividades até a atividade de baseada que é exibida. Você pode navegar de volta para o modo de estado clicando em qualquer elemento na hierarquia exibida. Se você desenhou uma transição de um estado para outro no modo de estado, e se você está exibindo a exibição orientada a eventos da atividade, uma atividade do estado é adicionada à atividade de baseada para você. Se você alterar as propriedades de atividade do estado, é passado refletida no modo de estado.

## <a name="state-machine-workflow-activities"></a>Atividades de fluxo de trabalho do computador de estado
 A tabela a seguir descreve as atividades principais que são usadas em um designer de fluxo de trabalho do computador de estado.

|Nome da caixa de ferramentas|Atividade|Descrição|
|------------------|--------------|-----------------|
|**State**|[StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx)|Representa um estado em uma máquina de estado; pode conter atividades **StateActivity** adicionais. Para obter mais informações, consulte [usando a atividade StateActivity](https://msdn2.microsoft.com/library/bb628612.aspx).|
|**SetState**|[SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx)|Especifica uma transição para um novo estado. Para obter mais informações, consulte [usando a atividade SetStateActivity](https://msdn2.microsoft.com/library/bb628469.aspx).|
|**StateInitialization**|[StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx)|Executa quando um estado estiver conectado; pode conter outras atividades. Para obter mais informações, consulte [usando a atividade StateInitialization](https://msdn2.microsoft.com/library/bb675253.aspx).|
|**StateFinalization**|[StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)|Executa atividades contidas ao sair de uma atividade [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) . Para obter mais informações, consulte [usando a atividade StateFinalizationActivity](https://msdn2.microsoft.com/library/bb675278.aspx).|
|**EventDriven**|[EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx)|Usado para os estados que contam com um evento externa para iniciar executar. A atividade **EventDrivenActivity** deve ter uma atividade que implemente a interface [IEventActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ieventactivity.aspx) como a primeira atividade filha. Para obter mais informações, consulte [usando a atividade EventDrivenActivity](https://msdn2.microsoft.com/library/bb628466.aspx).|

 O componente principal em um fluxo de trabalho de máquina de estado é a atividade [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) . Como os eventos são capturados em vários pontos em um fluxo de trabalho do computador de estado, os estados diferentes estão conectados para manipular as tarefas associadas com eventos. Durante o tempo de vida de fluxo de trabalho, o fluxo de trabalho pode sair e inserir vários estados diferentes. Esses Estados se conectam entre si usando a atividade [SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx) .

 Ao arrastar um novo **StateActivity** para a superfície de design do fluxo de trabalho, você pode adicionar as atividades [EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx), [StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx), [StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)ou **StateActivity** adicionais como atividades filhas.

> [!CAUTION]
> Ao usar o designer de fluxo de trabalho de máquina de estado para criar fluxos de trabalho, você deve monitorar a estrutura do fluxo de trabalho que está criando com a janela de exibição de **estrutura de tópicos do documento** . A exibição da estrutura do fluxo de trabalho da máquina de estado na janela de exibição de **estrutura de tópicos do documento** espelha o layout lógico das atividades no arquivo de marcação do fluxo de trabalho. O layout físico das atividades de fluxo de trabalho como aparecem na superfície de design não pode espelhar o layout lógico de atividades no arquivo de marcação de fluxo de trabalho.
>
> Para abrir a janela **estrutura de tópicos do documento** , no menu **Exibir** , aponte para **outras janelas**e selecione **estrutura de tópicos do documento**.

## <a name="see-also"></a>Consulte Também
 [Como: criar aplicativos de estado do console de fluxo de trabalho (Herdado)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) [como criar um](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [modelo](https://msdn2.microsoft.com/library/bb628601.aspx) de fluxo de trabalho de máquina de estado (Herdado) usando a atividade [StateActivity](https://msdn2.microsoft.com/library/bb628612.aspx) usando a atividade [StateInitializationActivity](https://msdn2.microsoft.com/library/bb675253.aspx) [usando a atividade StateFinalizationActivity](https://msdn2.microsoft.com/library/bb675278.aspx) [usando a atividade SetStateActivity](https://msdn2.microsoft.com/library/bb628469.aspx) [usando a atividade EventDrivenActivity](https://msdn2.microsoft.com/library/bb628466.aspx)
