---
title: Guia mensagens, caixa de diálogo de opções de mensagem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9eb1c88d935fa307e8b86a9a75da423bc08111c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149442"
---
# <a name="messages-tab-message-options-dialog-box"></a>Guia Mensagens, Caixa de diálogo Opções da Mensagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use o **mensagens** tab para selecionar qual mensagem tipos à lista na [exibição de mensagens](../debugger/messages-view.md)e para especificar critérios de pesquisa da mensagem. Para exibir o [caixa de diálogo de opções de mensagem](../debugger/message-options-dialog-box.md), escolha **mensagens de Log** do **Spy** menu.  
  
 Normalmente, você seleciona pela primeira vez **grupos de mensagens**e, em seguida, ajustar a seleção selecionando individuais **mensagens para o modo de exibição**. O **todos os** botão Seleciona todos os tipos de mensagem e o **None** botão limpa todos os tipos.  
  
 As seguintes configurações estão disponíveis sobre o **mensagens** guia:  
  
 **Mensagens para Exibir**  
 Selecione mensagens específicas para a exibição. Quando você cria uma nova janela de mensagens, ele pode exibir todas as mensagens. Quando você filtra mensagens do **mensagens** guia, esse filtro se aplica somente a novas mensagens, não as mensagens que já foram exibidas na exibição do Windows.  
  
 **Grupos de Mensagens**  
 Selecione os grupos de mensagens para a exibição. Os grupos disponíveis incluem:  
  
- WM_USER: com um código de maior que ou igual a WM_USER  
  
- Registrado: registrado com o **RegisterWindowMessage** chamar  
  
- Desconhecido: mensagens desconhecidas no intervalo de 0 a (WM_USER – 1)  
  
  Observe que esses **grupos de mensagens** não são mapeadas para as entradas específicas sob **exibição de mensagens para**. Quando você seleciona um grupo, a seleção é aplicada diretamente ao fluxo de mensagens.  
  
  Uma caixa de seleção esmaecida dentro **grupos de mensagens** indica que o **exibição de mensagens para** caixa de listagem foi modificada para mensagens nesse grupo; nem todos os tipos de mensagem nesse grupo são selecionados.  
  
  **Salvar as Configurações como Padrão**  
  Salve as configurações atuais para uso posterior como opções de pesquisa da mensagem. Essas configurações também são salvas ao sair Spy + +.
