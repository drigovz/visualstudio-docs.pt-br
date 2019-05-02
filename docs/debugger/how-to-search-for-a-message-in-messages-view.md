---
title: 'Como: Pesquisar por uma mensagem na exibição de mensagens | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37f99c30c23461ada406bb0650f86d45d2a4a2e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388401"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Como: Pesquisar uma mensagem na exibição de mensagens
Você pode procurar uma mensagem específica na exibição de mensagens, usando seu identificador, o tipo ou a ID da mensagem como critérios de pesquisa. Qualquer uma destas opções — ou uma combinação — será critérios de pesquisa válido. A direção inicial da pesquisa também pode ser especificada. Os campos na caixa de diálogo são pré-carregados com os atributos da mensagem selecionada no momento.

### <a name="to-search-for-a-message-in-messages-view"></a>Para procurar uma mensagem na exibição de mensagens

1. Organizar as janelas assim que Spy + + e um ativo [exibição de mensagens](../debugger/messages-view.md) janela são visíveis.

2. Dos **pesquisa** menu, escolha **localizar mensagem**.

    O [caixa de diálogo de pesquisa de mensagens](../debugger/message-search-dialog-box.md) é aberta.

3. Arraste o **ferramenta Descobridora** sobre a janela desejada. À medida que você arrasta a ferramenta, o **pesquisa de mensagem** caixa de diálogo exibe detalhes sobre a janela selecionada.

   - ou –

     Se você tiver o identificador da janela cujas mensagens que você deseja examinar, digite-o para o **manipular** caixa de texto.

   - ou –

     Se você souber o tipo de mensagem e/ou a ID da mensagem, selecione-os a **tipo** e **mensagem** menus suspensos e desmarque o **manipular** caixa de texto.

4. Limpe todos os campos para o qual você deseja especificar valores.

   > [!TIP]
   > Para reduzir a desordem na tela, selecione a **Spy ocultar** opção. Esta opção oculta a janela principal do Spy + +, deixando apenas o **localizar janela** caixa de diálogo visível na parte superior de seus outros aplicativos. A janela principal do Spy + + é restaurada quando você clica **Okey** ou **Cancelar**, ou quando você desmarca a **ocultar Spy + +** opção.

5. Escolher **para cima** ou **para baixo** para a direção inicial da pesquisa.

6. Clique em **OK**.

   Se uma mensagem correspondente for encontrada, ele é realçado na janela de exibição de mensagens. Ver [a exibição de mensagens](../debugger/messages-view.md).