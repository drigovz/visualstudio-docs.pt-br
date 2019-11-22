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
ms.openlocfilehash: 5bab07b8ba0b71bd880135518ff9ff5fc697d54c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302806"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Usando o computador de estado herdado Designer de Fluxo de Trabalho
Quando você estiver criando um novo projeto de fluxo de trabalho do computador de estado em [!INCLUDE[vs2010](../includes/vs2010-md.md)] que tem como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], você pode escolher usar **Aplicativo de console do fluxo de trabalho do computador de estado** ou herdado o modelo de projeto de **Biblioteca de fluxo de trabalho do computador de estado** . Se você escolher um desses modelos de projeto do computador de estado, o designer do computador de estado é apresentado como a interface do usuário herdado do designer de fluxo de trabalho. Para obter informações sobre os modelos de projeto de máquina de estado herdado, consulte [como criar estado aplicativos de console de fluxo de trabalho (Herdado)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) e [como criar uma biblioteca de fluxo de trabalho de estado (herdada)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Um fluxo de trabalho do computador de estado consiste em um conjunto de estados. Um estado denotado é como um estado inicial. Cada estado pode receber um determinado conjunto de eventos. Baseado em um evento, uma transição pode ser feita para outro estado. O fluxo de trabalho do computador de estado pode ter um estado final. Quando uma transição é feita ao estado final, o fluxo de trabalho completa.

## <a name="state-machine-designer-views"></a>Modos de exibição do designer do computador de estado
 O designer do computador de estado é um designer de forma livre, o que significa que as atividades podem ser movidos para o redor livremente na superfície de design. O designer do computador de estado tem dois modos: o modo *de estado* e exibição *de baseada* .

 Modo de estado mostra as atividades de estado e as atividades corretamente eventos que podem ser contidas dentro de uma atividade de estado. Nesta exibição, as transições de um estado para outro são representadas por linhas que estendem de atividade de baseada em um estado para outro estado. Você também pode criar transições desenhando a linha você mesmo. Para desenhar a transição, selecione a atividade de baseada e em seguida, selecione uma das alças da atividade e arraste-a. Esta ação desenha uma linha. Esta linha é anexada no estado de destino, indicando uma transição entre estados.

 Para acessar a exibição orientada evento, clique duas vezes em uma atividade de baseada. O designer que aparece é bem como o designer sequencial de fluxo de trabalho. Na parte superior do designer, uma barra de navegação mostra a hierarquia de atividades até a atividade de baseada que é exibida. Você pode navegar de volta para o modo de estado clicando em qualquer elemento na hierarquia exibida. Se você desenhou uma transição de um estado para outro no modo de estado, e se você está exibindo a exibição orientada a eventos da atividade, uma atividade do estado é adicionada à atividade de baseada para você. Se você alterar as propriedades de atividade do estado, é passado refletida no modo de estado.

## <a name="state-machine-workflow-activities"></a>Atividades de fluxo de trabalho do computador de estado
 A tabela a seguir descreve as atividades principais que são usadas em um designer de fluxo de trabalho do computador de estado.

|Nome da caixa de ferramentas|Atividade|Descrição|
|------------------|--------------|-----------------|
|**Estado**|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Representa um estado em uma máquina de estado; pode conter atividades **StateActivity** adicionais. Para obter mais informações, consulte [usando a atividade StateActivity](https://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Especifica uma transição para um novo estado. Para obter mais informações, consulte [usando a atividade SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Executa quando um estado estiver conectado; pode conter outras atividades. Para obter mais informações, consulte [usando a atividade StateInitialization](https://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Executa atividades contidas ao sair de uma atividade [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) . Para obter mais informações, consulte [usando a atividade StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Usado para os estados que contam com um evento externa para iniciar executar. A atividade **EventDrivenActivity** deve ter uma atividade que implemente a interface [IEventActivity](https://go.microsoft.com/fwlink?LinkID=65032) como a primeira atividade filha. Para obter mais informações, consulte [usando a atividade EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068).|

 O componente principal em um fluxo de trabalho de máquina de estado é a atividade [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) . Como os eventos são capturados em vários pontos em um fluxo de trabalho do computador de estado, os estados diferentes estão conectados para manipular as tarefas associadas com eventos. Durante o tempo de vida de fluxo de trabalho, o fluxo de trabalho pode sair e inserir vários estados diferentes. Esses Estados se conectam entre si usando a atividade [SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041) .

 Ao arrastar um novo **StateActivity** para a superfície de design do fluxo de trabalho, você pode adicionar as atividades [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)ou **StateActivity** adicionais como atividades filhas.

> [!CAUTION]
> Quando você usa o designer de fluxo de trabalho do computador de estado para criar fluxos de trabalho, você deve monitorar a estrutura de fluxo de trabalho que você está criando com a janela de exibição de **Estrutura de Tópicos de Documento** . A exibição da estrutura de fluxo de trabalho do computador de estado na janela de exibição de **Estrutura de Tópicos de Documento** espelha o layout lógico de atividades no arquivo de marcação de fluxo de trabalho. O layout físico das atividades de fluxo de trabalho como aparecem na superfície de design não pode espelhar o layout lógico de atividades no arquivo de marcação de fluxo de trabalho.
>
> Para abrir a janela de **Estrutura de Tópicos de Documento** , no menu de **Modo de Visualização** , aponte para **Outras Janelas**, selecione **Estrutura de Tópicos de Documento**.

## <a name="see-also"></a>Consulte também
 [Como: criar aplicativos de estado do console de fluxo de trabalho (Herdado)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) [como criar um](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [modelo](https://go.microsoft.com/fwlink?LinkID=65016) de fluxo de trabalho de máquina de estado (Herdado) usando a atividade [StateActivity](https://go.microsoft.com/fwlink?LinkID=65083) usando a atividade [StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65006) [usando a atividade StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65008) [usando a atividade SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082) [usando a atividade EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068)