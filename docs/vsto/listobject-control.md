---
title: Controle ListObject
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b5286a4bddff2b529abd0a565bb4dbeef7ffaf3
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251863"
---
# <a name="listobject-control"></a>Controle ListObject
  O <xref:Microsoft.Office.Tools.Excel.ListObject> controle é uma lista que expõe eventos e pode ser associada a dados. Quando você adiciona uma lista a uma planilha, o Visual Studio cria <xref:Microsoft.Office.Tools.Excel.ListObject> um controle que você pode programar diretamente sem precisar atravessar o Microsoft Office modelo de objeto do Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Criar o controle
 Em projetos de nível de documento, você pode <xref:Microsoft.Office.Tools.Excel.ListObject> adicionar controles a uma planilha em tempo de design ou em tempo de execução. Em projetos de suplemento do VSTO, você pode adicionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles a planilhas somente em tempo de execução. Para obter mais informações, confira [Como: Adicione controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md).

> [!NOTE]
> Por padrão, os objetos de lista criados dinamicamente não são mantidos na planilha como controles de host quando a planilha é fechada. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="bind-data-to-the-control"></a>Associar dados ao controle
 Um <xref:Microsoft.Office.Tools.Excel.ListObject> controle dá suporte à ligação de dados simples e complexa. O <xref:Microsoft.Office.Tools.Excel.ListObject> controle pode ser associado a uma fonte de dados usando <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> as <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> Propriedades e em tempo de design <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> ou o método em tempo de execução.

