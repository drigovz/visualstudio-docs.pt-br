---
title: Visão geral do modelo de objeto do Excel
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
ms.openlocfilehash: 6d7371880c739e242bcdd70fb2bb9ac0cd92677b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551588"
---
# <a name="excel-object-model-overview"></a>Visão geral do modelo de objeto do Excel
  Para desenvolver soluções que usam o Microsoft Office Excel, você pode interagir com os objetos fornecidos pelo modelo de objeto do Excel. Este tópico apresenta os objetos mais importantes:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  O modelo de objeto segue com mais detalhes a interface do usuário. O <xref:Microsoft.Office.Interop.Excel.Application> objeto representa o aplicativo inteiro e cada <xref:Microsoft.Office.Interop.Excel.Workbook> objeto contém uma coleção de `Worksheet` objetos. A partir daí, a abstração principal que representa as células <xref:Microsoft.Office.Interop.Excel.Range> é o objeto, que permite que você trabalhe com células individuais ou grupos de células.

  Além do modelo de objeto do Excel, os projetos do Office no Visual Studio fornecem *itens de host* e *controles de host* que estendem alguns objetos no modelo de objeto do Excel. Os itens de host e os controles de host se comportam como os objetos do Excel que eles estendem, mas também têm funcionalidade adicional, como recursos de ligação de dados e eventos extras. Para saber mais, confira automatizar o [Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md) e [itens de host e visão geral de controles de host](../vsto/host-items-and-host-controls-overview.md).

  Este tópico fornece uma breve visão geral do modelo de objeto do Excel. Para obter recursos em que você pode aprender mais sobre o modelo de objeto do Excel inteiro, consulte [usar a documentação do modelo de objeto do Excel](#ExcelOMDocumentation).

  ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") Para ver uma demonstração de vídeo relacionada [, consulte Como fazer: Usar manipuladores de eventos em um suplemento do Excel 2007? ](http://go.microsoft.com/fwlink/?LinkID=130291) e[como fazer: Usar formas para criar um gráfico de bolhas no Excel? ](http://go.microsoft.com/fwlink/?LinkID=130313).

## <a name="access-objects-in-an-excel-project"></a>Acessar objetos em um projeto do Excel
 Quando você cria um novo projeto de suplemento do VSTO para Excel, o Visual Studio cria automaticamente um arquivo de código *ThisAddIn. vb* ou *ThisAddIn.cs* . Você pode acessar o objeto de aplicativo usando `Me.Application` o `this.Application`ou o.

 Ao criar um novo projeto de nível de documento para o Excel, você tem a opção de criar uma nova pasta de trabalho do Excel ou um projeto de modelo do Excel. O Visual Studio cria automaticamente os seguintes arquivos de código em seu novo projeto do Excel para projetos de pasta de trabalho e modelo.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Plan1. vb|Sheet1.cs|
|Planilha2. vb|Sheet2.cs|
|Sheet3. vb|Sheet3.cs|

 Você pode usar a `Globals` classe em seu projeto para acessar `ThisWorkbook`, `Sheet1`, `Sheet2`ou `Sheet3` de fora da respectiva classe. Para obter mais informações, consulte [acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md). O exemplo a seguir chama <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> o método `Sheet1` de não importa se o código é `Sheet`colocado em uma das classes *n* ou na `ThisWorkbook` classe.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Como os dados em um documento do Excel são altamente estruturados, o modelo de objeto é hierárquico e direto. O Excel fornece centenas de objetos com os quais você pode querer interagir, mas você pode obter um bom começo do modelo de objeto concentrando-se em um pequeno subconjunto dos objetos disponíveis. Esses objetos incluem os quatro seguintes:

- Aplicativo

- Pastas de trabalho

- Planilha

- Intervalo

  Grande parte do trabalho feito com os centros do Excel em relação a esses quatro objetos e seus membros.

### <a name="application-object"></a>Objeto de aplicativo
 O objeto <xref:Microsoft.Office.Interop.Excel.Application> Excel representa o próprio aplicativo do Excel. O <xref:Microsoft.Office.Interop.Excel.Application> objeto apresenta uma grande quantidade de informações sobre o aplicativo em execução, as opções aplicadas a essa instância e os objetos de usuário atuais abertos na instância do.

> [!NOTE]
> Você não deve definir a <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> propriedade <xref:Microsoft.Office.Interop.Excel.Application> do objeto no Excel como **false**. Definir essa propriedade como false impede que o Excel disparasse qualquer evento, incluindo os eventos de controles de host.

### <a name="workbook-object"></a>Objeto de pasta de trabalho
 O <xref:Microsoft.Office.Interop.Excel.Workbook> objeto representa uma única pasta de trabalho dentro do aplicativo do Excel.

 As ferramentas de desenvolvimento do Office no Visual Studio <xref:Microsoft.Office.Interop.Excel.Workbook> estendem o <xref:Microsoft.Office.Tools.Excel.Workbook> objeto fornecendo o tipo. Esse tipo fornece acesso a todos os recursos de um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto. Para obter mais informações, veja [item de host da pasta de trabalho](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Objeto de planilha
 O <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto é um membro <xref:Microsoft.Office.Interop.Excel.Worksheets> da coleção. Muitas das propriedades, métodos e eventos do <xref:Microsoft.Office.Interop.Excel.Worksheet> são idênticos ou semelhantes aos membros fornecidos <xref:Microsoft.Office.Interop.Excel.Application> pelos objetos ou <xref:Microsoft.Office.Interop.Excel.Workbook> .

 O Excel fornece <xref:Microsoft.Office.Interop.Excel.Sheets> uma coleção como uma propriedade de <xref:Microsoft.Office.Interop.Excel.Workbook> um objeto. Cada membro da <xref:Microsoft.Office.Interop.Excel.Sheets> coleção é um <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> objeto ou.

 As ferramentas de desenvolvimento do Office no Visual Studio <xref:Microsoft.Office.Interop.Excel.Worksheet> estendem o <xref:Microsoft.Office.Tools.Excel.Worksheet> objeto fornecendo o tipo. Esse tipo fornece acesso a todos os recursos de um <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto, bem como novos recursos, como a capacidade de hospedar controles gerenciados e lidar com novos eventos. Para obter mais informações, consulte [planilha de item de host](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Objeto de intervalo
 O <xref:Microsoft.Office.Interop.Excel.Range> objeto é o objeto que você usará mais em seus aplicativos do Excel. Antes de poder manipular qualquer região no Excel, você deve exexpressá- <xref:Microsoft.Office.Interop.Excel.Range> la como um objeto e trabalhar com métodos e propriedades desse intervalo. Um <xref:Microsoft.Office.Interop.Excel.Range> objeto representa uma célula, uma linha, uma coluna, uma seleção de células que contém um ou mais blocos de células, que podem ou não ser contíguos ou até mesmo um grupo de células em várias planilhas.

 O Visual Studio estende <xref:Microsoft.Office.Interop.Excel.Range> o objeto fornecendo os <xref:Microsoft.Office.Tools.Excel.NamedRange> tipos <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> e. Esses tipos têm a maioria dos mesmos recursos que um <xref:Microsoft.Office.Interop.Excel.Range> objeto, bem como novos recursos, como a capacidade de vinculação de dados e novos eventos. Para obter mais informações, consulte [controle NamedRange](../vsto/namedrange-control.md) e [controle XmlMappedRange](../vsto/xmlmappedrange-control.md).

## <a name="ExcelOMDocumentation"></a>Usar a documentação do modelo de objeto do Excel
 Para obter informações completas sobre o modelo de objeto do Excel, consulte a referência do assembly de interoperabilidade primária do Excel (PIA) e a referência do modelo de objeto do VBA.

### <a name="primary-interop-assembly-reference"></a>Referência de assembly de interoperabilidade primária
 A documentação de referência do PIA do Excel descreve os tipos no assembly de interoperabilidade primário para Excel. Esta documentação está disponível no seguinte local: [Referência de assembly de interoperabilidade primária do Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

 Para obter mais informações sobre o design do PIA do Excel, como as diferenças entre classes e interfaces no PIA e como os eventos no PIA são implementados, consulte [visão geral de classes e interfaces nos assemblies](http://go.microsoft.com/fwlink/?LinkId=189592)de interoperabilidade primária do Office.

### <a name="vba-object-model-reference"></a>Referência de modelo de objeto VBA
 A referência do modelo de objeto do VBA documenta o modelo de objeto do Excel como ele é exposto ao código Visual Basic for Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199768).

 Todos os objetos e membros na referência do modelo de objeto do VBA correspondem a tipos e membros no PIA do Excel. Por exemplo, o objeto Worksheet na referência do modelo de objeto do VBA corresponde <xref:Microsoft.Office.Interop.Excel.Worksheet> ao objeto no pia do Excel. Embora a referência de modelo de objeto do VBA Forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA nesta referência C# para Visual Basic ou Visual se quiser usá-los em um projeto do Excel criado usando o Visual Studio.

### <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Soluções do Excel](../vsto/excel-solutions.md)|Explica como você pode criar personalizações em nível de documento e suplementos do VSTO para Microsoft Office Excel.|
|[Trabalhar com intervalos](../vsto/working-with-ranges.md)|Fornece exemplos que mostram como executar tarefas comuns com intervalos.|
|[Trabalhar com planilhas](../vsto/working-with-worksheets.md)|Fornece exemplos que mostram como executar tarefas comuns com planilhas.|
|[Trabalhar com pastas de trabalho](../vsto/working-with-workbooks.md)|Fornece exemplos que mostram como executar tarefas comuns com pastas de trabalho.|
