---
title: Opções, Editor de Texto, C#, Formatação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5371b7180aed462910a57daeb9bf5d43f2ecfedb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662280"
---
# <a name="options-text-editor-c-formatting"></a>Opções, editor de texto, C#, formatação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a caixa de diálogo da página de propriedades **Formatação** para definir opções para formatar código no Editor de Código. Para acessar essa caixa de diálogo, clique em **Opções** no menu **Ferramentas**, expanda **Editor de Texto**, expanda **C#** e, em seguida, clique em **Formatação**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="general-settings"></a>Configurações gerais
 As configurações gerais afetam como o Editor de Código aplica as opções de formatação ao código.

## <a name="uielement-list"></a>Lista de elementos de interface do usuário

|Rótulo|Descrição|
|-----------|-----------------|
|**Formatar automaticamente instrução concluídas em ;**|Quando selecionada, formata instruções à conclusão de acordo com as opções de formatação selecionadas para o Editor de Código. Desmarque essa caixa se não quiser que o Editor de Código altere as instruções.|
|**Formatar automaticamente bloco concluído em }**|Quando selecionada, forma blocos de código de acordo com as opções de formatação selecionadas para o Editor de código assim que você conclui o bloco de código. Desmarque essa caixa se não quiser que o Editor de Código altere os blocos.|
|**Ajustar recuo ao colar**|Quando selecionada, formata o texto colado no Editor de Código conforme as opções de formatação selecionadas para o Editor de Código. Desmarque essa caixa se não quiser que o texto colado seja alterado.|

## <a name="preview-window"></a>Janela de Visualização
 Os painéis de opções **Recuo**, **Novas Linhas**, **Espaçamento** e **Disposição** exibem uma janela de visualização. A janela de visualização mostra o efeito de cada opção. Para usar a janela de visualização, selecione uma opção de formatação. A janela de visualização mostra um exemplo da opção selecionada. Quando você altera a configuração, por exemplo, quando marca ou desmarca uma caixa de seleção, a janela de visualização é atualizada para mostrar o efeito da nova configuração.

## <a name="remarks"></a>Comentários
 As opções de recuo nas páginas de **guias** de cada idioma determinam apenas onde o editor de código coloca o cursor quando você pressiona Enter no final de uma linha. Opções de recuo em **Formatação** aplicam-se quando o código é formatado automaticamente, por exemplo, quando você cola o código no arquivo enquanto **Ajustar recuo ao colar** está selecionado e quando o bloco que está sendo formatado é digitado manualmente.

## <a name="see-also"></a>Consulte Também
 [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
