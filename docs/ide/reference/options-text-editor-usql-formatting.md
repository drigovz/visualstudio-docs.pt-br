---
title: Opções de formatação do editor de U-SQL
description: Saiba como usar a página opções de formatação e suas subpáginas para definir opções de formatação de código no editor de código quando você está programando no U-SQL.
ms.custom: SEO-VS-2020
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a42fa7e5f40f413f7bc336ba8f0afbba7bdbf445
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932287"
---
# <a name="options-text-editor-u-sql-formatting"></a>Opções, Editor de Texto, U-SQL, Formatação

Use a página opções de **formatação** para definir opções de formatação de código no editor de códigos. Para acessar essa página de opções, escolha **ferramentas**  >  **Opções**. Na caixa de diálogo **Opções**, escolha **Editor de Texto** > **U-SQL** > **Formatação**.

## <a name="general-page"></a>Página Geral

### <a name="general-settings"></a>Configurações gerais

Essas configurações afetam *quando* o editor de códigos aplica opções de formatação ao código.

- **Formatar automaticamente a instrução concluída ao inserir ponto-e-vírgula**

   Quando essa opção estiver selecionada, as instruções serão formadas quando você escolher a tecla de ponto-e-vírgula, de acordo com as opções de formatação selecionadas para o editor.

- **Formatar automaticamente ao colar**

   Quando selecionada, formata o texto que é colado no editor de acordo com as opções de formatação selecionadas para o editor.

## <a name="preview-windows"></a>Janelas de visualização

As subpáginas **Recuo**, **Novas Linhas** e **Espaçamento** exibem uma janela de visualização na parte inferior. A janela de visualização mostra o efeito de cada opção. Para usar a janela de visualização, selecione uma opção de formatação. A janela de visualização mostra um exemplo da opção selecionada. Quando você altera uma configuração marcando uma caixa de seleção, a janela de visualização é atualizada para mostrar o efeito da nova configuração.

### <a name="indentation-remarks"></a>Comentários de recuo

As opções de recuo nas páginas de **guias** de cada idioma determinam apenas onde o editor de código coloca o cursor quando você pressiona **Enter** no final de uma linha. As opções de recuo em **Formatação** se aplicam quando o código é formatado automaticamente, por exemplo:

- Quando você cola o código no arquivo enquanto **Formatar automaticamente ao colar** está selecionada
- Quando o bloco que está sendo formatado é digitado manualmente

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo geral, ambiente, opções](../../ide/reference/general-environment-options-dialog-box.md)
