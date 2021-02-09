---
title: Apresentando o Spy + + | Microsoft Docs
description: Leia sobre a ferramenta de depuração Spy + +. Exibir uma árvore gráfica de relações de objeto do sistema. Obter propriedades para Windows, threads, processos ou mensagens selecionadas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eefc69d7dbd7d05eaadc3e9fe8976c0ff03c9a30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910024"
---
# <a name="introducing-spy"></a>Introdução a Spy++
O Spy + + permite que você execute as seguintes tarefas:

- Exibir uma árvore gráfica de relações entre objetos do sistema. Isso inclui [processos](../debugger/processes-view.md), [threads](../debugger/threads-view.md)e [janelas](../debugger/windows-view.md).

- Procurar por [Windows](../debugger/how-to-search-for-a-window-in-windows-view.md), [threads](../debugger/how-to-search-for-a-thread-in-threads-view.md), [processos](../debugger/how-to-search-for-a-process-in-processes-view.md)ou [mensagens](../debugger/how-to-search-for-a-message-in-messages-view.md)especificados.

- Exiba as propriedades de [janelas](../debugger/how-to-display-window-properties.md), [threads](../debugger/how-to-display-thread-properties.md), [processos](../debugger/how-to-display-process-properties.md)ou [mensagens](../debugger/how-to-display-message-properties.md)selecionadas.

- Selecione uma janela, thread, processo ou mensagem diretamente na exibição.

- Use a [ferramenta Finder](../debugger/how-to-use-the-finder-tool.md) para selecionar uma janela pelo posicionamento do ponteiro do mouse.

- Defina a [opção de mensagem](../debugger/how-to-open-messages-view-from-find-window.md) usando parâmetros de seleção de log de mensagens complexos.

  O Spy + + tem uma barra de ferramentas e hiperlinks para ajudá-lo a trabalhar mais rapidamente. Ele também fornece um comando **Atualizar** para atualizar o modo de exibição ativo, uma **ferramenta de localizador de janelas** para tornar o espionagem mais fácil e uma caixa de diálogo **fonte** para personalizar as janelas de exibição. Além disso, o Spy + + permite salvar e restaurar as preferências do usuário.

  Em várias janelas do Spy + +, você pode clicar com o botão direito do mouse para exibir um menu de atalho de comandos usados com frequência. Quais comandos são exibidos depende de onde está o ponteiro. Por exemplo, se você clicar com o botão direito do mouse em uma entrada na exibição de janela e a janela selecionada estiver visível, clicar em **realçar** no menu de atalho fará com que a borda da janela selecionada seja atualizada para que possa ser localizada com mais facilidade.

> [!NOTE]
> Há dois outros utilitários que se assemelham ao Spy + +: PView, que mostra detalhes sobre processos e threads, e DDESPY.EXE, que permite monitorar mensagens de troca dinâmica de dados (DDE).

## <a name="64-bit-operating-systems"></a>Sistemas operacionais de 64 bits
 Há duas versões do Spy + +. A primeira versão, chamada Spy + + (spyxx.exe), foi projetada para exibir as mensagens enviadas para uma janela que está sendo executada em um processo de 32 bits. Por exemplo, o Visual Studio é executado em um processo de 32 bits. Portanto, você pode usar o Spy + + para exibir mensagens enviadas para **Gerenciador de soluções**. Como a configuração padrão para a maioria das compilações no Visual Studio é executar em um processo de 32 bits, essa primeira versão do Spy + + é aquela que está disponível no menu **ferramentas** do Visual Studio, se os [componentes necessários estiverem instalados](../debugger/how-to-start-spy-increment.md).

 A segunda versão, chamada Spy + + (64 bits) (spyxx_amd64.exe), foi projetada para exibir as mensagens enviadas a uma janela que está sendo executada em um processo de 64 bits. Por exemplo, em um sistema operacional de 64 bits, o bloco de notas é executado em um processo de 64 bits. Portanto, você pode usar o Spy + + (64 bits) para exibir as mensagens enviadas ao bloco de notas. O Spy + + (64 bits) normalmente está localizado em

 ..\\\Common7\Tools\spyxx_amd64.exe de *pasta de instalação do Visual Studio* .

 Você pode executar qualquer versão do Spy + + diretamente na linha de comando.

> [!NOTE]
> Embora o nome do arquivo Spy + + (64 bits) contenha "AMD", ele é executado em qualquer sistema operacional Windows x64.

## <a name="see-also"></a>Confira também
- [Como iniciar Spy++](../debugger/how-to-start-spy-increment.md)
- [Usando Spy++](../debugger/using-spy-increment.md)
- [Exibições do Spy++](../debugger/spy-increment-views.md)
- [Referência de Spy++](../debugger/spy-increment-reference.md)