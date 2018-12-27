---
title: 'Como: Criar manipuladores de eventos em projetos do Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: be56b279750c71ab71f1337f6bc7b2038e1195fe
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648594"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Como: Criar manipuladores de eventos em projetos do Office
  Há várias maneiras de criar manipuladores de eventos no Visual Basic e c#. No modo design, você pode criar o padrão de manipuladores de eventos para controles clicando duas vezes no controle ou usar o painel de eventos do **propriedades** janela para criar manipuladores de qualquer evento no controle. No entanto, se você estiver no modo de exibição de código, talvez não queira alternar para modo de Design para criar um manipulador de eventos.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Para criar um manipulador de eventos no Visual Basic  
  
1.  Dos **nome da classe** lista suspensa na parte superior do Editor de códigos, selecione o objeto que você deseja criar um manipulador de eventos.  
  
    > [!NOTE]  
    >  Se você quiser criar manipuladores de eventos para `ThisDocument` ou `ThisWorkbook`, você deve selecionar **(eventos ThisDocument)** ou **(eventos ThisWorkbook)** no **nome da classe**lista suspensa  
  
2.  Dos **nome do método** lista suspensa na parte superior do Editor de códigos, selecione o evento.  
  
     Visual Studio cria o manipulador de eventos e move o ponto de inserção para o manipulador de eventos recém-criado. Se o manipulador de eventos já existir, o ponto de inserção se move para o manipulador de eventos existente.  
  
### <a name="to-create-an-event-handler-in-c"></a>Para criar um manipulador de eventos em c#  
  
1.  Criar o delegado do evento na **inicialização** evento da classe digitando o nome de evento qualificado seguido por um espaço e, em seguida, digitar **+=** posteriormente sem espaço. Por exemplo:  
  
     `this.<object name>.<event name> +=`  
  
2.  No final da linha de código, pressione a tecla TAB duas vezes.  
  
     Visual Studio automaticamente conclui a linha de código cria o manipulador de eventos e move o ponto de inserção para o manipulador de eventos recém-criado.  
  
## <a name="see-also"></a>Consulte também  
 [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Passo a passo: Programe em eventos de um controle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Compilar soluções do Office](../vsto/building-office-solutions.md)  
  
  