---
title: Programar personalizações em nível de documento
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d1908f72bce01956bbb2eeb62bb9bbc30a64b0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254027"
---
# <a name="program-document-level-customizations"></a>Programar personalizações em nível de documento
  Ao estender Microsoft Office Word ou Microsoft Office Excel usando uma personalização em nível de documento, você pode executar as seguintes tarefas:

- Automatize o aplicativo usando seu modelo de objeto.

- Adicione controles à superfície do documento.

- Chame o código Visual Basic for Applications (VBA) no documento do assembly de personalização.

- Chame o código no assembly de personalização do VBA.

- Gerencie determinados aspectos do documento enquanto estiver em um servidor que não tem Microsoft Office instalado.

- Personalize a interface do usuário (IU) do aplicativo.

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Alguns aspectos da gravação de código em projetos de nível de documento são diferentes de outros tipos de projetos no Visual Studio. Muitas dessas diferenças são causadas pela maneira como os modelos de objeto do Office são expostos ao código gerenciado. Para obter mais informações, consulte [escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md).

  Para obter informações gerais sobre personalizações em nível de documento e outros tipos de soluções que você pode criar usando as ferramentas de desenvolvimento do Office no Visual Studio, consulte [visão geral do desenvolvimento de soluções do office &#40;&#41;do VSTO ](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-generated-classes-in-document-level-projects"></a>Usar as classes geradas em projetos de nível de documento
 Quando você cria um projeto de nível de documento, o Visual Studio gera automaticamente uma classe no projeto que você pode usar para começar a escrever seu código. O Visual Studio gera classes diferentes para o Word e o Excel:

- Em projetos de nível de documento para o Word, a classe é chamada `ThisDocument` por padrão.

- Projetos de nível de documento para Excel têm várias classes geradas: uma para a própria pasta de trabalho e uma para cada planilha. Por padrão, essas classes têm os seguintes nomes:

  - `ThisWorkbook`

  - `Sheet1`

  - `Sheet2`

  - `Sheet3`

  A classe gerada inclui manipuladores de eventos que são chamados quando o documento é aberto ou fechado. Para executar o código quando o documento é aberto, adicione o código ao `Startup` manipulador de eventos. Para executar o código logo antes de o documento ser fechado, adicione o código ao `Shutdown` manipulador de eventos. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).

### <a name="understand-the-design-of-the-generated-classes"></a>Entender o design das classes geradas
 Em projetos que visam o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , os tipos de item de host no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] são interfaces, portanto, as classes geradas não podem derivar sua implementação deles. Em vez disso, as classes geradas derivam a maioria de seus membros das seguintes classes base:

- `ThisDocument`: deriva de <xref:Microsoft.Office.Tools.Word.DocumentBase> .

- `ThisWorkbook`: deriva de <xref:Microsoft.Office.Tools.Excel.WorkbookBase> .

- `Sheet`*n*: deriva de <xref:Microsoft.Office.Tools.Excel.WorksheetBase> .

  Essas classes base redirecionam todas as chamadas para seus membros para implementações internas das interfaces de item de host correspondentes no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Por exemplo, se você chamar o <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> método da `ThisDocument` classe, a <xref:Microsoft.Office.Tools.Word.DocumentBase> classe redirecionará essa chamada para a implementação interna da <xref:Microsoft.Office.Tools.Word.Document> interface no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="access-the-object-model-of-the-host-application"></a>Acessar o modelo de objeto do aplicativo host
 Para acessar o modelo de objeto do aplicativo host, use membros da classe gerada em seu projeto. Cada uma dessas classes corresponde a um objeto no modelo de objeto do Excel ou Word e contém a maioria das mesmas propriedades, métodos e eventos. Por exemplo, a `ThisDocument` classe em um projeto de nível de documento do Word fornece a maioria dos mesmos membros que o <xref:Microsoft.Office.Interop.Word.Document> objeto no modelo de objeto do Word.

 O exemplo de código a seguir mostra como usar o modelo de objeto do Word para salvar o documento que faz parte de uma personalização em nível de documento para o Word. Este exemplo deve ser executado a partir da `ThisDocument` classe.

