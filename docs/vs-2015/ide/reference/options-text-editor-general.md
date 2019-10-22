---
title: Opções, Editor de Texto, Geral | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662258"
---
# <a name="options-text-editor-general"></a>Opções, Editor de Texto, Geral
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Essa caixa de diálogo permite alterar as configurações globais para o Editor de Texto e Código do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Para exibir essa caixa de diálogo, clique em **Opções** no menu **Ferramentas**, expanda a pasta **Editor de Texto** e clique em **Geral**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Configurações
 Arrastar e soltar edição de texto quando selecionado, permite que você mova o texto selecionando-o e arrastando-o com o mouse para outro local dentro do documento atual ou qualquer outro documento aberto.

 Realce de delimitador automático quando selecionado, os caracteres delimitadores que separam parâmetros ou pares item-valor, bem como chaves correspondentes, são realçados.

 Controlar alterações quando o editor de código é selecionado, uma linha amarela vertical aparece na margem de seleção para marcar o código que foi alterado desde que o arquivo foi salvo mais recentemente. Quando você salva as alterações, as linhas verticais ficam verdes.

 Detecção automática de codificação UTF-8 sem assinatura por padrão, o editor detecta a codificação pesquisando marcas de ordem de byte ou marcas de charset. Se nenhum deles for encontrado no documento atual, o editor de códigos tenta detectar automaticamente a codificação UTF-8 examinando sequências de bytes. Para desabilitar a detecção automática da codificação, desmarque essa opção.

## <a name="display"></a>Monitor
 Margem de seleção quando selecionada, exibe uma margem vertical ao longo da borda esquerda da área de texto do editor. Você pode clicar nessa margem para selecionar uma linha de texto inteira ou clicar e arrastar para selecionar linhas consecutivas de texto.

|Margem de seleção ativada|Margem de seleção desativada|
|-------------------------|--------------------------|
|![Captura de tela de HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif "|::ref1::|")|![Captura de tela de HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "|::ref2::|")|

 Margem do indicador quando selecionado, exibe uma margem vertical fora da borda esquerda da área de texto do editor. Quando você clica nesta margem, um ícone e uma dica de ferramenta relacionados ao texto aparecem. Por exemplo, atalhos da lista de tarefas ou de pontos de interrupção aparecem na margem de indicadores. Informações da margem de indicadores não são impressas.

 Barra de rolagem vertical quando selecionada, exibe um ScrollBar vertical que permite rolar para cima e para baixo para exibir os elementos que ficam fora da área de exibição do editor. Se barras de rolagem verticais não estiverem disponíveis, você poderá usar Page Up, Page Down e teclas do cursor para rolar.

 Barra de rolagem horizontal quando selecionada, exibe um ScrollBar horizontal que permite rolar de lado a lado para exibir elementos que ficam fora da área de exibição do editor. Se barras de rolagem horizontais não estiverem disponíveis, você poderá usar as teclas de cursor para rolar.

 Realçar a linha atual quando selecionada, exibe uma caixa cinza ao lado da linha de código na qual o cursor está localizado.

## <a name="see-also"></a>Veja também
 [Opções, editor de texto, todas as](../../ide/reference/options-text-editor-all-languages.md) [Opções de idiomas, editor de texto, todas as linguagens,](../../ide/reference/options-text-editor-all-languages-tabs.md) [Opções de guias, editor de texto, extensão de arquivo](../../ide/reference/options-text-editor-file-extension.md) [identificando e personalizando atalhos de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) [Personalizando o editor](../../ide/customizing-the-editor.md) [usando IntelliSense](../../ide/using-intellisense.md)
