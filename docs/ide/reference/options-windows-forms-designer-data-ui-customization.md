---
title: Opções, Designer de Formulários do Windows, Personalização da Interface do Usuário de Dados
description: Saiba como usar a página de personalização da interface do usuário de dados para definir quais controles aparecem na lista de controles disponíveis para os itens na janela fontes de dados.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2b43776d2218f6f2a6a120e139dcae9d540f6f10
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040089"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Caixa de diálogo opções: Designer de Formulários do Windows > personalização da interface do usuário de dados

Essa caixa de diálogo define quais controles aparecem na lista de controles disponíveis para itens na janela Fontes de Dados. Para abri-lo, **Tools** selecione  >  **Opções** de ferramentas e, em seguida, selecione **Designer de formulários do Windows**  >  **personalização da interface do usuário de dados**.

É possível selecionar um controle de um item na janela Fontes de Dados antes de arrastá-lo para o formulário em um aplicativo do Windows Forms. Os controles disponíveis são determinados pelo tipo de dados do item. Cada tipo de dados possui uma lista de controles associados válidos, conforme definido nessa caixa de diálogo, incluindo um controle padrão. Ao arrastar um item da janela Fontes de Dados para um formulário sem selecionar um controle, o controle padrão para o tipo de dados do item selecionado é adicionado ao formulário.

Personalize a lista de controles associados, marcando e desmarcando as caixas de seleção dos controles disponíveis para cada tipo de dados. Para adicionar um controle à lista, adicione um controle que implemente o atributo de associação de dados <xref:System.ComponentModel.DefaultBindingPropertyAttribute> ou <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> à Caixa de Ferramentas. Em seguida, o controle aparece na lista de controles para o tipo de dados. Para obter mais informações, consulte [como: adicionar controles personalizados à janela fontes de dados](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Tipo de dados

Exibe uma lista de tipos aos quais você associa controles. As tabelas são representadas como o tipo de dados `[List]`. As colunas são representadas como o tipo de dados real da coluna no armazenamento de dados subjacente.

## <a name="associated-controls"></a>Controles associados

Exibe uma lista de controles associados ao tipo de dados selecionado. Marque ou desmarque a caixa de seleção ao lado do controle para associá-la ou desassociá-la. Os controles selecionados aparecem na janela Fontes de Dados de uma coluna do banco de dados vinculada ao tipo de dados associado.

## <a name="set-default"></a>Definir Padrão

Atribui o tipo de controle selecionado para ser o padrão para o tipo de dados selecionado. O controle padrão aparece como a primeira seleção no menu de atalho para uma coluna do banco de dados na janela Fontes de Dados. Ao arrastar um item da janela Fontes de Dados para um formulário sem selecionar um controle, o controle padrão para o tipo de dados do item selecionado é adicionado ao formulário.

Somente um tipo de controle pode ser atribuído como padrão para um tipo de dados.

## <a name="clear-default"></a>Limpar Padrão

Remove a designação de um controle como padrão para o tipo de dados selecionado. Se não há um padrão para o tipo de dados selecionado, `[None]` aparece como a primeira seleção no menu de atalho para uma coluna do banco de dados desse tipo.
