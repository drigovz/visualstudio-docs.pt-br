---
title: Visão geral do modelo do Excel Object
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a823692a5cc0f154c514edff4fe9398de0efd212
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649419"
---
# <a name="excel-object-model-overview"></a>Visão geral do modelo de objeto excel
  Para desenvolver soluções que usam o Microsoft Office Excel, você pode interagir com os objetos fornecidos pelo modelo de objeto excel. Este tópico introduz os objetos mais importantes:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  O modelo de objeto segue de perto a interface do usuário. O <xref:Microsoft.Office.Interop.Excel.Application> objeto representa toda a <xref:Microsoft.Office.Interop.Excel.Workbook> aplicação, e `Worksheet` cada objeto contém uma coleção de objetos. A partir daí, a maior abstração que <xref:Microsoft.Office.Interop.Excel.Range> representa as células é o objeto, que permite trabalhar com células individuais ou grupos de células.

  Além do modelo de objeto excel, os projetos do Office no Visual Studio fornecem *itens de host* e controles de host que estendem *alguns objetos* no modelo de objeto excel. Os itens de host e os controles de host se comportam como os objetos excel que estendem, mas também têm funcionalidades adicionais, como recursos de vinculação de dados e eventos extras. Para obter mais informações, consulte [Automate Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md) e [itens host e controles de host visão geral](../vsto/host-items-and-host-controls-overview.md).

  Este tópico fornece uma breve visão geral do modelo de objeto excel. Para obter recursos onde você pode aprender mais sobre todo o modelo de objeto do Excel, consulte [Usar a documentação do modelo de objeto excel](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Acesso a objetos em um projeto de Excel
 Quando você cria um novo projeto de complemento VSTO para excel, o Visual Studio cria automaticamente um arquivo de código *ThisAddIn.vb* ou *ThisAddIn.cs.* Você pode acessar o `Me.Application` objeto `this.Application`do Aplicativo usando ou .

 Quando você cria um novo projeto de nível de documento para o Excel, você tem a opção de criar um novo projeto de Pasta de Trabalho do Excel ou modelo de Excel. O Visual Studio cria automaticamente os seguintes arquivos de código em seu novo projeto excel para projetos de pasta de trabalho e modelo.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|Thisworkbook.cs|
|Sheetsheet1.vb|Sheet1.cs|
|Sheet2.vb|Sheet2.cs|
|Sheet3.vb|Sheet3.cs|

 Você pode `Globals` usar a classe `ThisWorkbook`em `Sheet1` `Sheet2`seu `Sheet3` projeto para acessar, ou de fora da respectiva classe. Para obter mais informações, consulte [O acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md). O exemplo a <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> seguir `Sheet1` chama o método de independentemente `Sheet`de o `ThisWorkbook` código ser colocado em uma das classes *n* ou na classe.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Como os dados em um documento excel são altamente estruturados, o modelo de objeto é hierárquico e simples. O Excel fornece centenas de objetos com os quais você pode querer interagir, mas você pode obter um bom começo no modelo de objeto, focando em um pequeno subconjunto dos objetos disponíveis. Esses objetos incluem os quatro seguintes:

- Aplicativo

- Pasta de trabalho

- Planilha

- Intervalo

  Grande parte do trabalho feito com o Excel gira em torno desses quatro objetos e seus membros.

### <a name="application-object"></a>Objeto de aplicativo
 O <xref:Microsoft.Office.Interop.Excel.Application> objeto Excel representa o próprio aplicativo Excel. O <xref:Microsoft.Office.Interop.Excel.Application> objeto expõe uma grande quantidade de informações sobre o aplicativo em execução, as opções aplicadas a essa instância e os objetos de usuário atuais abertos dentro da instância.

> [!NOTE]
> Você não deve <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> definir <xref:Microsoft.Office.Interop.Excel.Application> a propriedade do objeto no Excel como **falsa**. Definir essa propriedade como falsa impede que o Excel eime quaisquer eventos, incluindo os eventos de controles de host.

### <a name="workbook-object"></a>Objeto da carteira de trabalho
 O <xref:Microsoft.Office.Interop.Excel.Workbook> objeto representa uma única pasta de trabalho dentro do aplicativo Excel.

 As ferramentas de desenvolvimento do <xref:Microsoft.Office.Interop.Excel.Workbook> Office no <xref:Microsoft.Office.Tools.Excel.Workbook> Visual Studio estendem o objeto fornecendo o tipo. Este tipo lhe dá acesso <xref:Microsoft.Office.Interop.Excel.Workbook> a todos os recursos de um objeto. Para obter mais informações, consulte [o item host da Agenda de Trabalho](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Objeto de planilha
 O <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto é um <xref:Microsoft.Office.Interop.Excel.Worksheets> membro da coleção. Muitas das propriedades, métodos e <xref:Microsoft.Office.Interop.Excel.Worksheet> eventos do são idênticos ou <xref:Microsoft.Office.Interop.Excel.Application> <xref:Microsoft.Office.Interop.Excel.Workbook> semelhantes aos membros fornecidos pelos ou objetos.

 O Excel <xref:Microsoft.Office.Interop.Excel.Sheets> fornece uma coleção <xref:Microsoft.Office.Interop.Excel.Workbook> como propriedade de um objeto. Cada membro <xref:Microsoft.Office.Interop.Excel.Sheets> da coleção <xref:Microsoft.Office.Interop.Excel.Worksheet> é <xref:Microsoft.Office.Interop.Excel.Chart> um ou um objeto.

 As ferramentas de desenvolvimento do <xref:Microsoft.Office.Interop.Excel.Worksheet> Office no <xref:Microsoft.Office.Tools.Excel.Worksheet> Visual Studio estendem o objeto fornecendo o tipo. Esse tipo lhe dá acesso <xref:Microsoft.Office.Interop.Excel.Worksheet> a todos os recursos de um objeto, bem como novos recursos, como a capacidade de hospedar controles gerenciados e lidar com novos eventos. Para obter mais informações, consulte [o item host da planilha](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Objeto de intervalo
 O <xref:Microsoft.Office.Interop.Excel.Range> objeto é o objeto que você mais usará dentro de seus aplicativos Excel. Antes de manipular qualquer região dentro do Excel, você deve expressá-lo como um <xref:Microsoft.Office.Interop.Excel.Range> objeto e trabalhar com métodos e propriedades desse intervalo. Um <xref:Microsoft.Office.Interop.Excel.Range> objeto representa uma célula, uma linha, uma coluna, uma seleção de células que contêm um ou mais blocos de células, que podem ou não ser contíguas, ou mesmo um grupo de células em várias folhas.

 O Visual <xref:Microsoft.Office.Interop.Excel.Range> Studio estende <xref:Microsoft.Office.Tools.Excel.NamedRange> o <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> objeto fornecendo e tipos. Esses tipos têm a maioria <xref:Microsoft.Office.Interop.Excel.Range> dos mesmos recursos que um objeto, bem como novos recursos, como o recurso de vinculação de dados e novos eventos. Para obter mais informações, consulte [o controle NamedRange](../vsto/namedrange-control.md) e [o controle XmlMappedRange](../vsto/xmlmappedrange-control.md).

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a>Use a documentação do modelo de objeto Excel
 Para obter informações completas sobre o modelo de objeto Excel, você pode consultar a referência PIA (Primary Interop Assembly, conjunto de interop primário) do Excel e a referência do modelo de objeto VBA.

### <a name="primary-interop-assembly-reference"></a>Referência primária de montagem interop
 A documentação de referência do Excel PIA descreve os tipos no conjunto de interop primário para Excel. Esta documentação está disponível no seguinte local: [Excel 2010 referência de montagem de interop primária](office-primary-interop-assemblies.md).

 Para obter mais informações sobre o design do Excel PIA, como as diferenças entre classes e interfaces no PIA e como os eventos no PIA são [implementados, consulte Visão Geral das classes e interfaces nos conjuntos de interop primários do Office.](/previous-versions/office/office-12/ms247299(v=office.12))

### <a name="vba-object-model-reference"></a>Referência do modelo de objeto VBA
 A referência do modelo de objeto VBA documenta o modelo de objeto Excel, pois ele é exposto ao código Visual Basic for Applications (VBA). Para obter mais informações, consulte [a referência do modelo de objeto excel 2010](/office/vba/api/overview/Excel/object-model).

 Todos os objetos e membros da referência do modelo de objeto VBA correspondem a tipos e membros no Excel PIA. Por exemplo, o objeto Planilha na referência do modelo <xref:Microsoft.Office.Interop.Excel.Worksheet> de objeto VBA corresponde ao objeto no Excel PIA. Embora a referência do modelo de objeto VBA forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve traduzir o código VBA nesta referência ao Visual Basic ou Visual C# se você quiser usá-los em um projeto de Excel que você cria usando o Visual Studio.

### <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Soluções excel](../vsto/excel-solutions.md)|Explica como você pode criar personalizações em nível de documento e complementos vsto para o Microsoft Office Excel.|
|[Trabalhe com faixas](../vsto/working-with-ranges.md)|Fornece exemplos que mostram como executar tarefas comuns com intervalos.|
|[Trabalhe com planilhas](../vsto/working-with-worksheets.md)|Fornece exemplos que mostram como executar tarefas comuns com planilhas.|
|[Trabalhe com livros de trabalho](../vsto/working-with-workbooks.md)|Fornece exemplos que mostram como executar tarefas comuns com livros de trabalho.|
