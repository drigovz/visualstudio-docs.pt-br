---
title: Associar controles de Windows Forms a dados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672972"
---
# <a name="bind-windows-forms-controls-to-data"></a>Associar controles do Windows Forms a dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode associar fontes de dados a controles arrastando objetos da janela **fontes de dados** para um formulário do Windows ou para um controle existente em um formulário. Antes de arrastar itens, você pode definir o tipo de controle ao qual deseja associar. Valores diferentes aparecem dependendo se você escolher a própria tabela ou uma coluna individual.  Você também pode definir valores personalizados. Para uma tabela, "detalhes" significa que cada coluna está associada a um controle separado.

 ![Associar fonte de dados ao DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata associar fonte de dados ao DataGridView")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>Associar a dados em um controle DataGridView
 Para DataGridView, a tabela inteira é associada a esse controle único. Quando você arrasta um DataGridView para o formulário, uma faixa de ferramenta para os registros de navegação ( <xref:System.Windows.Forms.BindingNavigator> ) também é exibida. Um [DataSet](../data-tools/dataset-tools-in-visual-studio.md), o TableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> aparece na bandeja do componente. Na ilustração a seguir, um TableAdaptermanager também é adicionado porque a tabela Customers tem uma relação com a tabela Orders. Essas variáveis são todas declaradas no código gerado automaticamente como membros privados na classe Form. O código gerado automaticamente para preencher o DataGridView está localizado no manipulador de eventos form_load. O código para salvar os dados para atualizar o banco de dado está localizado no manipulador de eventos Save do BindingNavigator. Você pode mover ou modificar esse código conforme necessário.

 ![GridView com BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView com BindingNavigator")

 Você pode personalizar o comportamento do DataGridView e do BindingNavigator clicando na marca inteligente no canto superior direito de cada um:

 ![DataGridView e marcas inteligentes do navegador de associação](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView e marcas inteligentes do navegador de associação")

 Se os controles de que seu aplicativo precisa não estiverem disponíveis na janela **fontes de dados** , você poderá adicionar controles. Para obter mais informações, consulte [Adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).

 Você também pode arrastar itens da janela **fontes de dados** para controles que já estão em um formulário para associar o controle aos dados. Um controle que já está associado a dados tem suas associações de dados redefinidas para o item arrastado mais recentemente para ele. Para serem destinos de destino válidos, os controles devem ser capazes de exibir o tipo de dados subjacente do item arrastado para ele na janela **fontes de dados** . Por exemplo, não é válido arrastar um item que tenha um tipo de dados <xref:System.DateTime> para um <xref:System.Windows.Forms.CheckBox> , porque o <xref:System.Windows.Forms.CheckBox> não é capaz de exibir uma data.

## <a name="bind-to--data-in-individual-controls"></a>Associar a dados em controles individuais
 Quando você associa uma fonte de dados a "detalhes", cada coluna no conjunto é associada a um controle separado.

 ![Associar fonte de dados a detalhes](../data-tools/media/raddata-bind-data-source-to-details.png "raddata associar fonte de dados a detalhes")

> [!IMPORTANT]
> Observe que, na ilustração anterior, você arrasta da propriedade Orders da tabela Customers, não da tabela Orders. Ligando-se à propriedade Customer. Orders, os comandos de navegação feitos no DataGridView são refletidos imediatamente nos controles details. Se você arrastou da tabela Orders, os controles ainda seriam associados ao conjunto de um, mas não seriam sincronizados com o DataGridView.

 A ilustração a seguir mostra os controles associados a dados padrão que são adicionados ao formulário depois que a propriedade Orders na tabela Customers é associada a "Details" na janela **Data Sources** .

 ![Tabela de pedidos associada a detalhes](../data-tools/media/raddata-orders-table-bound-to-details.png "tabela de pedidos do raddata associada a detalhes")

 Observe também que cada controle tem uma marca inteligente. Essa marca permite personalizações que se aplicam somente ao controle.

## <a name="see-also"></a>Consulte Também
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
