---
title: Fluxos de trabalho de depuração com designers de Fluxo de Trabalho
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b8de1ff9875d175c956a45b87d459d0943e783c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597055"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Depurar fluxos de trabalho com o Designer de Fluxo de Trabalho

O **Designer de fluxo de trabalho** fornece a capacidade de depurar fluxos de trabalho e atividades personalizadas. O processo e o comportamento são semelhantes aos do depurador padrão do Visual Studio.

## <a name="invoke-the-workflow-debugger"></a>Invocar o depurador de fluxo de trabalho

Geralmente, você depura fluxos de trabalho assim como você os programas de depuração escritos em outras linguagens de programação do Visual Studio. Você pode iniciar o depurador de fluxo de trabalho das seguintes maneiras:

- Selecione **anexar ao processo** no menu **depurar** para selecionar o processo de host em execução para sua instância de fluxo de trabalho. Este procedimento é o mesmo que anexar a um processo host no código gerenciado.

- Pressione **F5** para iniciar a execução de uma instância do fluxo de trabalho ou para continuar a execução depois que um ponto de interrupção tiver sido atingido.

- Use a depuração remota. Para obter informações sobre como usar a depuração remota, consulte [como habilitar a depuração remota](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Se o aplicativo de fluxo de trabalho for direcionado para a arquitetura x86 e estiver hospedado em um computador que executa um sistema operacional de 64 bits, a depuração remota não funcionará a menos que o Visual Studio esteja instalado no computador remoto ou o destino do aplicativo de fluxo de trabalho seja alterado para **qualquer CPU**.

## <a name="step-through-code"></a>Percorrer o código

- **Etapa em**: entrar em uma atividade pressionando **F11**. O depurador avança em qualquer manipulador que é definido. Se nenhum manipulador é definido, você vai sobre a atividade, ou com atividades compostas, que contém outras atividades, você vai na primeira atividade executando.

- **Depuração temporária:** Saia de uma atividade pressionando **Shift**+**F11**. Depuração fora de uma atividade executa a atividade atual e todas as suas atividades irmãos para a conclusão. O depurador interrompe no pai de atividade atual. Para passar para fora de um manipulador de código, o depurador interrompe a atividade com que o manipulador está associado.

- **Depuração**: passe sobre uma atividade pressionando **F10**. Para entrar em uma atividade de composição, o depurador interrompe no primeiro filho executável de atividade composta. Para entrar em uma não composição, como uma atividade de <xref:System.Activities.Statements.Assign> , o depurador executa a atividade e seus manipuladores associados e interromper-los na atividade seguir. Se a atividade que é executada é a atividade filho a última em uma atividade de composição, então, após a execução, o depurador interrompe a atividade pai.

## <a name="debug-with-f5"></a>Depurar com F5

Se você estiver criando um aplicativo de console de fluxo de trabalho, basta pressionar **F5** para iniciar a depuração em seu aplicativo e fluxo de trabalho. Se você estiver criando uma biblioteca de atividades por conta própria, deverá especificar um aplicativo host executável como o projeto de inicialização. Para definir um projeto de inicialização no **Gerenciador de soluções**, clique com o botão direito do mouse no nome do projeto do host e selecione **definir como projeto de inicialização**.
