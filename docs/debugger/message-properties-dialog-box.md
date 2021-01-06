---
title: Caixa de diálogo Propriedades da mensagem | Microsoft Docs
description: Consulte Propriedades da mensagem para obter mais informações sobre uma mensagem do que é mostrado na exibição de mensagens.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3f58ad7344c7de9a9486fcb3ccefbf263688926f
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903058"
---
# <a name="message-properties-dialog-box"></a>Caixa de diálogo Propriedades da Mensagem
Use essa caixa de diálogo para saber mais sobre uma mensagem específica. Para exibir essa caixa de diálogo, mova o foco para uma janela de [exibição de mensagens](../debugger/messages-view.md) . Selecione qualquer nó de mensagem na árvore e, em seguida, escolha **Propriedades** no menu **Exibir** .

 A guia **geral** é a única guia exibida. As seguintes configurações estão disponíveis:

 **Identificador de janela** A ID exclusiva desta janela. Os números de identificador de janela são reutilizados; eles identificam uma janela somente pelo tempo de vida dessa janela. Clique nesse valor para exibir as propriedades desta janela.

 **Nível de aninhamento** Profundidade do aninhamento desta mensagem, em que 0 não é aninhamento.

 **Mensagem** de Número, status e nome da mensagem do Windows selecionada.

 **LRESULT** O valor do parâmetro *LRESULT* , se houver.

 **wParam** O valor do parâmetro *wParam* , se houver.

 **lParam** O valor do parâmetro *lParam* , se houver. Esse valor será decodificado se for um ponteiro para uma cadeia de caracteres ou estrutura.

## <a name="related-sections"></a>Seções relacionadas
 [Caixa de diálogo opções de mensagem](../debugger/message-options-dialog-box.md) Usado para selecionar quais mensagens são listadas no modo de exibição mensagens ativas.

 [Caixa de diálogo pesquisa de mensagem](../debugger/message-search-dialog-box.md) Usado para localizar o nó de uma mensagem específica no modo de exibição de mensagens.

 [Referência do Spy + +](../debugger/spy-increment-reference.md) Inclui seções que descrevem cada menu e caixa de diálogo do Spy + +.

 [Abrindo a exibição de mensagens na janela Localizar](../debugger/how-to-open-messages-view-from-find-window.md) Explica como abrir o modo de exibição mensagens na caixa de diálogo localizar janela.

 [Pesquisando uma mensagem no modo de exibição de mensagens](../debugger/how-to-search-for-a-message-in-messages-view.md) Explica como localizar uma mensagem específica no modo de exibição de mensagens.

 [Exibição de mensagens](../debugger/messages-view.md) Exibe o fluxo de mensagens associado a uma janela, processo ou thread.

 [Modos de exibição do Spy + +](../debugger/spy-increment-views.md) Explica as exibições de árvore do Spy + + do Windows, mensagens, processos e threads.

 [Usando o Spy + +](../debugger/using-spy-increment.md) Apresenta a ferramenta Spy + + e explica como ela pode ser usada.