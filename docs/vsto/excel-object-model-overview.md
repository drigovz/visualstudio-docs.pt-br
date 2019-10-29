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
ms.openlocfilehash: 29ede9dd29952e87e7f1dd76875905973bada6a6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986087"
---
# <a name="excel-object-model-overview"></a>Visão geral do modelo de objeto do Excel
  Para desenvolver soluções que usam o Microsoft Office Excel, você pode interagir com os objetos fornecidos pelo modelo de objeto do Excel. Este tópico apresenta os objetos mais importantes:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  O modelo de objeto segue com mais detalhes a interface do usuário. O objeto <xref:Microsoft.Office.Interop.Excel.Application> representa o aplicativo inteiro e cada objeto <xref:Microsoft.Office.Interop.Excel.Workbook> contém uma coleção de objetos `Worksheet`. A partir daí, a abstração principal que representa as células é o objeto <xref:Microsoft.Office.Interop.Excel.Range>, que permite que você trabalhe com células individuais ou grupos de células.

  Além do modelo de objeto do Excel, os projetos do Office no Visual Studio fornecem *itens de host* e *controles de host* que estendem alguns objetos no modelo de objeto do Excel. Os itens de host e os controles de host se comportam como os objetos do Excel que eles estendem, mas também têm funcionalidade adicional, como recursos de ligação de dados e eventos extras. Para saber mais, confira [automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md) e [itens de host e visão geral de controles de host](../vsto/host-items-and-host-controls-overview.md).

  Este tópico fornece uma breve visão geral do modelo de objeto do Excel. Para obter recursos em que você pode aprender mais sobre o modelo de objeto do Excel inteiro, consulte [usar a documentação do modelo de objeto do Excel](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Acessar objetos em um projeto do Excel
 Quando você cria um novo projeto de suplemento do VSTO para Excel, o Visual Studio cria automaticamente um arquivo de código *ThisAddIn. vb* ou *ThisAddIn.cs* . Você pode acessar o objeto de aplicativo usando `Me.Application` ou `this.Application`.

 Ao criar um novo projeto de nível de documento para o Excel, você tem a opção de criar uma nova pasta de trabalho do Excel ou um projeto de modelo do Excel. O Visual Studio cria automaticamente os seguintes arquivos de código em seu novo projeto do Excel para projetos de pasta de trabalho e modelo.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook. vb|ThisWorkbook.cs|
|Plan1. vb|Sheet1.cs|
|Planilha2. vb|Sheet2.cs|
|Sheet3. vb|Sheet3.cs|

 Você pode usar a classe `Globals` em seu projeto para acessar `ThisWorkbook`, `Sheet1`, `Sheet2`ou `Sheet3` de fora da respectiva classe. Para obter mais informações, consulte [acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md). O exemplo a seguir chama o método <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> de `Sheet1` independentemente se o código é colocado em uma das classes `Sheet`*n* ou na classe `ThisWorkbook`.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Como os dados em um documento do Excel são altamente estruturados, o modelo de objeto é hierárquico e direto. O Excel fornece centenas de objetos com os quais você pode querer interagir, mas você pode obter um bom começo do modelo de objeto concentrando-se em um pequeno subconjunto dos objetos disponíveis. Esses objetos incluem os quatro seguintes:

- Aplicativo

- Pastas de trabalho

- Planilha

- Intervalo

  Grande parte do trabalho feito com os centros do Excel em relação a esses quatro objetos e seus membros.

### <a name="application-object"></a>Objeto de aplicativo
 O objeto de <xref:Microsoft.Office.Interop.Excel.Application> do Excel representa o próprio aplicativo do Excel. O objeto <xref:Microsoft.Office.Interop.Excel.Application> expõe uma grande quantidade de informações sobre o aplicativo em execução, as opções aplicadas a essa instância e os objetos de usuário atuais são abertos na instância do.

> [!NOTE]
> Você não deve definir a propriedade <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> do objeto <xref:Microsoft.Office.Interop.Excel.Application> no Excel como **false**. Definir essa propriedade como false impede que o Excel disparasse qualquer evento, incluindo os eventos de controles de host.

### <a name="workbook-object"></a>Objeto de pasta de trabalho
 O objeto <xref:Microsoft.Office.Interop.Excel.Workbook> representa uma única pasta de trabalho dentro do aplicativo Excel.

 As ferramentas de desenvolvimento do Office no Visual Studio estendem o objeto <xref:Microsoft.Office.Interop.Excel.Workbook> fornecendo o tipo <xref:Microsoft.Office.Tools.Excel.Workbook>. Esse tipo fornece acesso a todos os recursos de um objeto <xref:Microsoft.Office.Interop.Excel.Workbook>. Para obter mais informações, veja [item de host da pasta de trabalho](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Objeto de planilha
 O objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> é um membro da coleção <xref:Microsoft.Office.Interop.Excel.Worksheets>. Muitas das propriedades, métodos e eventos do <xref:Microsoft.Office.Interop.Excel.Worksheet> são idênticos ou semelhantes aos membros fornecidos pelos objetos <xref:Microsoft.Office.Interop.Excel.Application> ou <xref:Microsoft.Office.Interop.Excel.Workbook>.

 O Excel fornece uma coleção de <xref:Microsoft.Office.Interop.Excel.Sheets> como uma propriedade de um objeto <xref:Microsoft.Office.Interop.Excel.Workbook>. Cada membro da coleção de <xref:Microsoft.Office.Interop.Excel.Sheets> é um objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> ou <xref:Microsoft.Office.Interop.Excel.Chart>.

 As ferramentas de desenvolvimento do Office no Visual Studio estendem o objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> fornecendo o tipo <xref:Microsoft.Office.Tools.Excel.Worksheet>. Esse tipo fornece acesso a todos os recursos de um objeto <xref:Microsoft.Office.Interop.Excel.Worksheet>, bem como novos recursos, como a capacidade de hospedar controles gerenciados e lidar com novos eventos. Para obter mais informações, consulte [planilha de item de host](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Objeto de intervalo
 O objeto <xref:Microsoft.Office.Interop.Excel.Range> é o objeto que você usará mais em seus aplicativos do Excel. Antes de poder manipular qualquer região no Excel, você deve exexpressá-la como um objeto <xref:Microsoft.Office.Interop.Excel.Range> e trabalhar com métodos e propriedades desse intervalo. Um objeto de <xref:Microsoft.Office.Interop.Excel.Range> representa uma célula, uma linha, uma coluna, uma seleção de células que contém um ou mais blocos de células, que podem ou não ser contíguos ou até mesmo um grupo de células em várias planilhas.

 O Visual Studio estende o objeto <xref:Microsoft.Office.Interop.Excel.Range> fornecendo os tipos <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Esses tipos têm a maioria dos mesmos recursos que um objeto <xref:Microsoft.Office.Interop.Excel.Range>, bem como novos recursos, como a capacidade de vinculação de dados e novos eventos. Para obter mais informações, consulte [controle NamedRange](../vsto/namedrange-control.md) e [controle XmlMappedRange](../vsto/xmlmappedrange-control.md).

## <a name="ExcelOMDocumentation"></a>Usar a documentação do modelo de objeto do Excel
 Para obter informações completas sobre o modelo de objeto do Excel, consulte a referência do assembly de interoperabilidade primária do Excel (PIA) e a referência do modelo de objeto do VBA.

### <a name="primary-interop-assembly-reference"></a>Referência de assembly de interoperabilidade primária
 A documentação de referência do PIA do Excel descreve os tipos no assembly de interoperabilidade primário para Excel. Esta documentação está disponível no seguinte local: [referência de assembly de interoperabilidade primária do Excel 2010](/visualstudio/vsto/office-primary-interop-assemblies&view=vs-2019).

 Para obter mais informações sobre o design do PIA do Excel, como as diferenças entre classes e interfaces no PIA e como os eventos no PIA são implementados, consulte [visão geral de classes e interfaces nos assemblies de interoperabilidade primária do Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Referência de modelo de objeto VBA
 A referência do modelo de objeto do VBA documenta o modelo de objeto do Excel como ele é exposto ao código Visual Basic for Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do Excel 2010](/office/vba/api/overview/Excel/object-model).

 Todos os objetos e membros na referência do modelo de objeto do VBA correspondem a tipos e membros no PIA do Excel. Por exemplo, o objeto Worksheet na referência do modelo de objeto do VBA corresponde ao objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> no PIA do Excel. Embora a referência de modelo de objeto do VBA Forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA nesta referência C# para Visual Basic ou Visual se quiser usá-los em um projeto do Excel criado usando o Visual Studio.

### <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Soluções do Excel](../vsto/excel-solutions.md)|Explica como você pode criar personalizações em nível de documento e suplementos do VSTO para Microsoft Office Excel.|
|[Trabalhar com intervalos](../vsto/working-with-ranges.md)|Fornece exemplos que mostram como executar tarefas comuns com intervalos.|
|[Trabalhar com planilhas](../vsto/working-with-worksheets.md)|Fornece exemplos que mostram como executar tarefas comuns com planilhas.|
|[Trabalhar com pastas de trabalho](../vsto/working-with-workbooks.md)|Fornece exemplos que mostram como executar tarefas comuns com pastas de trabalho.|
