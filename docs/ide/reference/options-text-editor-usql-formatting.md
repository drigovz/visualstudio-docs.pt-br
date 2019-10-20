---
title: Opções de formatação do editor de U-SQL
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1e57470c1afa0fad97265bdcebff4fd9a2a0a43
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666661"
---
# <a name="options-text-editor-u-sql-formatting"></a>Opções, Editor de Texto, U-SQL, Formatação

Use a página de opções **Formatação** para definir opções para formatar o código no editor de códigos. Para acessar essa página de opções, escolha **Ferramentas** > **Opções**. Na caixa de diálogo **Opções**, escolha **Editor de Texto** > **U-SQL** > **Formatação**.

## <a name="general-page"></a>Página geral

### <a name="general-settings"></a>Configurações gerais

Essas configurações afetam *quando* o editor de códigos aplica opções de formatação ao código.

- **Formatar automaticamente a instrução concluída ao inserir ponto-e-vírgula**

   Quando essa opção estiver selecionada, as instruções serão formadas quando você escolher a tecla de ponto-e-vírgula, de acordo com as opções de formatação selecionadas para o editor.

- **Formatar automaticamente ao colar**

   Quando selecionada, formata o texto que é colado no editor de acordo com as opções de formatação selecionadas para o editor.

## <a name="preview-windows"></a>Janelas de visualização

As subpáginas **Recuo**, **Novas Linhas** e **Espaçamento** exibem uma janela de visualização na parte inferior. A janela de visualização mostra o efeito de cada opção. Para usar a janela de visualização, selecione uma opção de formatação. A janela de visualização mostra um exemplo da opção selecionada. Quando você altera uma configuração marcando uma caixa de seleção, a janela de visualização é atualizada para mostrar o efeito da nova configuração.

### <a name="indentation-remarks"></a>Comentários de recuo

As opções de recuo nas páginas **Guias** de cada linguagem determinam apenas onde o editor de códigos coloca o cursor quando você pressiona **Enter** no final de uma linha. As opções de recuo em **Formatação** se aplicam quando o código é formatado automaticamente, por exemplo:

- Quando você cola o código no arquivo enquanto **Formatar automaticamente ao colar** está selecionada
- Quando o bloco que está sendo formatado é digitado manualmente

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)