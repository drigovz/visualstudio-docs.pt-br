---
title: Item de host de planilha
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 301b0a62efae4674432b1051451e5d982899c1b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254877"
---
# <a name="worksheet-host-item"></a>Item de host de planilha
  O <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host é um tipo que estende o <xref:Microsoft.Office.Interop.Excel.Worksheet> tipo do assembly de interoperabilidade primário para o Excel. O <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host fornece todas as mesmas propriedades, métodos e eventos que um <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto, mas também expõe eventos adicionais e atua como um contêiner para controles de host e controles de Windows Forms.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Em projetos de nível de documento, você pode adicionar <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host ao seu projeto em tempo de design. Em projetos de suplemento do VSTO, você pode gerar <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host em tempo de execução.

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Entender os itens de host da planilha em projetos de nível de documento
 Quando você cria um projeto de nível de documento para o Excel, o Visual Studio cria automaticamente três <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host no projeto. Os nomes padrão das planilhas são `Sheet1` , `Sheet2` e `Sheet3` . Se você criar um projeto baseado em uma pasta de trabalho existente, o número de itens do host dependerá do número de planilhas na pasta de trabalho.

 Essas classes de planilha fornecem acesso a membros do <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host para executar tarefas básicas em sua personalização, como modificar o conteúdo de uma planilha. Você também pode usar essas classes para adicionar controles a planilhas. Ao combinar diferentes conjuntos de controles e escrever código, você pode associar os controles aos dados, coletar informações do usuário e responder às ações do usuário. Para obter mais informações, consulte [programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md).

 As classes de planilha fornecem um local no qual você pode começar a escrever código em seu projeto. Como a classe fornece todas as mesmas propriedades, métodos e eventos que o <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto no assembly de interoperabilidade primário para o Excel, você também pode usar essas classes para acessar o modelo de objeto do Excel. Para obter mais informações, consulte [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).

 Em projetos de nível de documento, você pode adicionar <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host adicionais ao projeto em tempo de design adicionando uma nova planilha à pasta de trabalho no designer.

### <a name="rename-worksheets"></a>Renomear planilhas
 Em um projeto de nível de documento, você pode renomear as planilhas no designer do Visual Studio, mas isso só altera o nome de exibição da planilha. O nome programático ainda é o nome padrão da planilha. Se você renomear a planilha na janela **Propriedades** , somente o nome programático será alterado.

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Limitações do item de host de planilha em projetos de nível de documento
 Você não pode criar novos <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host em tempo de execução em um projeto de nível de documento. Se você criar uma nova planilha do Excel em tempo de execução, ela será do tipo <xref:Microsoft.Office.Interop.Excel.Worksheet> . Como não é um item de host, ele não pode conter controles de host nem controles de Windows Forms. Para obter mais informações sobre como criar documentos em tempo de execução, consulte [How to: programaticamente, adicionar novas planilhas a pastas de trabalho](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Entender os itens de host da planilha nos projetos do suplemento do VSTO
 Em projetos de nível de aplicativo, você pode gerar um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host em tempo de execução para qualquer planilha aberta no Excel. Você pode usar o <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host para adicionar controles à planilha associada ou para manipular eventos que não estão disponíveis em <xref:Microsoft.Office.Interop.Excel.Worksheet> objetos.

 Para gerar um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host, use o `GetVstoObject` método. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Confira também
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Item de host da pasta de trabalho](../vsto/workbook-host-item.md)
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
