---
title: Atualizar o Excel ou o projeto do Word migrado para o .NET Framework 4/4,5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bc211f4d30359c885b22a45910363bbadca236f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253716"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Atualize os projetos do Excel e do Word que você migra para o .NET Framework 4 ou o .NET Framework 4,5
  Se você tiver um projeto do Excel ou do Word que usa qualquer um dos recursos a seguir, você deverá modificar seu código se a estrutura de destino for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior:

- [Métodos GetVstoObject e HasVstoObject](#GetVstoObject)

- [Classes geradas em projetos de nível de documento](#generatedclasses)

- [Controles de Windows Forms em documentos](#winforms)

- [Eventos de controle de conteúdo do Word](#ccevents)

- [Classes OLEObject e OLEControl](#ole)

- [Propriedade Controls. Item (Object)](#itemproperty)

- [Coleções que derivam de CollectionBase](#collections)

  Você também deve remover as `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` referências e para a `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` classe de projetos do Excel que são redirecionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. O Visual Studio não remove este atributo ou a referência de classe para você.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Remover o atributo ExcelLocale1033 dos projetos do Excel
 O `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` foi removido da parte do tempo de execução das ferramentas do Visual Studio 2010 para Office usada para soluções direcionadas para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. O Common Language Runtime (CLR) no [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e posterior sempre passa a ID de localidade 1033 para o modelo de objeto do Excel e você não pode mais usar esse atributo para desabilitar esse comportamento. Para obter mais informações, consulte [globalização e localização de soluções do Excel](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>Para remover o ExcelLocale1033Attribute

1. Com o projeto aberto no Visual Studio, abra **Gerenciador de soluções**.

2. No nó **Propriedades** (para C#) ou no nó **meu projeto** (para Visual Basic), clique duas vezes no arquivo de código AssemblyInfo para abri-lo no editor de códigos.

    > [!NOTE]
    > Em projetos Visual Basic, você deve clicar no botão **Mostrar todos os arquivos** em **Gerenciador de soluções** para ver o arquivo de código AssemblyInfo.

3. Localize o `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` e remova-o do arquivo ou comente-o.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Remover uma referência à classe ExcelLocal1033Proxy
 Projetos que foram criados usando Microsoft Visual Studio ferramentas 2005 para o sistema Microsoft Office instanciam o objeto do Excel <xref:Microsoft.Office.Interop.Excel.Application> usando a `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` classe. Essa classe foi removida da parte do tempo de execução das ferramentas do Visual Studio 2010 para Office usada para soluções direcionadas ao [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. Portanto, você deve remover ou comentar a linha de código que faz referência a essa classe.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Para remover a referência à classe ExcelLocal1033Proxy

1. Abra o projeto no Visual Studio e, em seguida, abra **Gerenciador de soluções**.

2. No **Gerenciador de soluções**, abra o menu de atalho para *ThisAddIn.cs* (para C#) ou *ThisAddin. vb* (para Visual Basic) e escolha **Exibir código**.

3. No editor de código, na `VSTO generated code` região, remova ou comente a linha de código a seguir.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="update-code-that-uses-the-getvstoobject-and-hasvstoobject-methods"></a><a name="GetVstoObject"></a> Atualizar o código que usa os métodos GetVstoObject e HasVstoObject
 Em projetos que visam o .NET Framework 3,5, `GetVstoObject` os `HasVstoObject` métodos ou estão disponíveis como métodos de extensão em um dos seguintes objetos nativos em seu projeto <xref:Microsoft.Office.Interop.Word.Document> :, <xref:Microsoft.Office.Interop.Excel.Workbook> , <xref:Microsoft.Office.Interop.Excel.Worksheet> ou <xref:Microsoft.Office.Interop.Excel.ListObject> . Ao chamar esses métodos, você não precisa passar um parâmetro. O exemplo de código a seguir demonstra como usar o método GetVstoObject em um suplemento do Word VSTO que tem como alvo o .NET Framework 3,5.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 Em projetos direcionados [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] para o ou posterior, você deve modificar seu código para acessar esses métodos de uma das seguintes maneiras:

- Você ainda pode acessar esses métodos como métodos de extensão <xref:Microsoft.Office.Interop.Word.Document> nos <xref:Microsoft.Office.Interop.Excel.Workbook> objetos,, <xref:Microsoft.Office.Interop.Excel.Worksheet> ou <xref:Microsoft.Office.Interop.Excel.ListObject> . No entanto, agora você deve passar o objeto retornado pela `Globals.Factory` propriedade para esses métodos.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Como alternativa, você pode acessar esses métodos no objeto retornado pela `Globals.Factory` propriedade. Ao acessar esses métodos dessa forma, você deve passar o objeto nativo que deseja estender para o método.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="update-code-that-uses-instances-of-the-generated-classes-in-document-level-projects"></a><a name="generatedclasses"></a> Atualizar o código que usa instâncias das classes geradas em projetos de nível de documento
 Em projetos de nível de documento direcionados para o .NET Framework 3,5, as classes geradas nos projetos derivam das seguintes classes no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] :

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheet>

  Em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, os tipos [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] listados acima são interfaces, em vez de classes. As classes geradas em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior derivam das seguintes novas classes no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] :

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Se o código em seu projeto se referir a uma instância de uma das classes geradas como a classe base da qual deriva, você deverá modificar o código.

  Por exemplo, em um projeto de pasta de trabalho do Excel que tem como alvo o .NET Framework 3,5, você pode ter um método auxiliar que executa algum trabalho em instâncias das `Sheet` *n* classes geradas em seu projeto.

```vb
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)
    ' Do something to the worksheet object.
End Sub
```

```csharp
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)
{
    // Do something to the worksheet object.
}
```

 Se você redirecionar o projeto para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, deverá fazer uma das seguintes alterações em seu código:

- Modifique qualquer código que chame o `DoSomethingToSheet` método para passar a <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> propriedade de um <xref:Microsoft.Office.Tools.Excel.WorksheetBase> objeto em seu projeto. Essa propriedade retorna um <xref:Microsoft.Office.Tools.Excel.Worksheet> objeto.

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- `DoSomethingToSheet`Em vez disso, modifique o parâmetro do método para esperar um <xref:Microsoft.Office.Tools.Excel.WorksheetBase> objeto.

    ```vb
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)
        ' Do something to the worksheet object.
    End Sub
    ```

    ```csharp
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)
    {
        // Do something to the worksheet object.
    }
    ```

## <a name="update-code-that-uses-windows-forms-controls-on-documents"></a><a name="winforms"></a> Atualizar o código que usa controles de Windows Forms em documentos
 Você deve adicionar uma instrução **using** (C#) ou **Imports** (Visual Basic) para o <xref:Microsoft.Office.Tools.Excel> <xref:Microsoft.Office.Tools.Word> namespace ou na parte superior de qualquer arquivo de código que usa a propriedade Controls para adicionar Windows Forms controles ao documento ou planilha de forma programática.

 Em projetos que visam o .NET Framework 3,5, os métodos que adicionam Windows Forms controles (como o `AddButton` método) são definidos nas <xref:Microsoft.Office.Tools.Excel.ControlCollection> <xref:Microsoft.Office.Tools.Word.ControlCollection> classes e.

 Em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, esses métodos são métodos de extensão que estão disponíveis na propriedade Controls. Para usar esses métodos de extensão, o arquivo de código no qual você usa os métodos deve ter uma instrução **using** ou **Imports** para o <xref:Microsoft.Office.Tools.Excel> <xref:Microsoft.Office.Tools.Word> namespace ou. Essa instrução é gerada automaticamente em novos projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. No entanto, essa instrução não é adicionada automaticamente em projetos direcionados para o .NET Framework 3,5, portanto, você deve adicioná-la ao redirecionar o projeto.

 Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-handles-word-content-control-events"></a><a name="ccevents"></a> Código de atualização que manipula eventos de controle de conteúdo do Word
 Em projetos que visam o .NET Framework 3,5, os eventos de controles de conteúdo do Word são tratados pelo <xref:System.EventHandler%601> delegado genérico. Em projetos direcionados [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] para o ou posterior, esses eventos são tratados por outros delegados.

 A tabela a seguir lista os eventos de controle de conteúdo do Word e os delegados associados a eles em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

|Evento|Delegar para usar no [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e projetos posteriores|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="update-code-that-uses-the-oleobject-and-olecontrol-classes"></a><a name="ole"></a> Atualizar o código que usa as classes OLEObject e OLEControl
 Em projetos direcionados para o .NET Framework 3,5, você pode adicionar controles personalizados (como Windows Forms controles de usuário) a um documento ou planilha usando as `Microsoft.Office.Tools.Excel.OLEObject` `Microsoft.Office.Tools.Word.OLEControl` classes e.

 Em projetos direcionados [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] para o ou posterior, essas classes foram substituídas pelas <xref:Microsoft.Office.Tools.Excel.ControlSite> <xref:Microsoft.Office.Tools.Word.ControlSite> interfaces e. Você deve modificar o código que se refere ao `Microsoft.Office.Tools.Excel.OLEObject` e `Microsoft.Office.Tools.Word.OLEControl` ao em vez disso, consulte <xref:Microsoft.Office.Tools.Excel.ControlSite> e <xref:Microsoft.Office.Tools.Word.ControlSite> . Além dos novos nomes, esses controles se comportam da mesma forma que em projetos direcionados para o .NET Framework 3,5.

 Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-the-controlsitemobject-property"></a><a name="itemproperty"></a> Atualizar o código que usa a propriedade Controls. Item (Object)
 Em projetos que visam o .NET Framework 3,5, você pode usar a Propriedade Item (objeto) do Microsoft.Office.Tools.Word.Document. Controles ou `Microsoft.Office.Tools.Excel.Worksheet.Controls` coleção para determinar se um documento ou planilha tem um controle especificado.

 Em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, a Propriedade Item (Object) foi removida dessas coleções. Para determinar se um documento ou planilha contém um controle especificado, use o método contém (System. Object) da <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> coleção ou <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> em vez disso.

 Para obter mais informações sobre a coleção Controls de documentos e planilhas, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-collections-that-derive-from-collectionbase"></a><a name="collections"></a> Atualizar o código que usa coleções que derivam de CollectionBase
 Em projetos que visam o .NET Framework 3,5, vários tipos de coleção no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derivam da <xref:System.Collections.CollectionBase> classe, como `Microsoft.Office.Tools.SmartTagCollection` , `Microsoft.Office.Tools.Excel.ControlCollection` e `Microsoft.Office.Tools.Word.ControlCollection` .

 Em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, esses tipos de coleção agora são interfaces que não derivam de <xref:System.Collections.CollectionBase> . Alguns membros não estão mais disponíveis nesses tipos de coleção, como <xref:System.Collections.CollectionBase.Capacity%2A> , <xref:System.Collections.CollectionBase.List%2A> e <xref:System.Collections.CollectionBase.InnerList%2A> .

## <a name="see-also"></a>Confira também
- [Migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Controles de conteúdo](../vsto/content-controls.md)
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
