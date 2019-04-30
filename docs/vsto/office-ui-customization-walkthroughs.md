---
title: Instruções passo a passo personalização de interface do usuário do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes, walkthroughs
- smart documents, walkthroughs
- walkthroughs [Office development in Visual Studio], smart tags
- walkthroughs [Office development in Visual Studio], action panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95561f1404da1efd71ff3418f9154392f393795c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977881"
---
# <a name="office-ui-customization-walkthroughs"></a>Instruções passo a passo personalização de interface do usuário do Office
  As instruções a seguir demonstra o maneiras que você pode personalizar o usuário (UI) de interface de aplicativos do Microsoft Office por meio de personalizações no nível de documento e suplementos do VSTO.

## <a name="actions-pane-walkthroughs"></a>Instruções passo a passo de painel de ações
- [Passo a passo: Inserir texto em um documento de um painel Ações](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md) demonstra como criar um painel de ações em um documento do Word. O painel de ações contém dois controles que enviam os entrada do usuário para o documento.

- [Passo a passo: Associar dados a controles em um painel de ações do Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) demonstra como associar dados a controles em um painel de ações no Word. Os controles de demonstram uma relação mestre/detalhes entre tabelas em um banco de dados do SQL Server.

- [Passo a passo: Associar dados a controles em um painel de ações do Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) descreve como adicionar controles que estão associados a uma fonte de dados para um painel de ações no Excel.

## <a name="custom-task-pane-walkthroughs"></a>Instruções passo a passo de painel de tarefas personalizado
- [Passo a passo: Automatizar um aplicativo de um painel de tarefas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) demonstra como criar um painel de tarefas personalizado que contém um controle que automatiza o aplicativo host quando o usuário clica no controle.

- [Passo a passo: Sincronizar um painel de tarefas personalizado com um botão da faixa de opções](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md) demonstra como criar um painel de tarefas personalizado que os usuários podem ocultar ou exibir clicando em um botão de alternância na faixa de opções.

- [Passo a passo: Exibir painéis de tarefas personalizados com mensagens de email no Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md) demonstra como exibir uma instância exclusiva de um painel de tarefas personalizado com cada mensagem de email que é criado ou aberto no Outlook.

## <a name="ribbon-walkthroughs"></a>Instruções passo a passo de faixa de opções
- [Passo a passo: Criar uma guia personalizada usando o Designer de faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md) demonstra como criar uma guia de faixa de opções personalizada usando o Designer de faixa de opções. A guia contém um botão que pode ser usado para ocultar ou exibir um painel de ações.

- [Passo a passo: Atualizar os controles em uma faixa de opções em tempo de execução](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md) demonstra como usar o modelo de objeto da faixa de opções para atualizar os controles em uma faixa de opções, depois que a faixa de opções é carregada no aplicativo do Office.

- [Passo a passo: Criar uma guia personalizada usando o XML da faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md) demonstra como criar uma guia de faixa de opções personalizada usando XML da faixa de opções em vez de usar o Designer de faixa de opções.

## <a name="controls-on-word-documents"></a>Controles em documentos do Word
- [Passo a passo: Adicionar controles a um documento em tempo de execução em um suplemento do VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md) demonstra como adicionar controles a um documento usando um suplemento do VSTO.

- [Passo a passo: Alterar a formatação do documento usando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md) demonstra como alterar a formatação em um documento do Word por meio de caixas de seleção em uma personalização no nível de documento.

- [Passo a passo: Exibir texto em uma caixa de texto em um documento usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md) demonstra como usar os botões e caixas de texto em documentos do Word.

- [Passo a passo: Atualizar um gráfico em um documento usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md) demonstra como alterar estilos de gráfico em um documento do Word usando os botões de opção em uma personalização no nível de documento.

## <a name="controls-on-excel-worksheets"></a>Controles em planilhas do Excel
- [Passo a passo: Adicionar controles a uma planilha em tempo de execução no projeto de suplemento do VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) demonstra como adicionar controles a uma planilha usando um suplemento do VSTO.

- [Passo a passo: Alterar a formatação da planilha usando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md) demonstra as Noções básicas de usar as caixas de seleção em uma planilha do Excel para alterar a formatação.

- [Passo a passo: Exibir texto em uma caixa de texto em uma planilha usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md) demonstra as Noções básicas de como usar os botões e caixas de texto em planilhas do Excel.

- [Passo a passo: Atualizar um gráfico em uma planilha usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md) mostra as Noções básicas de alterar os estilos de gráfico usando os botões de opção em uma planilha do Excel.

## <a name="see-also"></a>Consulte também
- [Instruções passo a passo usando o Word](../vsto/walkthroughs-using-word.md)
- [Instruções passo a passo usando o Excel](../vsto/walkthroughs-using-excel.md)
- [Dados em instruções passo a passo de soluções do Office](../vsto/data-in-office-solutions-walkthroughs.md)
- [Instruções passo a passo de implantação e segurança](../vsto/security-and-deployment-walkthroughs.md)
- [Introdução ao &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
