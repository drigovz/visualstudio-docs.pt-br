---
title: Criar tabelas de pesquisa em aplicativos do WPF | Microsoft Docs
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6816b7465b8a3271ec6ebc0db5046d76e60ec5b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657421"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Criar tabelas de pesquisa em aplicativos do WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *tabela de pesquisa* de termos (às vezes chamada de *Associação de pesquisa*) descreve um controle que exibe informações de uma tabela de dados com base no valor de um campo de chave estrangeira em outra tabela. Você pode criar uma tabela de pesquisa arrastando o nó principal de uma tabela ou objeto pai na janela **fontes de dados** para um controle já associado a uma coluna ou propriedade em uma tabela filho relacionada.

 Por exemplo, considere uma tabela de `Orders` em um banco de dados de vendas. Cada registro na tabela de `Orders` inclui um `CustomerID` que indica qual cliente fez o pedido. O `CustomerID` é uma chave estrangeira que aponta para um registro de cliente na tabela `Customers`. Ao exibir uma lista de pedidos da tabela `Orders`, talvez você queira exibir o nome do cliente real em vez do `CustomerID`. Como o nome do cliente está na tabela `Customers`, você precisa criar uma tabela de pesquisa para exibir o nome do cliente. A tabela de pesquisa usa o valor `CustomerID` no registro de `Orders` para navegar na relação e retornar o nome do cliente.

## <a name="to-create-a-lookup-table"></a>Criar uma tabela de pesquisa

1. Adicione um dos seguintes tipos de fontes de dados com dados relacionados ao seu projeto:

    - DataSet ou Modelo de Dados de Entidade.

    - WCF Data Service, serviço WCF ou serviço Web. Para obter mais informações, consulte [How to: Connect to data in a Service](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Objetos. Para obter mais informações, consulte [How to: Connect to data in Objects](https://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).

    > [!NOTE]
    > Antes que você possa criar uma tabela de pesquisa, duas tabelas ou objetos relacionados devem existir como uma fonte de dados para o projeto.

2. Abra o**designer do WPF**e certifique-se de que o designer contém um contêiner que é um destino de soltura válido para itens na janela **fontes de dados** .

     Para obter mais informações sobre destinos de destino válidos, consulte [associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

3. No menu **dados** , clique em **mostrar fontes de dados** para abrir a janela **fontes de dados** .

4. Expanda os nós na janela **fontes de dados** , até que você possa ver a tabela ou o objeto pai e a tabela ou objeto filho relacionado.

    > [!NOTE]
    > A tabela ou objeto filho relacionado é o nó que aparece como um nó filho expansível na tabela ou objeto pai.

5. Clique no menu suspenso do nó filho e selecione **detalhes**.

6. Expanda o nó filho.

7. No nó filho, clique no menu suspenso do item que relaciona os dados filho e pai. (No exemplo anterior, este é o nó **CustomerID** .) Selecione um dos seguintes tipos de controles que dão suporte à associação de pesquisa:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Se o controle **ListBox** ou **ListView** não aparecer na lista, você poderá adicionar esses controles à lista. Para obter informações, consulte [definir o controle a ser criado ao arrastar da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Qualquer controle personalizado que deriva de <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        > Para obter informações sobre como adicionar controles personalizados à lista de controles que você pode selecionar para itens na janela **fontes de dados** , consulte [Adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Arraste o nó filho da janela **fontes de dados** para um contêiner no designer do WPF. (No exemplo anterior, o nó filho é o nó **pedidos** .)

     O Visual Studio gera um XAML que cria novos controles vinculados a dados para cada um dos itens que você arrasta. O XAML também adiciona um novo <xref:System.Windows.Data.CollectionViewSource> para a tabela ou objeto filho aos recursos do destino de soltura. Para algumas fontes de dados, o Visual Studio também gera código para carregar dados na tabela ou no objeto. Para obter mais informações, consulte [associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

9. Arraste o nó pai da janela **fontes de dados** para o controle de associação de pesquisa que você criou anteriormente. (No exemplo anterior, o nó pai é o nó **Customers** ).

     O Visual Studio define algumas propriedades no controle para configurar a associação de pesquisa. A tabela a seguir lista as propriedades que o Visual Studio modifica. Se necessário, você pode alterar essas propriedades no XAML ou na janela **Propriedades** .

    |propriedade|Explicação da configuração|
    |--------------|----------------------------|
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Essa propriedade especifica a coleção ou associação que é usada para obter os dados que são exibidos no controle. O Visual Studio define essa propriedade como a <xref:System.Windows.Data.CollectionViewSource> para os dados pai que você arrastou para o controle.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Esta propriedade especifica o caminho do item de dados que é exibido no controle. O Visual Studio define essa propriedade como a primeira coluna ou propriedade nos dados pai, após a chave primária, que tem um tipo de dados de cadeia de caracteres.<br /><br /> Se você quiser exibir uma coluna ou propriedade diferente nos dados pai, altere essa propriedade para o caminho de uma propriedade diferente.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|O Visual Studio associa essa propriedade à coluna ou à propriedade dos dados filho que você arrastou para o designer. Essa é a chave estrangeira para os dados pai.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|O Visual Studio define essa propriedade como o caminho da coluna ou da propriedade dos dados filho que são a chave estrangeira para os dados pai.|

## <a name="see-also"></a>Consulte também
 [Associar controles do WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [associar controles do WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [exibir dados relacionados em aplicativos WPF](../data-tools/display-related-data-in-wpf-applications.md) [Walkthrough: Exibindo dados relacionados em um aplicativo do WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