```vb
Me.Save()
```

```csharp
this.Save();
```

 Para fazer a mesma coisa de fora da `ThisDocument` classe, use o `Globals` objeto para acessar a `ThisDocument` classe. Por exemplo, você pode adicionar esse código a um arquivo de código do painel ações se desejar incluir um botão **salvar** na interface do usuário do painel Ações.

```vb
Globals.ThisDocument.Save()
```

```csharp
Globals.ThisDocument.Save();
```

 Como a `ThisDocument` classe obtém a maioria de seus membros do <xref:Microsoft.Office.Tools.Word.Document> item de host, o `Save` método que é chamado nesse código é, na verdade, o <xref:Microsoft.Office.Tools.Word.Document.Save%2A> método do <xref:Microsoft.Office.Tools.Word.Document> item de host. Esse método corresponde ao <xref:Microsoft.Office.Interop.Word._Document.Save%2A> método do <xref:Microsoft.Office.Interop.Word.Document> objeto no modelo de objeto do Word.

 Para obter mais informações sobre como usar os modelos de objeto do Word e do Excel, consulte Visão [geral do modelo de objeto do Word](../vsto/word-object-model-overview.md) e modelo de objeto do [Excel](../vsto/excel-object-model-overview.md).

 Para obter mais informações sobre o `Globals` objeto, consulte [acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="add-controls-to-documents"></a>Adicionar controles a documentos
 Para personalizar a interface do usuário do documento, você pode adicionar Windows Forms controles ou *controles de host* à superfície do documento. Ao combinar diferentes conjuntos de controles e escrever código, você pode associar os controles aos dados, coletar informações do usuário e responder às ações do usuário.

 Os controles de host são classes que estendem alguns dos objetos no modelo de objeto do Word e do Excel. Por exemplo, o <xref:Microsoft.Office.Tools.Excel.ListObject> controle de host fornece toda a funcionalidade do <xref:Microsoft.Office.Interop.Excel.ListObject> no Excel. No entanto, o <xref:Microsoft.Office.Tools.Excel.ListObject> controle de host também tem eventos adicionais e recursos de associação de dados.

 Para obter mais informações, consulte Visão geral de [itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md) e [controles do Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="combine-vba-and-document-level-customizations"></a>Combine personalizações do VBA e no nível do documento
 Você pode usar o código do VBA em um documento que faz parte de uma personalização no nível do documento. Você pode chamar o código VBA no documento a partir do assembly de personalização e também pode configurar seu projeto para habilitar o código VBA no documento para chamar o código no assembly de personalização.

 Para obter mais informações, consulte [combinar VBA e personalizações em nível de documento](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="manage-documents-on-a-server"></a>Gerenciar documentos em um servidor
 Você pode gerenciar vários aspectos diferentes de personalizações em nível de documento em um servidor que não tem Microsoft Office Word ou Microsoft Office Excel instalado. Por exemplo, você pode acessar e modificar dados no cache de dados do documento. Você também pode gerenciar o assembly de personalização associado ao documento. Por exemplo, você pode remover programaticamente o assembly do documento para que o documento não execute mais seu código, ou você pode anexar um assembly programaticamente a um documento.

 Para obter mais informações, consulte [gerenciar documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Personalizar a interface do usuário de aplicativos Microsoft Office
 Você pode personalizar a interface do usuário do Word e do Excel das seguintes maneiras usando uma personalização em nível de documento:

- Adicione controles de host ou controles de Windows Forms à superfície do documento.

   Para obter mais informações, consulte [automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md), [automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)e [Windows Forms controles em documentos do Office visão geral](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Adicione um painel Ações ao documento.

   Para obter mais informações, consulte [visão geral do painel Ações](../vsto/actions-pane-overview.md).

- Adicione guias personalizadas à faixa de faixas.

   Para obter mais informações, consulte [visão geral da faixa](../vsto/ribbon-overview.md)de visualização.

- Adicione grupos personalizados a uma guia interna na faixa de bits.

   Para obter mais informações, consulte [como: personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md).

  Para obter mais informações sobre como personalizar a interface do usuário do Microsoft Office aplicativos, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).

## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Obter objetos estendidos de objetos nativos do Office em personalizações em nível de documento
 Muitos manipuladores de eventos para eventos do Office recebem um objeto nativo do Office que representa a pasta de trabalho, a planilha ou o documento que gerou o evento. Em alguns casos, talvez você queira executar apenas alguns códigos se a pasta de trabalho ou o documento em sua personalização no nível do documento gerar o evento. Por exemplo, em uma personalização em nível de documento para o Excel, talvez você queira executar algum código quando o usuário ativar uma das planilhas na pasta de trabalho personalizada, mas não quando o usuário ativar uma planilha em alguma outra pasta de trabalho que esteja aberta ao mesmo tempo.

 Quando você tem um objeto do Office nativo, você pode testar se esse objeto foi estendido para um *item de host* ou controle de *host* em uma personalização no nível do documento. Os itens de host e os controles de host são tipos fornecidos pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que adicionam funcionalidade a objetos que existem nativamente nos modelos de objeto do Word ou do Excel (chamados de *objetos nativos do Office*). Coletivamente, os itens de host e os controles de host também são chamados de *objetos estendidos*. Para obter mais informações sobre itens de host e controles de host, consulte [visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md).

## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>Entender os métodos GetVstoObject e HasVstoObject
 Para testar um objeto do Office nativo, use `HasVstoObject` os `GetVstoObject` métodos e em seu projeto:

- Use o `HasVstoObject` método se você quiser determinar se o objeto do Office nativo tem um objeto estendido em sua personalização. Esse método retornará **true** se o objeto do Office nativo tiver um objeto estendido e **false** caso contrário.

- Use o `GetVstoObject` método se você quiser obter o objeto estendido para um objeto do Office nativo. Esse método retornará um <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.Workbook> objeto,, <xref:Microsoft.Office.Tools.Excel.Worksheet> ou <xref:Microsoft.Office.Tools.Word.Document> se o objeto do Office nativo especificado tiver um. Caso contrário, `GetVstoObject` retornará **NULL**. Por exemplo, o `GetVstoObject` método retornará um <xref:Microsoft.Office.Tools.Word.Document> se o especificado <xref:Microsoft.Office.Interop.Word.Document> for o objeto subjacente para o documento em seu projeto de documento do Word.

  Em projetos de nível de documento, você não pode usar o `GetVstoObject` método para criar um novo <xref:Microsoft.Office.Tools.Excel.Workbook> item de <xref:Microsoft.Office.Tools.Excel.Worksheet> host, ou, <xref:Microsoft.Office.Tools.Word.Document> em tempo de execução. Você pode usar esse método somente para acessar os itens de host existentes que são gerados em seu projeto em tempo de design. Se você quiser criar novos itens de host em tempo de execução, deverá desenvolver um projeto de suplemento do VSTO. Para obter mais informações, consulte [limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) e [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>Usar os métodos GetVstoObject e HasVstoObject
 Para chamar o `HasVstoObject` `GetVstoObject` método e, use o `Globals.Factory.GetVstoObject` `Globals.Factory.HasVstoObject` método ou e passe o objeto do Word ou do Excel nativo (como um <xref:Microsoft.Office.Interop.Word.Document> ou <xref:Microsoft.Office.Interop.Excel.Worksheet> ) que você deseja testar.

## <a name="see-also"></a>Confira também
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Combine personalizações do VBA e no nível do documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Gerenciar documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
