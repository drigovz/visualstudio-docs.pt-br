---
title: Guia saída, caixa de diálogo opções de mensagem | Microsoft Docs
description: Use a guia saída das opções de mensagem para especificar quais dados de mensagem aparecem no modo de exibição mensagens. Este artigo descreve as configurações disponíveis.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Output
ms.assetid: 22dd48c2-6d17-41b1-b84c-9ddeaef68411
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9cb48f061cfda78e3dec8ef515df82fdefb8193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891573"
---
# <a name="output-tab-message-options-dialog-box"></a>Guia Saída, Caixa de diálogo Opções da Mensagem
Use a guia **saída** para especificar quais dados de cada mensagem listar no [modo de exibição de mensagens](../debugger/messages-view.md). Para exibir a [caixa de diálogo opções de mensagem](../debugger/message-options-dialog-box.md), escolha **registrar mensagens** no menu do **Spy** .

 As configurações a seguir estão disponíveis na guia **saída** :

 **Números de linha** Exibir números de linha.

 **Nível de aninhamento de mensagens** Prefixe mensagens aninhadas com um período por nível.

 **Parâmetros de mensagem bruto** Exiba os valores **wParam** e **lParam** hexadecimais.

 **Parâmetros de mensagem decodificados** Exibe os resultados da decodificação específica de mensagem dos valores **wParam** e **lParam** .

 **Valores de retorno brutos** Exiba o valor de retorno de **LRESULT** hexadecimal.

 **Valores de retorno decodificados** Exibe os resultados da decodificação específica de mensagem do valor de retorno **LRESULT** .

 **Tempo de origem da mensagem** O tempo decorrido desde o início do sistema Windows (apenas para mensagens postadas).

 **Posição do mouse da mensagem** A tela é coordenada do mouse quando a mensagem foi postada (somente para mensagens postadas).

 **Máximo de linhas** Limite o número de linhas que são retidas na exibição de mensagens atualmente selecionada.

 **Também registrar mensagens no arquivo** Especifique um arquivo de saída para o log de mensagens. Esse arquivo de saída é gravado simultaneamente com a janela log de mensagens.

 **Salvar configurações como padrão** Salve as configurações anteriores para novas janelas de fluxo de mensagens. Essas configurações são salvas quando você sai do Spy + +.