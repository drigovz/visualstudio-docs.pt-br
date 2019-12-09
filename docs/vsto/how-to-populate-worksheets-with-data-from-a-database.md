---
title: 'Como: preencher planilhas com dados de um banco de dado'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a1e01f5c9fc1372cda4d7d31f8ba56b90e166e7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985854"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Como: preencher planilhas com dados de um banco de dado

Você pode acessar dados em projetos do Office de nível de documento da mesma maneira que acessa dados em projetos Windows Forms. Você usa as mesmas ferramentas e código para colocar os dados em sua solução, e você pode até mesmo usar Windows Forms controles para exibir os dados. Além disso, você pode aproveitar os controles chamados de controles de host, que são objetos nativos no Microsoft Office Excel que foram aprimorados com eventos e capacidade de vinculação de dados. Para obter mais informações, consulte [visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

O exemplo a seguir mostra como adicionar controles vinculados a dados em projetos de nível de documento usando um designer. Para obter um exemplo de como adicionar controles vinculados a dados em projetos de nível de aplicativo em tempo de execução, consulte [passo a passos: Associação de dados complexa no projeto de suplemento do VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Adicionar um controle de vinculação de dados a uma planilha no tempo de design

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Para preencher uma planilha com dados de um banco de dado

1. Abra um projeto de nível de documento do Excel no Visual Studio, com a planilha aberta no designer.

2. Abra a janela **Data Sources** e crie uma fonte de dados para seu projeto. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).

3. Arraste o campo ou tabela desejado da janela **fontes de dados** para a planilha.

Um dos seguintes controles é criado na planilha:

- Se você arrastar um campo, um controle de <xref:Microsoft.Office.Tools.Excel.NamedRange> será criado na planilha. Para obter mais informações, consulte [controle NamedRange](../vsto/namedrange-control.md).

- Se você arrastar uma tabela, um controle de <xref:Microsoft.Office.Tools.Excel.ListObject> será criado na planilha. Para obter mais informações, consulte o [controle ListObject](../vsto/listobject-control.md).

Você pode adicionar um controle diferente selecionando a tabela ou o campo na janela **fontes de dados** e escolhendo um controle diferente na lista suspensa.

## <a name="objects-in-the-project"></a>Objetos no projeto

Além do controle, os seguintes objetos relacionados a dados são adicionados automaticamente ao seu projeto:

- Um dataset tipado que encapsula as tabelas de dados às quais você se conectou no Database. Para obter mais informações, consulte [ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Um <xref:System.Windows.Forms.BindingSource> que conecta o controle ao dataset tipado. Para obter mais informações, consulte [visão geral do componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- Um TableAdapter que conecta o dataset tipado ao banco de dados. Para obter mais informações, consulte [visão geral do TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

- Um TableAdaptermanager, que é usado para coordenar adaptadores de tabela no conjunto de conjuntos para habilitar atualizações hierárquicas. Para obter mais informações, consulte [atualização hierárquica](../data-tools/hierarchical-update.md) e [referência do TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Quando você executa o projeto, o controle exibe o primeiro registro na fonte de dados. Você pode usar o <xref:System.Windows.Forms.BindingSource> para permitir que os usuários percorram os registros.

### <a name="to-scroll-through-the-records"></a>Para percorrer os registros

- Use <xref:System.Windows.Forms.BindingSource> métodos como <xref:System.Windows.Forms.BindingSource.MoveNext%2A> e <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Para obter informações sobre como enviar atualizações para o dataset tipado e o banco de [dados, consulte How to: Update a data source with data of a host Control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Consulte também

- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)
- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Como: popular documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Como: popular documentos com dados de um banco de dado](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Como: popular documentos com dados de serviços](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Como: atualizar uma fonte de dados com dados de um controle de host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)