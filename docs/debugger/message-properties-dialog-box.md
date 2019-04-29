---
title: Caixa de diálogo Propriedades de mensagem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options
- message options, General
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f590f40e4e3361f4dbeb46a3a9b8758b8ab5075
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846109"
---
# <a name="message-properties-dialog-box"></a>Caixa de diálogo Propriedades da Mensagem
Use essa caixa de diálogo para obter mais informações sobre uma mensagem específica. Para exibir essa caixa de diálogo, mova o foco para um [exibição de mensagens](../debugger/messages-view.md) janela. Selecione qualquer nó de mensagem na árvore e escolha **propriedades** da **exibição** menu.

 O **geral** guia é a única guia exibida. As configurações a seguir estão disponíveis:

 **Identificador de janela** a ID exclusiva dessa janela. Os números de identificador de janela são reutilizados; elas identificam uma janela somente para o tempo de vida dessa janela. Clique nesse valor para exibir as propriedades dessa janela.

 **Nível de aninhamento** profundidade de aninhamento dessa mensagem, onde 0 é sem aninhamento.

 **Mensagem** número, o status e o nome da mensagem do windows selecionados.

 **lResult** o valor de *lResult* parâmetro, se houver.

 **wParam** o valor de *wParam* parâmetro, se houver.

 **lParam** o valor de *lParam* parâmetro, se houver. Esse valor é decodificado se ele for um ponteiro para uma cadeia de caracteres ou uma estrutura.

## <a name="related-sections"></a>Seções relacionadas
 [Caixa de diálogo Opções da mensagem](../debugger/message-options-dialog-box.md) usado para selecionar quais mensagens são listadas na exibição de mensagens do Active Directory.

 [Caixa de diálogo de pesquisa da mensagem](../debugger/message-search-dialog-box.md) usado para localizar o nó para uma mensagem específica na exibição de mensagens.

 [Referência de Spy + +](../debugger/spy-increment-reference.md) inclui as seções que descrevem cada Spy + + menu e caixa de diálogo caixa.

 [Abrindo o modo de exibição de mensagens da janela localizar](../debugger/how-to-open-messages-view-from-find-window.md) explica como abrir a exibição de mensagens da caixa de diálogo Localizar janela.

 [Procurando por uma mensagem na exibição de mensagens](../debugger/how-to-search-for-a-message-in-messages-view.md) explica como localizar uma mensagem específica na exibição de mensagens.

 [A exibição de mensagens](../debugger/messages-view.md) exibe o fluxo de mensagem associado a uma janela, processo ou thread.

 [Exibições do Spy + +](../debugger/spy-increment-views.md) explica as exibições de árvore do Spy + + do windows, as mensagens, processos e threads.

 [Usando Spy + +](../debugger/using-spy-increment.md) apresenta a ferramenta Spy + + e explica como ele pode ser usado.