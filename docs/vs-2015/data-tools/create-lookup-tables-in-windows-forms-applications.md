---
title: Criar tabelas de pesquisa em aplicativos Windows Forms | Microsoft Docs
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
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3979d08757445e9df5fc159fe7642b04bf74b995
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72630930"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Criar tabelas de pesquisa em aplicativos do Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *tabela de pesquisa* de termos descreve os controles associados a duas tabelas de dados relacionadas. Esses controles de pesquisa exibem dados da primeira tabela com base em um valor selecionado na segunda tabela.

 Você pode criar tabelas de pesquisa arrastando o nó principal de uma tabela pai (da [janela fontes de dados](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) para um controle no formulário que já esteja associado à coluna na tabela filho relacionada.

 Por exemplo, considere uma tabela de `Orders` em um banco de dados de vendas. Cada registro na `Orders` tabela inclui um `CustomerID` , indicando qual cliente fez o pedido. O `CustomerID` é uma chave estrangeira que aponta para um registro de cliente na `Customers` tabela. Nesse cenário, você expande a `Orders` tabela na janela **fontes de dados** e define o nó principal como **detalhes**. Em seguida, defina a `CustomerID` coluna para usar um <xref:System.Windows.Forms.ComboBox> (ou qualquer outro controle que dê suporte à associação de pesquisa) e arraste o `Orders` nó para o formulário. Por fim, arraste o `Customers` nó para o controle que está associado à coluna relacionada — nesse caso, o <xref:System.Windows.Forms.ComboBox> associado à `CustomerID` coluna.

## <a name="to-databind-a-lookup-control"></a>Para associar um controle de pesquisa

1. Abra a janela **fontes de dados** .

    > [!NOTE]
    > As tabelas de pesquisa exigem que duas tabelas ou objetos relacionados estejam disponíveis na janela **fontes de dados** .

2. Expanda os nós na janela **Data Sources** até que você possa ver a tabela pai e todas as suas colunas e a tabela filho relacionada e todas as suas colunas.

    > [!NOTE]
    > O nó da tabela filho é o nó que aparece como um nó filho expansível na tabela pai.

3. Altere o tipo de descarte da tabela filho para **detalhes** selecionando **detalhes** na lista de controle no nó da tabela filho. Para obter mais informações, consulte [definir o controle a ser criado ao arrastar da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Localize o nó que relaciona as duas tabelas (o `CustomerID` nó no exemplo anterior). Altere seu tipo drop para a <xref:System.Windows.Forms.ComboBox> selecionando **ComboBox** na lista de controles.

5. Arraste o nó da tabela filho principal da janela **fontes de dados** para o formulário.

     Os controles de ligação de vínculo (com rótulos descritivos) e uma faixa de ferramenta ( <xref:System.Windows.Forms.BindingNavigator> ) aparecem no formulário. Um [DataSet](../data-tools/dataset-tools-in-visual-studio.md), o TableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> aparece na bandeja do componente.

6. Agora, arraste o nó da tabela pai principal da janela **fontes de dados** diretamente para o controle de pesquisa (o <xref:System.Windows.Forms.ComboBox> ).

     As associações de pesquisa agora são estabelecidas. Consulte a tabela abaixo para obter as propriedades específicas que foram definidas no controle.

    |Propriedade|Explicação da configuração|
    |--------------|----------------------------|
    |**Fonte**|O Visual Studio define esta propriedade para o <xref:System.Windows.Forms.BindingSource> criado para a tabela que você arrasta para o controle (em oposição ao <xref:System.Windows.Forms.BindingSource> criado quando o controle foi criado).<br /><br /> Se você precisar fazer um ajuste, defina-o como o <xref:System.Windows.Forms.BindingSource> da tabela com a coluna que você deseja exibir.|
    |**DisplayMember**|O Visual Studio define essa propriedade para a primeira coluna após a chave primária que tem um tipo de dado de cadeia da tabela que você arrasta para o controle.<br /><br /> Se você precisar fazer um ajuste, defina-o como o nome da coluna que você deseja exibir.|
    |**ValueMember**|O Visual Studio define essa propriedade para a primeira coluna participante da chave primária, ou a primeira coluna na tabela, se nenhuma chave for definida.<br /><br /> Se você precisar fazer um ajuste, defina-o como a chave primária na tabela com a coluna que você deseja exibir.|
    |**SelectedValue**|O Visual Studio define essa propriedade como a coluna original descartada da janela **fontes de dados** .<br /><br /> Se você precisar fazer um ajuste, defina isso para a coluna de chave estrangeira na tabela relacionada.|

## <a name="see-also"></a>Consulte Também
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
