---
title: A exibição de mensagens | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db9d64119a94e2358a6f52e6e1269fca8d726cbb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694394"
---
# <a name="messages-view"></a>Exibição de mensagens
Cada janela possui um fluxo de mensagem associado. Uma janela de exibição de mensagens exibe esse fluxo de mensagens. O identificador de janela, o código de mensagem e a mensagem são mostradas. Você pode criar um modo de exibição de mensagens para um thread ou processo também. Isso permite que você exiba as mensagens enviadas para todas as janelas pertencentes a um processo específico ou um thread, que é particularmente útil para capturar as mensagens de inicialização de janela.

 Uma típica janela de exibição de mensagens é exibida abaixo. Observe que a primeira coluna contém o identificador de janela e a segunda coluna contém um código de mensagem (explicado [códigos de mensagem](../debugger/message-codes.md)). Mensagem decodificada de parâmetros e valores de retorno estão à direita.

 ![Spy&#43; &#43; a exibição de mensagens](../debugger/media/spy--_messagesview.png "Spy + + _MessagesView") Spy + + a exibição de mensagens

## <a name="procedures"></a>Procedimentos

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Para abrir um modo de exibição de mensagens para uma janela, processo ou thread

1.  Mover o foco para um [modo de exibição do Windows](../debugger/windows-view.md), [exibição de processos](../debugger/processes-view.md), ou [exibição de Threads](../debugger/threads-view.md) janela.

2.  Localize o nó para o item cujas mensagens que você deseja examinar e selecioná-lo.

3.  Dos **Spy** menu, escolha **mensagens de Log**.

     O [caixa de diálogo de opções de mensagem](../debugger/message-options-dialog-box.md) é aberta.

4.  Selecione as opções para a mensagem que você deseja exibir.

5.  Pressione **Okey** para começar a mensagens de log.

     Um abre a janela de exibição de mensagens e um **mensagens** menu é adicionado à barra de ferramentas Spy + +. Dependendo das opções selecionadas, as mensagens inicia o streaming para a janela de exibição de mensagens ativa.

6.  Quando você ter mensagens suficientes, escolha **parar log** da **mensagens** menu.

## <a name="in-this-section"></a>Nesta seção
 [Controlando a exibição de mensagens](../debugger/how-to-control-messages-view.md) explica como gerenciar a exibição de mensagens.

 [Abrindo o modo de exibição de mensagens da janela localizar](../debugger/how-to-open-messages-view-from-find-window.md) explica como abrir a exibição de mensagens da caixa de diálogo Localizar janela.

 [Procurando por uma mensagem na exibição de mensagens](../debugger/how-to-search-for-a-message-in-messages-view.md) explica como localizar uma mensagem específica na exibição de mensagens.

 [Iniciando e parando a exibição do Log de mensagem](../debugger/how-to-start-and-stop-the-message-log-display.md) explica como iniciar e parar o log de mensagem.

 [Códigos de mensagem](../debugger/message-codes.md) define os códigos para as mensagens listados na exibição de mensagens.

 [Exibindo propriedades de mensagem](../debugger/how-to-display-message-properties.md) como mostrar mais informações sobre uma mensagem.

## <a name="related-sections"></a>Seções relacionadas
 [Exibições do Spy + +](../debugger/spy-increment-views.md) explica as exibições de árvore do Spy + + do windows, as mensagens, processos e threads.

 [Usando Spy + +](../debugger/using-spy-increment.md) apresenta a ferramenta Spy + + e explica como ele pode ser usado.

 [Caixa de diálogo Opções da mensagem](../debugger/message-options-dialog-box.md) usado para selecionar quais mensagens são listadas na exibição de mensagens do Active Directory.

 [Caixa de diálogo de pesquisa da mensagem](../debugger/message-search-dialog-box.md) usado para localizar o nó para uma mensagem específica na exibição de mensagens.

 [Caixa de diálogo Propriedades da mensagem](../debugger/message-properties-dialog-box.md) usado para exibir as propriedades de uma mensagem selecionada no modo de exibição de mensagem.

 [Referência de Spy + +](../debugger/spy-increment-reference.md) inclui as seções que descrevem cada Spy + + menu e caixa de diálogo caixa.