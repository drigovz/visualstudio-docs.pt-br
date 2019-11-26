---
title: Como invocar o depurador de fluxo de trabalho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 13fd54eeebf0323fcb9b8cad6a8cd8b75ae11fb3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292895"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Como: Chamar o depurador de fluxo de trabalho
Geralmente, você depura fluxos de trabalho assim como você os programas de depuração escritos em outras linguagens de programação do Visual Studio. Você pode iniciar o depurador de fluxo de trabalho das seguintes maneiras:

- Selecione **anexar ao processo** no menu **depurar** para selecionar o processo de host em execução para sua instância de fluxo de trabalho. Este procedimento é o mesmo que anexar a um processo host no código gerenciado.

- Pressione **F5** para iniciar a execução de uma instância do fluxo de trabalho ou para continuar a execução depois que um ponto de interrupção tiver sido atingido.

- Use a depuração remota. Para obter informações sobre como usar a depuração remota, consulte [como habilitar a depuração remota](https://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > Se o aplicativo de fluxo de trabalho for direcionado para a arquitetura x86 e estiver hospedado em um computador que executa um sistema operacional de 64 bits, a depuração remota não funcionará a menos que [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] esteja instalado no computador remoto ou o destino do aplicativo de fluxo de trabalho seja alterado para **qualquer CPU**.

### <a name="stepping-through-code"></a>Percorrendo o código

- **Etapa em**: você pode entrar em uma atividade usando **F11**. O depurador avança em qualquer manipulador que é definido. Se nenhum manipulador é definido, você vai sobre a atividade, ou com atividades compostas, que contém outras atividades, você vai na primeira atividade executando.

- **Depuração temporária:** Você pode sair de uma atividade usando **Shift-F11**. Depuração fora de uma atividade executa a atividade atual e todas as suas atividades irmãos para a conclusão. O depurador interrompe no pai de atividade atual. Para passar para fora de um manipulador de código, o depurador interrompe a atividade com que o manipulador está associado.

- **Depuração**: você pode percorrer uma atividade usando **F10**. Para entrar em uma atividade de composição, o depurador interrompe no primeiro filho executável de atividade composta. Para entrar em uma não composição, como uma atividade de <xref:System.Activities.Statements.Assign> , o depurador executa a atividade e seus manipuladores associados e interromper-los na atividade seguir. Se a atividade que é executada é a atividade filho a última em uma atividade de composição, então, após a execução, o depurador interrompe a atividade pai.

### <a name="debugging-with-f5"></a>Depuração com F5

- Se você estiver criando um projeto de aplicativo de console de fluxo de trabalho, basta pressionar **F5** para iniciar a depuração em seu aplicativo e fluxo de trabalho. Se você estiver criando uma biblioteca de atividade em seus próprios, você deve ter um executável do aplicativo host como um projeto de inicialização. Para definir um projeto de inicialização no **Gerenciador de soluções**, clique com o botão direito do mouse no nome do projeto do host e selecione **definir como projeto de inicialização**.

## <a name="see-also"></a>Consulte também
 [Como definir pontos de interrupção em fluxos de](../workflow-designer/how-to-set-breakpoints-in-workflows.md) trabalho [Depurando fluxos de trabalho com o designer de fluxo de trabalho](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)