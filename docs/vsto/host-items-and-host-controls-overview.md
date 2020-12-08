---
title: Visão geral de itens de host e controles de host
description: Saiba que os itens de host e os controles de host são tipos que ajudam a fornecer o modelo de programação para soluções do Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- host items [Office development in Visual Studio]
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], listed
- Excel [Office development in Visual Studio], host items
- host controls [Office Development in Visual Stuio], naming
- host controls [Office development in Visual Studio]
- host controls [Office development in Visual Studio], about host controls
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host items [Office development in Visual Studio], about host items
- host items [Office development in Visual Studio], listed
- documents [Office development in Visual Studio], host items
- data binding [Office development in Visual Studio], host controls
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], deleting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: edc8939f2a9e5f41f81c8176d5268528c273a7ce
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845564"
---
# <a name="host-items-and-host-controls-overview"></a>Visão geral de itens de host e controles de host
  Os itens de host e os controles de host são tipos que ajudam a fornecer o modelo de programação para soluções do Office que são criadas usando as ferramentas de desenvolvimento do Office no Visual Studio. Os itens de host e os controles de host fazem a interação com os modelos de objeto do Microsoft Office Word e Microsoft Office Excel, que se baseiam em COM, mais como interagir com objetos gerenciados, como controles de Windows Forms.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="host-items"></a>Itens do host
 Itens de host são tipos que estão na parte superior das hierarquias de modelo de objeto em projetos do Office. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] define os seguintes itens de host para soluções do Word e do Excel:

- <xref:Microsoft.Office.Tools.Word.Document>

- <xref:Microsoft.Office.Tools.Excel.Workbook>

- <xref:Microsoft.Office.Tools.Excel.Worksheet>

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  Cada um desses tipos estende um objeto que existe nativamente no modelo de objeto do Word ou do Excel, chamado de *objeto do Office nativo*. Por exemplo, o <xref:Microsoft.Office.Tools.Word.Document> item de host estende o <xref:Microsoft.Office.Interop.Word.Document> objeto, que é definido no assembly de interoperabilidade primário para o Word.

  Os itens de host geralmente têm a mesma funcionalidade base que os objetos do Office correspondentes, mas são aprimorados com os seguintes recursos:

- A capacidade de hospedar os controles gerenciados, incluindo controles de host e controles de Windows Forms.

- Modelos de eventos mais avançados. Alguns eventos de documento, pasta de trabalho e planilha nos modelos de objeto do Word e do Excel nativos são gerados apenas no nível do aplicativo. Os itens de host fornecem esses eventos no nível do documento, para que seja mais fácil manipular os eventos de um documento específico.

