---
title: Exibição de mensagens | Microsoft Docs
description: Cada janela, thread e processo tem um fluxo de mensagens associado que pode ser exibido em uma janela de exibição de mensagens. Saiba como abrir e controlar uma exibição de mensagens.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e20d3f83d6e68211d1b48f63747bea80ee6b25d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876323"
---
# <a name="messages-view"></a>Exibição de mensagens
Cada janela tem um fluxo de mensagens associado. Uma janela de exibição de mensagens exibe esse fluxo de mensagens. O identificador de janela, o código de mensagem e a mensagem são mostrados. Você também pode criar uma exibição de mensagens para um thread ou processo. Isso permite exibir mensagens enviadas a todas as janelas de propriedade de um processo ou thread específico, o que é particularmente útil para capturar mensagens de inicialização de janela.

 Uma janela de exibição de mensagens típica aparece abaixo. Observe que a primeira coluna contém o identificador de janela e a segunda coluna contém um código de mensagem (explicado em [códigos de mensagem](../debugger/message-codes.md)). Os parâmetros de mensagem decodificados e os valores de retorno estão à direita.

 ![Exibição de mensagens do Spy&#43;&#43; ](../debugger/media/spy--_messagesview.png "Spy + + _MessagesView") Exibição de mensagens do Spy + +

## <a name="procedures"></a>Procedimentos

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Para abrir uma exibição de mensagens para uma janela, um processo ou um thread

1. Mova o foco para um [modo](../debugger/windows-view.md)de exibição do Windows, [exibição de processos](../debugger/processes-view.md)ou janela de [exibição de threads](../debugger/threads-view.md) .

2. Localize o nó do item cujas mensagens você deseja examinar e selecione-o.

3. No menu do **Spy** , escolha **mensagens de log**.

     A [caixa de diálogo opções de mensagem](../debugger/message-options-dialog-box.md) é aberta.

4. Selecione as opções para a mensagem que você deseja exibir.

5. Pressione **OK** para iniciar o log de mensagens.

     Uma janela de exibição de mensagens é aberta e um menu **mensagens** é adicionado à barra de ferramentas do Spy + +. Dependendo das opções selecionadas, as mensagens começam a ser transmitidas para a janela de exibição de mensagens ativas.

6. Quando você tiver mensagens suficientes, escolha **parar o registro em log** no menu **mensagens** .

## <a name="in-this-section"></a>Nesta seção
 [Exibição de mensagens de controle](../debugger/how-to-control-messages-view.md) Explica como gerenciar a exibição de mensagens.

 [Abrindo a exibição de mensagens na janela Localizar](../debugger/how-to-open-messages-view-from-find-window.md) Explica como abrir o modo de exibição mensagens na caixa de diálogo localizar janela.

 [Pesquisando uma mensagem no modo de exibição de mensagens](../debugger/how-to-search-for-a-message-in-messages-view.md) Explica como localizar uma mensagem específica no modo de exibição de mensagens.

 [Iniciando e parando a exibição do log de mensagens](../debugger/how-to-start-and-stop-the-message-log-display.md) Explica como iniciar e parar o log de mensagens.

 [Códigos de mensagem](../debugger/message-codes.md) Define os códigos para as mensagens listadas no modo de exibição de mensagens.

 [Exibindo Propriedades de mensagens](../debugger/how-to-display-message-properties.md) Como mostrar mais informações sobre uma mensagem.

## <a name="related-sections"></a>Seções relacionadas
 [Modos de exibição do Spy + +](../debugger/spy-increment-views.md) Explica as exibições de árvore do Spy + + do Windows, mensagens, processos e threads.

 [Usando o Spy + +](../debugger/using-spy-increment.md) Apresenta a ferramenta Spy + + e explica como ela pode ser usada.

 [Caixa de diálogo opções de mensagem](../debugger/message-options-dialog-box.md) Usado para selecionar quais mensagens são listadas no modo de exibição mensagens ativas.

 [Caixa de diálogo pesquisa de mensagem](../debugger/message-search-dialog-box.md) Usado para localizar o nó de uma mensagem específica no modo de exibição de mensagens.

 [Caixa de diálogo Propriedades da mensagem](../debugger/message-properties-dialog-box.md) Usado para exibir as propriedades de uma mensagem selecionada na exibição de mensagem.

 [Referência do Spy + +](../debugger/spy-increment-reference.md) Inclui seções que descrevem cada menu e caixa de diálogo do Spy + +.