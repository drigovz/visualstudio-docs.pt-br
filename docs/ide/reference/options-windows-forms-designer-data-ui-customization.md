---
title: Opções, Designer de Formulários do Windows, Personalização da Interface do Usuário de Dados
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ca68a944002d743c6f3d2f89b309b8b77c5dfdb3
ms.sourcegitcommit: 6b0503ed8d25454d6e39a8e606910b3fa58cf1d2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68981682"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Caixa de diálogo Opções: Designer de Formulários do Windows > Personalização da Interface do Usuário de Dados

Essa caixa de diálogo define quais controles aparecem na lista de controles disponíveis para itens na janela Fontes de Dados. Para abri-la, selecione **Ferramentas** > **Opções** e, em seguida, selecione **Designer de Formulários do Windows** > **Personalização da Interface do Usuário de Dados**.

É possível selecionar um controle de um item na janela Fontes de Dados antes de arrastá-lo para o formulário em um aplicativo do Windows Forms. Os controles disponíveis são determinados pelo tipo de dados do item. Cada tipo de dados possui uma lista de controles associados válidos, conforme definido nessa caixa de diálogo, incluindo um controle padrão. Ao arrastar um item da janela Fontes de Dados para um formulário sem selecionar um controle, o controle padrão para o tipo de dados do item selecionado é adicionado ao formulário.

Personalize a lista de controles associados, marcando e desmarcando as caixas de seleção dos controles disponíveis para cada tipo de dados. Para adicionar um controle à lista, adicione um controle que implemente o atributo de associação de dados <xref:System.ComponentModel.DefaultBindingPropertyAttribute> ou <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> à Caixa de Ferramentas. Em seguida, o controle aparece na lista de controles para o tipo de dados. Para obter mais informações, confira [Como: adicionar controles personalizados à janela Fontes de Dados](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Tipo de dados

Exibe uma lista de tipos aos quais você associa controles. As tabelas são representadas como o tipo de dados `[List]`. As colunas são representadas como o tipo de dados real da coluna no armazenamento de dados subjacente.

## <a name="associated-controls"></a>Controles associados

Exibe uma lista de controles associados ao tipo de dados selecionado. Marque ou desmarque a caixa de seleção ao lado do controle para associá-la ou desassociá-la. Os controles selecionados aparecem na janela Fontes de Dados de uma coluna do banco de dados vinculada ao tipo de dados associado.

## <a name="set-default"></a>Definir Padrão

Atribui o tipo de controle selecionado para ser o padrão para o tipo de dados selecionado. O controle padrão aparece como a primeira seleção no menu de atalho para uma coluna do banco de dados na janela Fontes de Dados. Ao arrastar um item da janela Fontes de Dados para um formulário sem selecionar um controle, o controle padrão para o tipo de dados do item selecionado é adicionado ao formulário.

Somente um tipo de controle pode ser atribuído como padrão para um tipo de dados.

## <a name="clear-default"></a>Limpar Padrão

Remove a designação de um controle como padrão para o tipo de dados selecionado. Se não há um padrão para o tipo de dados selecionado, `[None]` aparece como a primeira seleção no menu de atalho para uma coluna do banco de dados desse tipo.