---
title: Janela Saída | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f17b91cc462b6f628100ffbf370fcdec2eb9888d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662190"
---
# <a name="output-window"></a>Janela de saída
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A Janela de **Saída** pode exibir mensagens de status para vários recursos no IDE (ambiente de desenvolvimento integrado). Para abrir a Janela de **Saída**, na barra de menus, escolha **Exibir/Saída** (ou clique em CTRL+ALT+O).

> [!WARNING]
> A Janela de Saída não é exibida no menu Exibir nas edições do Visual Studio Express. Para mostrá-la, use as teclas de atalho CTRL+ALT+O.

## <a name="toolbar"></a>Barra de ferramentas
 **Mostrar saída de** Exibe um ou mais painéis de saída a serem exibidos. Vários painéis de informações podem estar disponíveis, dependendo de quais ferramentas no IDE usaram a Janela de **Saída** para entregar mensagens ao usuário.

 **Localizar mensagem no código** Move o ponto de inserção no editor de código para a linha que contém o erro de compilação selecionado.

 **Ir para a mensagem anterior** Altera o foco na janela de **saída** para o erro de compilação anterior e move o ponto de inserção no editor de código para a linha que contém esse erro de compilação.

 **Ir para a próxima mensagem** Altera o foco na janela de **saída** para o próximo erro de compilação e move o ponto de inserção no editor de código para a linha que contém esse erro de compilação.

 **Limpar tudo** Limpa todo o texto do painel de **saída** .

 **Alternar quebra automática de palavra** Ativa e desativa o recurso de quebra automática de palavra no painel de **saída** . Quando a Quebra Automática de Linha estiver ativada, um texto em entradas maiores que se estende além da área de exibição será mostrado na próxima linha.

## <a name="output-pane"></a>Painel de Saída
 O painel **Saída** selecionado na lista **Mostrar saída de** exibe a saída da fonte indicada.

## <a name="routing-messages-to-the-output-window"></a>Encaminhando mensagens para a Janela de Saída
 Para exibir a janela **Saída** sempre que você compilar um projeto, na caixa de diálogo **Geral, Projetos e Soluções, Opções**, selecione **Mostrar Janela de Saída no início do build**. Em seguida, com um arquivo de código aberto para edição, escolha os botões **Ir para a Próxima Mensagem** e **Ir para a Mensagem Anterior** na barra de ferramentas da Janela de **Saída** para selecionar entradas no painel **Saída**. Conforme você faz isso, o ponto de inserção no editor de código salta para a linha de código em que ocorre o problema selecionado.

 Determinados recursos e comandos do IDE invocados na [janela de comando](../../ide/reference/command-window.md) entregam a saída para a janela de **saída** . A saída de ferramentas externas como arquivos .bat e .com, que normalmente é exibida na janela Prompt de Comando, é encaminhada para um painel **Saída** ao selecionar a opção **Usar Janela de Saída** em [Gerenciando ferramentas externas](../../ide/managing-external-tools.md). Muitos outros tipos de mensagens também podem ser exibidos em painéis **Saída**. Por exemplo, quando a sintaxe Transact-SQL em um procedimento armazenado é verificada em um banco de dados de destino, os resultados são exibidos na Janela de **Saída**.

 Você também pode programar seus próprios aplicativos para gravar mensagens de diagnóstico em tempo de execução em um painel **Saída**. Para fazer isso, use os membros da classe <xref:System.Diagnostics.Debug> ou <xref:System.Diagnostics.Trace> no namespace <xref:System.Diagnostics> da biblioteca de classes do .NET Framework. Os membros da classe <xref:System.Diagnostics.Debug> exibem a saída quando você compila as configurações de Depuração da solução ou do projeto; os membros da classe <xref:System.Diagnostics.Trace> exibem a saída quando você compila as configurações de Depuração ou de Versão. Para obter mais informações, consulte [mensagens de diagnóstico no janela de saída](../../debugger/diagnostic-messages-in-the-output-window.md).

 No [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], é possível criar etapas e eventos de build personalizados cujos avisos e erros são exibidos e contados no painel **Saída**. Ao pressionar F1 em uma linha de saída, é possível exibir um tópico de ajuda apropriado. Para obter mais informações, consulte [Formatando a saída de uma etapa de build ou um evento de build personalizado](https://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da).

## <a name="scrolling-behavior"></a>Comportamento de rolagem
 Se você usar a rolagem automática na Janela de Saída e, em seguida, navegar usando o mouse ou as teclas de seta, a rolagem automática será interrompida. Para retomar a rolagem automática, pressione CTRL+END.

## <a name="see-also"></a>Consulte Também
 [Mensagens de diagnóstico no janela de saída](../../debugger/diagnostic-messages-in-the-output-window.md) [como controlar o janela de saída](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858) [Compilar e criar](../../ide/compiling-and-building-in-visual-studio.md) [noções básicas](../../ide/understanding-build-configurations.md) sobre a [biblioteca de classes](https://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157) de configurações de Build
