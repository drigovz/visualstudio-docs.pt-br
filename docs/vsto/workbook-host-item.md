---
title: Item de host da pasta de trabalho
description: Saiba que o item de host da pasta de trabalho é um tipo que estende o tipo de pasta de trabalho do assembly de interoperabilidade primário para o Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d3d5b7efadefd77be7ce25026c8f485ee0ef133
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528354"
---
# <a name="workbook-host-item"></a>Item de host da pasta de trabalho
  O <xref:Microsoft.Office.Tools.Excel.Workbook> item de host é um tipo que estende o <xref:Microsoft.Office.Interop.Excel.Workbook> tipo do assembly de interoperabilidade primário para o Excel. O <xref:Microsoft.Office.Tools.Excel.Workbook> item de host fornece todas as mesmas propriedades, métodos e eventos que um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto, mas também fornece recursos adicionais.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Em projetos de nível de documento, há um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host padrão que representa a pasta de trabalho em seu projeto. Em projetos de suplemento do VSTO, você pode gerar <xref:Microsoft.Office.Tools.Excel.Workbook> itens de host em tempo de execução.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Entender o item de host da pasta de trabalho em projetos de nível de documento
 Para acessar a pasta de trabalho em seu projeto, use a `ThisWorkbook` classe. A `ThisWorkbook` classe fornece acesso a membros do item de <xref:Microsoft.Office.Tools.Excel.Workbook> host para executar tarefas básicas em sua personalização, como a execução de código quando a pasta de trabalho é aberta ou fechada. Para obter mais informações, consulte [programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md).

 A `ThisWorkbook` classe fornece um local no qual você pode começar a escrever código em seu projeto. Como a classe fornece todas as mesmas propriedades, métodos e eventos que o <xref:Microsoft.Office.Interop.Excel.Workbook> objeto no assembly de interoperabilidade primário para Excel, você também pode usar `ThisWorkbook` o para acessar o modelo de objeto do Excel. Para obter mais informações, consulte [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).

 Clique duas vezes no item de projeto **ThisWorkbook** em **Gerenciador de soluções** para exibir o designer de pasta de trabalho e exibir as propriedades e os eventos da pasta de trabalho na janela **Propriedades** .

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Limitações do item de host da pasta de trabalho em projetos de nível de documento
 Um projeto de nível de documento pode conter apenas um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host (ou seja, a `ThisWorkbook` classe). Você não pode adicionar novos <xref:Microsoft.Office.Tools.Excel.Workbook> itens de host ao seu projeto em tempo de design e não pode criar novos <xref:Microsoft.Office.Tools.Excel.Workbook> itens de host em tempo de execução de uma personalização em nível de documento.

 Se você criar uma nova pasta de trabalho do Excel em tempo de execução, ela será do tipo <xref:Microsoft.Office.Interop.Excel.Workbook> . Como não é um item de host, ele não pode conter controles de host nem controles de Windows Forms. Para obter mais informações sobre como criar pastas de trabalho em tempo de execução, consulte [como: criar programaticamente novas pastas de trabalho](../vsto/how-to-programmatically-create-new-workbooks.md).

 O <xref:Microsoft.Office.Tools.Excel.Workbook> item de host não funciona como um contêiner para controles de host. Portanto, você não pode adicionar nenhum controle visível à pasta de trabalho, mas pode adicionar componentes, como um <xref:System.Data.DataSet> , para que os componentes possam ser compartilhados por todas as planilhas. Em um projeto de nível de documento, os componentes disponíveis para a pasta de trabalho podem ser encontrados na guia **componente** , na guia **dados** e em **todas as Windows Forms** guia da **caixa de ferramentas**.

> [!NOTE]
> As ferramentas de desenvolvimento do Office no Visual Studio não oferecem suporte a pastas de trabalho compartilhadas.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Entender itens de host de pasta de trabalho em projetos de suplemento do VSTO
 Em projetos de suplemento do VSTO, você pode gerar um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host em tempo de execução para qualquer pasta de trabalho aberta no Excel. Para gerar um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host, use o `GetVstoObject` método. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Veja também
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Item de host de planilha](../vsto/worksheet-host-item.md)
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