### <a name="understand-host-items-in-document-level-projects"></a>Entender os itens do host em projetos de nível de documento
 Em projetos de nível de documento, os itens de host fornecem um ponto de entrada para seu código e têm designers que o ajudam a desenvolver sua solução.

 O <xref:Microsoft.Office.Tools.Word.Document> e os <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host têm designers associados que são a representação visual do documento ou da planilha, como um designer de Windows Forms. Você pode usar esse designer para modificar o conteúdo do documento ou da planilha diretamente no Word ou no Excel e para arrastar os controles para a superfície de design. Para obter mais informações, consulte [documentar](../vsto/document-host-item.md) item de host e [item de host de planilha](../vsto/worksheet-host-item.md).

 O <xref:Microsoft.Office.Tools.Excel.Workbook> item de host não funciona como um contêiner para controles que têm uma interface do usuário. Em vez disso, o designer desse item de host funciona como uma bandeja de componentes, que permite que você arraste um componente, como um <xref:System.Data.DataSet> , para sua superfície de design. Para obter mais informações, veja [item de host da pasta de trabalho](../vsto/workbook-host-item.md).

 Itens de host não podem ser criados programaticamente em projetos de nível de documento. Em vez disso, use as `ThisDocument` `ThisWorkbook` classes, ou `Sheet` *n* que o Visual Studio gera automaticamente em seu projeto em tempo de design. Essas classes geradas derivam dos itens de host e fornecem um ponto de entrada para seu código. Para obter mais informações, consulte [limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="understand-host-items-in-vsto-add-in-projects"></a>Entender itens de host em projetos de suplemento do VSTO
 Ao criar um suplemento do VSTO, você não tem acesso a nenhum item de host por padrão. No entanto, você pode gerar <xref:Microsoft.Office.Tools.Word.Document> , <xref:Microsoft.Office.Tools.Excel.Workbook> e <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host em suplementos do Word e do VSTO do Excel em tempo de execução.

 Depois de gerar um item de host, você pode executar tarefas como adicionar controles a documentos. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="host-controls"></a>Controles de host
 Os controles de host estendem vários objetos de interface do usuário nos modelos de objeto do Word e do Excel, como `Microsoft.Office.Interop.Word.ContentControl` <xref:Microsoft.Office.Interop.Excel.Range> objetos e.

 Os seguintes controles de host estão disponíveis para projetos do Excel:

- [Controle de gráfico](../vsto/chart-control.md)

- [Controle ListObject](../vsto/listobject-control.md)

- [Controle NamedRange](../vsto/namedrange-control.md)

- [Controle XmlMappedRange](../vsto/xmlmappedrange-control.md)

  Os seguintes controles de host estão disponíveis para projetos do Word:

- [Controle de indicador](../vsto/bookmark-control.md)

- [Controles de conteúdo](../vsto/content-controls.md)

- [Controle XMLNode](../vsto/xmlnode-control.md)

- [Controle de XMLNodes](../vsto/xmlnodes-control.md)

  Os controles de host que são adicionados aos documentos do Office se comportam como os objetos nativos do Office; no entanto, os controles de host têm funcionalidade adicional, incluindo eventos e recursos de associação de dados. Por exemplo, quando você deseja capturar os eventos de um objeto nativo <xref:Microsoft.Office.Interop.Excel.Range> no Excel, você deve primeiro manipular o evento de alteração da planilha. Em seguida, você deve determinar se a alteração ocorreu dentro do <xref:Microsoft.Office.Interop.Excel.Range> . Por outro lado, o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle de host tem um <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> evento que você pode manipular diretamente.

  A relação entre um item de host e controles de host é semelhante à relação entre um Windows Form e controles de Windows Forms. Assim como você colocaria um controle de caixa de texto em um formulário do Windows, coloca um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle em um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host. A ilustração a seguir mostra a relação entre os itens de host e os controles de host.

  ![Relação entre os itens de host e os controles de host](../vsto/media/hostitemscontrols.png "Relação entre os itens de host e os controles de host")

  Você também pode usar controles de Windows Forms em suas soluções do Office adicionando-os diretamente à superfície de documento do Word e do Excel. Para obter mais informações, consulte [visão geral dos controles de Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

> [!NOTE]
> Não há suporte para a adição de controles de host ou de Windows Forms a um subdocumento do Word.

### <a name="add-host-controls-to-your-documents"></a>Adicionar controles de host aos seus documentos
 Em projetos de nível de documento, você pode adicionar controles de host a seus documentos do Word ou planilhas do Excel em tempo de design das seguintes maneiras:

- Adicione controles de host ao seu documento em tempo de design da mesma maneira que você adicionaria um objeto nativo.

- Arraste controles de host da **caixa de ferramentas** para seus documentos e planilhas. Os controles de host do Excel estão disponíveis na guia **controles do Excel** em projetos do Excel, e os controles de host do Word estão disponíveis na guia **controles do Word** em projetos do Word.

- Arraste controles de host da janela **fontes de dados** para seus documentos e planilhas. Isso permite que você adicione controles que já estão associados a dados. Para obter mais informações, consulte [associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).

  Em projetos de suplemento do em nível de documento e do VSTO, você também pode adicionar alguns controles de host a documentos em tempo de execução. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Para obter mais informações sobre como adicionar controles de host a documentos, consulte os seguintes tópicos:

- [Como: adicionar controles de gráfico a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Como adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Como: adicionar controles XMLMappedRange a planilhas](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)

- [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

- [Como: adicionar controles de conteúdo a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Como: adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

- [Como: adicionar controles de XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)

### <a name="name-host-controls"></a>Nomear controles de host
 Quando você arrasta um controle de host da **caixa de ferramentas** para o documento, o controle é nomeado automaticamente usando o tipo de controle com um número incremental no final. Por exemplo, os indicadores são nomeados **Bookmark1**, **bookmark2** e assim por diante. Se você usar a funcionalidade nativa do Word ou do Excel para adicionar o controle, poderá atribuir a ele um nome específico no momento em que você criá-lo. Você também pode renomear os controles alterando o valor da propriedade **Name** na janela **Propriedades** .

> [!NOTE]
> Você não pode usar palavras reservadas para nomear controles de host. Por exemplo, se você adicionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle a uma planilha e alterar o nome para o **sistema**, ocorrerão erros quando você compilar o projeto.

### <a name="delete-host-controls"></a>Excluir controles de host
 Em projetos de nível de documento, você pode excluir controles de host em tempo de design selecionando o controle na planilha do Excel ou no documento do Word e pressionando a tecla **delete** . No entanto, você deve usar a caixa de diálogo **definir nome** no Excel para excluir <xref:Microsoft.Office.Tools.Excel.NamedRange> controles.

 Se você adicionar um controle de host a um documento em tempo de design, não deverá removê-lo programaticamente em tempo de execução porque, na próxima vez que tentar usar o controle no código, uma exceção será lançada. O `Delete` método de um controle de host remove apenas os controles de host que são adicionados ao documento em tempo de execução. Se você chamar o `Delete` método de um controle de host que foi criado em tempo de design, uma exceção será lançada.

 Por exemplo, o <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> método de <xref:Microsoft.Office.Tools.Excel.NamedRange> apenas exclui com êxito o <xref:Microsoft.Office.Tools.Excel.NamedRange> se ele foi programaticamente adicionado à planilha, o que é conhecido como criação dinâmica de controles de host. Controles de host criados dinamicamente também podem ser removidos passando o nome do controle para o `Remove` método da <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> propriedade ou. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Se os usuários finais excluirem um controle de host do documento em tempo de execução, a solução poderá falhar de maneiras inesperadas. Você pode usar os recursos de proteção de documentos no Word e no Excel para proteger os controles de host de serem excluídos. Para obter mais informações, consulte [amostras e exemplos de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md).

> [!NOTE]
> Não remova programaticamente os controles durante o `Shutdown` manipulador de eventos do documento ou da planilha. Os elementos da interface do usuário não estão mais disponíveis quando o `Shutdown` evento ocorre. Se você quiser remover os controles antes de o aplicativo fechar, adicione seu código a outro manipulador de eventos, como `BeforeClose` ou `BeforeSave` .

### <a name="program-against-host-control-events"></a>Programa em relação a eventos de controle de host
 Uma maneira de os controles de host estender objetos do Office é adicionar eventos. Por exemplo, o <xref:Microsoft.Office.Interop.Excel.Range> objeto no Excel e <xref:Microsoft.Office.Interop.Word.Bookmark> no objeto do Word não tem eventos, mas o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] estende esses objetos adicionando eventos programáveis. Você pode acessar e codificar com base nesses eventos da mesma maneira que acessa eventos de controles no Windows Forms: por meio da lista suspensa de eventos no Visual Basic e na página de propriedades do evento em C#. Para obter mais informações, consulte [Walkthrough: programa em relação a eventos de um controle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

> [!NOTE]
> Você não deve definir a <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> Propriedade do <xref:Microsoft.Office.Interop.Excel.Application> objeto no Excel como **false**. Definir essa propriedade como **false** impede que o Excel disparasse qualquer evento, incluindo os eventos de controles de host.

## <a name="see-also"></a>Confira também
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)
- [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