> [!NOTE]
> O <xref:Microsoft.Office.Tools.Excel.ListObject> é atualizado automaticamente quando está associado a uma fonte de dados, como um <xref:System.Data.DataTable>, que gera eventos quando os dados são alterados. Se você associar o <xref:Microsoft.Office.Tools.Excel.ListObject> a uma fonte de dados que não gera eventos quando os dados são alterados, você deve chamar <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> o <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> método ou para atualizar <xref:Microsoft.Office.Tools.Excel.ListObject>o.

 Quando você adiciona um <xref:Microsoft.Office.Tools.Excel.ListObject> a uma célula de planilha mapeando um elemento de esquema repetido para essa célula, o Visual <xref:Microsoft.Office.Tools.Excel.ListObject> Studio mapeia automaticamente o para o conjunto de os gerado. No entanto <xref:Microsoft.Office.Tools.Excel.ListObject> , o não é associado automaticamente aos dados. Você pode executar etapas para associar o <xref:Microsoft.Office.Tools.Excel.ListObject> ao conjunto de data em tempo de design ou em tempo de execução em um projeto de nível de documento. Você pode associar programaticamente o <xref:Microsoft.Office.Tools.Excel.ListObject> ao conjunto de data em tempo de execução em um suplemento do VSTO.

 Como os dados são separados do <xref:Microsoft.Office.Tools.Excel.ListObject>, você deve adicionar e remover dados por meio do DataSet associado, e não diretamente por meio do. <xref:Microsoft.Office.Tools.Excel.ListObject> Se os dados no DataSet associado forem atualizados por meio de qualquer mecanismo, <xref:Microsoft.Office.Tools.Excel.ListObject> o controle refletirá automaticamente as alterações. Para obter mais informações, consulte [associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Você pode preencher rapidamente um <xref:Microsoft.Office.Tools.Excel.ListObject> controle ligando o <xref:Microsoft.Office.Tools.Excel.ListObject> a uma fonte de dados. Se você editar os dados em uma associação <xref:Microsoft.Office.Tools.Excel.ListObject>de dados, as alterações também serão feitas automaticamente na fonte de dados. <xref:Microsoft.Office.Tools.Excel.ListObject> Se desejar preencher um e, em seguida, permitir que o usuário altere os dados <xref:Microsoft.Office.Tools.Excel.ListObject> no sem modificar a fonte de dados, você poderá usar <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> o método para desanexar o <xref:Microsoft.Office.Tools.Excel.ListObject> da fonte de dados. Para obter mais informações, confira [Como: Preencha os controles ListObject com](../vsto/how-to-fill-listobject-controls-with-data.md)dados.

> [!NOTE]
> A vinculação de dados não tem suporte em <xref:Microsoft.Office.Tools.Excel.ListObject> controles sobrepostos.

### <a name="improve-performance-in-listobject-controls"></a>Melhorar o desempenho em controles ListObject
 A leitura de um arquivo XML em um controle <xref:Microsoft.Office.Tools.Excel.ListObject> vinculado a dados tende a ser mais lenta se você ligar o controle primeiro e, <xref:System.Data.DataSet.ReadXml%2A> em seguida, chamar para preencher o DataSet. Para melhorar o desempenho, <xref:System.Data.DataSet.ReadXml%2A> chame antes de associar o controle.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>Desconectar controles ListObject da fonte de dados
 Depois de preencher um <xref:Microsoft.Office.Tools.Excel.ListObject> controle com dados ligando-o a uma fonte de dados, você pode desconectá-lo para que as modificações feitas nos dados no objeto de lista não afetem a fonte de dados. Para obter mais informações, confira [Como: Preencha os controles ListObject com](../vsto/how-to-fill-listobject-controls-with-data.md)dados.

### <a name="restore-column-and-row-order"></a>Restaurar ordem de coluna e linha
 Quando você associa dados a um <xref:Microsoft.Office.Tools.Excel.ListObject> controle que foi adicionado a um documento em tempo de design, o Visual Studio controla a ordem da coluna e da linha sempre que a pasta de trabalho é salva. Se um usuário mover as <xref:Microsoft.Office.Tools.Excel.ListObject> colunas ou linhas durante o tempo de execução, o novo pedido será preservado na próxima vez em que a <xref:Microsoft.Office.Tools.Excel.ListObject> pasta de trabalho for aberta e o controle será associado à fonte de dados novamente.

 Se você quiser restaurar o <xref:Microsoft.Office.Tools.Excel.ListObject> para sua coluna original e ordem de linha, você pode chamar o <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> método. Esse método remove as propriedades de documento personalizadas relacionadas à ordem de coluna e linha de <xref:Microsoft.Office.Tools.Excel.ListObject>especificada. Chame esse método do <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> evento da pasta de trabalho se você não quiser preservar a ordem da coluna e <xref:Microsoft.Office.Tools.Excel.ListObject>da linha do.

## <a name="format"></a>Formatar
 A formatação que pode ser aplicada a <xref:Microsoft.Office.Interop.Excel.ListObject> um pode ser aplicada a <xref:Microsoft.Office.Tools.Excel.ListObject> um controle. Isso inclui bordas, fontes, formato de número e estilos. Os usuários finais podem reorganizar as colunas em uma associação <xref:Microsoft.Office.Tools.Excel.ListObject>de dados e essas alterações serão persistidas com o documento, desde que <xref:Microsoft.Office.Tools.Excel.ListObject> o tenha sido adicionado ao documento em tempo de design. Na próxima vez em que o documento for aberto, o objeto de lista será vinculado à mesma fonte de dados, mas a ordem das colunas refletirá as alterações dos usuários.

## <a name="add-and-remove-columns-at-run-time"></a>Adicionar e remover colunas em tempo de execução
 Você não pode adicionar ou remover manualmente colunas em um controle de <xref:Microsoft.Office.Tools.Excel.ListObject> vinculação de dados em tempo de execução. Se um usuário final tentar excluir uma coluna, ela será imediatamente restaurada e todas as colunas adicionadas serão removidas. Portanto, é importante escrever código para explicar aos usuários por que eles não podem executar essas ações em um <xref:Microsoft.Office.Tools.Excel.ListObject> associado a dados. O Visual Studio fornece vários eventos em <xref:Microsoft.Office.Tools.Excel.ListObject> uma associação de dados relacionada à. Por exemplo, você pode usar o <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> evento para avisar os usuários que os dados que eles tentaram excluir não podem ser excluídos e restaurados.

## <a name="add-and-remove-rows-at-run-time"></a>Adicionar e remover linhas em tempo de execução
 Você pode adicionar e remover linhas manualmente em um controle associado <xref:Microsoft.Office.Tools.Excel.ListObject> a dados, desde que a fonte de dados permita a adição de novas linhas e não seja somente leitura. Você pode escrever código em relação a eventos como <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> o para validar os dados. Para obter mais informações, confira [Como: Validar dados quando uma nova linha for adicionada a um controle](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)ListObject.

 Às vezes, a relação do objeto de lista com a fonte de dados causa erros de rotina. Por exemplo, você pode mapear quais colunas você deseja que apareçam <xref:Microsoft.Office.Tools.Excel.ListObject>no, portanto, se você omitir colunas com restrições, como um campo que não pode aceitar valores nulos, os erros serão gerados sempre que uma linha for criada. Você pode escrever código para adicionar os valores ausentes em um manipulador de eventos <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> para o evento.

## <a name="rename-listobject-controls-in-excel"></a>Renomear controles ListObject no Excel
 O Excel permite que os usuários alterem o nome de tabelas do Excel em tempo de execução usando a guia **design** . No entanto <xref:Microsoft.Office.Tools.Excel.ListObject> , o controle não oferece suporte a esse recurso. Se um usuário tentar renomear uma tabela do Excel que corresponda <xref:Microsoft.Office.Tools.Excel.ListObject>a um, o nome da tabela do Excel será revertido automaticamente para o nome original quando a pasta de trabalho for salva.

## <a name="events"></a>Eventos
 Os eventos a seguir estão disponíveis para <xref:Microsoft.Office.Tools.Excel.ListObject> o controle:

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Change>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>

## <a name="see-also"></a>Consulte também
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Como: Adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Como: Redimensionar controles ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Como: Validar dados quando uma nova linha for adicionada a um controle ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Como: Mapear colunas ListObject para dados](../vsto/how-to-map-listobject-columns-to-data.md)
- [Como: Preencher controles ListObject com dados](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Como: Preencher planilhas com dados de um banco de dado](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
