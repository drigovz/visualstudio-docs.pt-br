---
title: Janela de saída
description: Saiba mais sobre a janela de saída e como ela exibe mensagens de status para vários recursos no IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0bdbaf79a3700a1ba1c0574e345093af25608e39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932040"
---
# <a name="output-window"></a>janela Saída

A Janela de **Saída** exibe mensagens de status para vários recursos no IDE (ambiente de desenvolvimento integrado). Para abrir a Janela de **Saída**, na barra de menus, escolha **Exibir** > **Saída** ou pressione **Ctrl**+**Alt**+**O**.

## <a name="toolbar"></a>Barra de ferramentas

Os seguintes controles são mostrados na barra de ferramentas da Janela de **Saída**.

### <a name="show-output-from"></a>Mostrar saída de

Exibe um ou mais painéis de saída a serem exibidos. Vários painéis de informações podem estar disponíveis, dependendo de quais ferramentas no IDE usaram a Janela de **Saída** para entregar mensagens ao usuário.

### <a name="find-message-in-code"></a>Localizar mensagem no código

Move o ponto de inserção no editor de código para a linha que contém o erro de build selecionado.

### <a name="go-to-previous-message"></a>Ir para a mensagem anterior

Altera o foco na Janela de **Saída** para o erro de build anterior e move o ponto de inserção no editor de código para a linha que contém o erro de build.

### <a name="go-to-next-message"></a>Ir para a próxima mensagem

Altera o foco na Janela de **Saída** para o próximo erro de build e move o ponto de inserção no editor de código para a linha que contém o erro de build.

### <a name="clear-all"></a>Limpar tudo

Limpa todo o texto do painel **Saída**.

### <a name="toggle-word-wrap"></a>Ativar/Desativar Quebra Automática de Linha

Ativa e desativa o recurso Quebra Automática de Linha no painel **Saída**. Quando a Quebra Automática de Linha estiver ativada, um texto em entradas maiores que se estende além da área de exibição será mostrado na próxima linha.

## <a name="output-pane"></a>Painel de saída

O painel **Saída** selecionado na lista **Mostrar saída de** exibe a saída da fonte indicada.

## <a name="route-messages-to-the-output-window"></a>Rotear mensagens para a Janela de Saída

Para exibir a Janela de **Saída** sempre que você criar um projeto, na caixa de diálogo **Opções** na página **Projetos e Soluções** > **Geral**, selecione **Mostrar Janela de Saída ao iniciar o build**. Em seguida, com um arquivo de código aberto para edição, escolha **Ir para a Próxima Mensagem** e **Ir para a Mensagem Anterior** na barra de ferramentas da Janela de **Saída** para selecionar as entradas no painel **Saída**. Conforme você faz isso, o ponto de inserção no editor de código salta para a linha de código em que ocorre o problema selecionado.

Determinados recursos e comandos do IDE invocados na [janela Comando](../../ide/reference/command-window.md) fornecem sua saída para a janela de **Saída**. A saída de ferramentas externas como arquivos *.bat* e *.com*, que normalmente é exibida na janela de comando, é roteada para um painel de **Saída** quando você seleciona a opção **Usar Janela de Saída** em [Gerenciar ferramentas externas](../../ide/managing-external-tools.md). Muitos outros tipos de mensagens também podem ser exibidos em painéis **Saída**. Por exemplo, quando a sintaxe Transact-SQL em um procedimento armazenado é verificada em um banco de dados de destino, os resultados são exibidos na Janela de **Saída**.

Você também pode programar seus próprios aplicativos para gravar mensagens de diagnóstico em tempo de execução em um painel **Saída**. Para fazer isso, use membros da classe <xref:System.Diagnostics.Debug> ou <xref:System.Diagnostics.Trace> no namespace <xref:System.Diagnostics> da API .NET. Os membros da classe <xref:System.Diagnostics.Debug> exibem a saída quando você compila as configurações de Depuração da solução ou do projeto; os membros da classe <xref:System.Diagnostics.Trace> exibem a saída quando você compila as configurações de Depuração ou de Versão. Para obter mais informações, confira [Mensagens de diagnóstico na Janela de Saída](../../debugger/diagnostic-messages-in-the-output-window.md).

No C++, é possível criar etapas de build e eventos de build personalizados cujos avisos e erros são exibidos e contados no painel de **Saída**. Pressionando **F1** em uma linha de saída, você pode exibir um tópico da Ajuda apropriado. Para obter mais informações, confira [Formatar a saída de uma etapa de build personalizada](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Comportamento de rolagem

Se você usar a rolagem automática na Janela de **Saída** e, em seguida, navegar usando o mouse ou as teclas de seta, a rolagem automática será interrompida. Para retomar a rolagem, pressione **Ctrl** + **end**.

## <a name="see-also"></a>Confira também

- [Mensagens de diagnóstico na janela de saída](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Como controlar a Janela de Saída](/previous-versions/ht6z4e28(v=vs.140))
- [Compilar e criar](../../ide/compiling-and-building-in-visual-studio.md)
- [Noções sobre configurações de build](../../ide/understanding-build-configurations.md)
- [Visão geral da biblioteca de classes](/dotnet/standard/class-library-overview)