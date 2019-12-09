---
title: Exibir dados relacionados em aplicativos do WPF | Microsoft Docs
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
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6efa79fc59ed9812cf6162096dd462100b71fbca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672409"
---
# <a name="display-related-data-in-wpf-applications"></a>Exibir dados relacionados em aplicativos WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em alguns aplicativos, talvez você queira trabalhar com dados provenientes de várias tabelas ou entidades relacionadas entre si em uma relação pai-filho. Por exemplo, talvez você queira exibir uma grade que exibe os clientes de uma tabela `Customers`. Quando o usuário seleciona um cliente específico, outra grade exibe os pedidos desse cliente de uma tabela de `Orders` relacionada.

 Você pode criar controles vinculados a dados que exibem dados relacionados arrastando itens da janela **fontes de dados** para o designer do WPF.

## <a name="to-create-controls-that-display-related-records"></a>Para criar controles que exibem registros relacionados

1. No menu **dados** , clique em **mostrar fontes de dados** para abrir a janela **fontes de dados** .

2. Clique em **Adicionar Nova Fonte de Dados** e complete o **Assistente de Configuração de Fonte de Dados**.

3. Abra o designer do WPF e certifique-se de que o designer contém um contêiner que é um destino de soltura válido para os itens na janela **fontes de dados** .

     Para obter mais informações sobre destinos de destino válidos, consulte [associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

4. Na janela **fontes de dados** , expanda o nó que representa a tabela ou o objeto pai na relação. A tabela ou o objeto pai está no lado "um" de uma relação um-para-muitos.

5. Arraste o nó pai (ou quaisquer itens individuais no nó pai) da janela **fontes de dados** para um destino de soltura válido no designer.

     O Visual Studio gera um XAML que cria novos controles vinculados a dados para cada item que você arrasta. O XAML também adiciona um novo <xref:System.Windows.Data.CollectionViewSource> para a tabela ou objeto pai aos recursos do destino de soltura. Para algumas fontes de dados, o Visual Studio também gera código para carregar os dados na tabela ou no objeto pai. Para obter mais informações, consulte [associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. Na janela **fontes de dados** , localize a tabela ou o objeto filho relacionado. As tabelas e os objetos filho relacionados aparecem como nós expansíveis na parte inferior da lista de dados do nó pai.

7. Arraste o nó filho (ou qualquer item individual no nó filho) da janela **fontes de dados** para um destino de soltura válido no designer.

     O Visual Studio gera um XAML que cria novos controles vinculados a dados para cada um dos itens que você arrasta. O XAML também adiciona um novo <xref:System.Windows.Data.CollectionViewSource> para a tabela ou objeto filho aos recursos do destino de soltura. Essa nova <xref:System.Windows.Data.CollectionViewSource> está associada à propriedade da tabela ou objeto pai que você acabou de arrastar para o designer. Para algumas fontes de dados, o Visual Studio também gera código para carregar os dados na tabela ou no objeto filho.

     A figura a seguir demonstra a tabela de **pedidos** relacionados da tabela **Customers** em um conjunto de dados na janela **Data Sources** .

     ![Janela fontes de dados mostrando a relação](../data-tools/media/datasources2.gif "DataSources2")

## <a name="see-also"></a>Consulte também
 [Associar controles do WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [associar controles do WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [criar tabelas de pesquisa em aplicativos WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [Walkthrough: Exibindo dados relacionados em um aplicativo do WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
