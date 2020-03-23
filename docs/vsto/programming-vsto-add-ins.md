---
title: Complementos do Programa VSTO
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93470ebcea306d3cea762d60e061994b2bf27cc8
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301702"
---
# <a name="program-vsto-add-ins"></a>Complementos do Programa VSTO
  Quando você estende um aplicativo do Microsoft Office criando um Complemento `ThisAddIn` VSTO, você escreve código diretamente contra a classe em seu projeto. Você pode usar essa classe para executar tarefas como acessar o modelo de objeto do aplicativo host do Microsoft Office, personalizar a interface do usuário (Interface do Usuário) do aplicativo e expor objetos em seu Complemento VSTO a outras soluções do Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Alguns aspectos da escrita de código em projetos de complemento VSTO são diferentes de outros tipos de projetos no Visual Studio. Muitas dessas diferenças são causadas pela forma como os modelos de objeto office são expostos a código gerenciado. Para obter mais informações, consulte [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md).

 Para obter informações gerais sobre add-ins vsto e outros tipos de soluções que você pode criar usando as ferramentas de desenvolvimento do Office no Visual Studio, consulte [a visão geral do desenvolvimento de soluções do Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Use a classe ThisAddIn
 Você pode começar a escrever seu código `ThisAddIn` de complemento VSTO na classe. O Visual Studio gera automaticamente essa classe no arquivo [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]de código *ThisAddIn.vb* (in) ou *ThisAddIn.cs* (em C#) em seu projeto de complemento VSTO. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instantaneamente instancia esta classe para você quando o aplicativo do Microsoft Office carrega seu Complemento VSTO.

 Existem dois manipuladores de `ThisAddIn` eventos padrão na classe. Para executar o código quando o Complemento VSTO `ThisAddIn_Startup` estiver carregado, adicione código ao manipulador de eventos. Para executar o código pouco antes do complemento do `ThisAddIn_Shutdown` VSTO ser descarregado, adicione código ao manipulador de eventos. Para obter mais informações sobre esses manipuladores de eventos, consulte [projetos Eventos no Escritório](../vsto/events-in-office-projects.md).

> [!NOTE]
> No Outlook, por `ThisAddIn_Shutdown` padrão, o manipulador de eventos nem sempre é chamado quando o Add-in VSTO é descarregado. Para obter mais informações, consulte [Eventos em Projetos de Escritório](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Acesse o modelo de objeto do aplicativo host
 Para acessar o modelo de objeto `Application` do aplicativo `ThisAddIn` host, use o campo da classe. Este campo retorna um objeto que representa a instância atual do aplicativo host. A tabela a seguir lista o `Application` tipo do valor de retorno para o campo em cada projeto de complemento do VSTO.

|Aplicativo host|Tipo de valor de retorno|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Aplicativo](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Aplicativo|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 O exemplo de código a `Application` seguir mostra como usar o campo para criar uma nova pasta de trabalho em um complemento VSTO para o Microsoft Office Excel. Este exemplo é destinado a `ThisAddIn` ser executado a partir da classe.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Para fazer a mesma `ThisAddIn` coisa de `Globals` fora da `ThisAddIn` classe, use o objeto para acessar a classe. Para obter mais `Globals` informações sobre o objeto, consulte [O acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Para obter mais informações sobre os modelos de objetos de aplicativos específicos do Microsoft Office, consulte os seguintes tópicos:

- [Visão geral do modelo de objeto excel](../vsto/excel-object-model-overview.md)

- [Visão geral do modelo de objeto de texto](../vsto/word-object-model-overview.md)

- [Visão geral do modelo do Outlook](../vsto/outlook-object-model-overview.md)

- [Soluções InfoPath](../vsto/infopath-solutions.md)

- [Soluções PowerPoint](../vsto/powerpoint-solutions.md)

- [Soluções de projetos](../vsto/project-solutions.md)

- [Visão geral do modelo do objeto Visio](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a>Acesse um documento quando o aplicativo do Office começar
 Nem [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] todos os aplicativos abrem automaticamente um documento quando [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] você os inicia, e nenhum dos aplicativos abre um documento quando você os inicia. Portanto, não adicione código no `ThisAdd-In_Startup` manipulador de eventos se o código exigir que um documento seja aberto. Em vez disso, adicione esse código a um evento que o aplicativo office levanta quando um usuário cria ou abre um documento. Dessa forma, você pode garantir que um documento esteja aberto antes que seu código realize operações nele.

 O exemplo de código a seguir funciona com um documento no Word somente quando o usuário cria um documento ou abre um documento existente.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>Estes membros AddIn para usar em outras tarefas
 A tabela a seguir descreve outras tarefas comuns e mostra quais membros da `ThisAddIn` classe você pode usar para executar as tarefas.

|Tarefa|Membro para usar|
|----------|-------------------|
|Executar código para inicializar o complemento VSTO quando o Complemento VSTO estiver carregado.|Adicione código `ThisAddIn_Startup` ao método. Este é o manipulador <xref:Microsoft.Office.Tools.AddInBase.Startup> de eventos padrão para o evento. Para obter mais informações, consulte [Eventos em Projetos de Escritório](../vsto/events-in-office-projects.md).|
|Executar código para limpar os recursos usados pelo Complemento VSTO antes que o Complemento VSTO seja descarregado.|Adicione código `ThisAddIn_Shutdown` ao método. Este é o manipulador <xref:Microsoft.Office.Tools.AddInBase.Shutdown> de eventos padrão para o evento. Para obter mais informações, consulte [Eventos em Projetos de Escritório](../vsto/events-in-office-projects.md). **Nota:**  No Outlook, por `ThisAddIn_Startup` padrão, o manipulador de eventos nem sempre é chamado quando o Add-in VSTO é descarregado. Para obter mais informações, consulte [Eventos em Projetos de Escritório](../vsto/events-in-office-projects.md).|
|Exibir um painel de tarefas personalizado.|Use `CustomTaskPanes` o campo. Para obter mais informações, consulte [Painéis de tarefas personalizados](../vsto/custom-task-panes.md).|
|Exponha objetos em seu complemento VSTO a outras soluções do Microsoft Office.|Substituir o método <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>. Para obter mais informações, consulte [Código de chamada em Add-ins VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Personalize um recurso no sistema do Microsoft Office implementando uma interface de extensibilidade.|Anular o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método para retornar uma instância de uma classe que implementa a interface. Para obter mais informações, consulte [Personalizar recursos de interface usando interfaces de extensibilidade](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Nota:**  Para personalizar a iu de fita, <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> você também pode substituir o método.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Entenda o design da classe ThisAddIn
 Em projetos que [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] <xref:Microsoft.Office.Tools.AddIn> visam o , é uma interface. A `ThisAddIn` classe deriva <xref:Microsoft.Office.Tools.AddInBase> da classe. Esta classe base redireciona todas as chamadas para <xref:Microsoft.Office.Tools.AddIn> seus membros [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]para uma implementação interna da interface no .

 Em projetos de complemento VSTO `ThisAddIn` para o `Microsoft.Office.Tools.Outlook.OutlookAddIn` Outlook, a classe deriva da classe em <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> projetos que visam [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]o Quadro .NET 3.5 e de projetos que visam o . Essas classes base fornecem algumas funcionalidades adicionais para suportar regiões de formulário. Para obter mais informações sobre regiões de formulário, consulte [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Personalize a interface de usuário dos aplicativos do Microsoft Office
 Você pode personalizar programáticamente a interface do rei dos aplicativos do Microsoft Office usando um complemento VSTO. Por exemplo, você pode personalizar a fita, exibir um painel de tarefas personalizado ou criar uma região de formulário personalizada no Outlook. Para obter mais informações, consulte [personalização da IU do Office](../vsto/office-ui-customization.md).

 O Visual Studio fornece designers e classes que você pode usar para criar painéis de tarefas personalizados, personalizações de fitas e regiões de formulário do Outlook. Esses designers e aulas ajudam a simplificar o processo de personalização desses recursos. Para obter mais informações, consulte [Painéis de tarefas personalizados,](../vsto/custom-task-panes.md) [Ribbon Designer](../vsto/ribbon-designer.md)e [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).

 Se você quiser personalizar um desses recursos de uma forma que não seja suportada pelas classes e designers, você também pode personalizar esses recursos implementando uma *interface de extensibilidade* em seu Complemento VSTO. Para obter mais informações, consulte [Personalizar recursos de interface usando interfaces de extensibilidade](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 Além disso, você pode modificar a UI de documentos do Word e as cadernetas do Excel gerando itens de host que ampliam o comportamento de documentos e livros de trabalho. Isso permite adicionar controles gerenciados a documentos e planilhas. Para obter mais informações, consulte [Estender documentos do Word e livros de trabalho do Excel em Complementos vsto em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Código de chamada em Add-ins VSTO de outras soluções
 Você pode expor objetos em seu complemento VSTO a outras soluções, incluindo outras soluções do Office. Isso é útil se o seu Complemento VSTO fornecer um serviço que você deseja habilitar outras soluções para usar. Por exemplo, se você tiver um Complemento VSTO para o Microsoft Office Excel que execute cálculos sobre dados financeiros de um serviço web, outras soluções podem realizar esses cálculos ligando para o Complemento do Excel VSTO em tempo de execução.

 Para obter mais informações, consulte [Código de chamada em Add-ins VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Confira também
- [Desenvolver soluções de Office](../vsto/developing-office-solutions.md)
- [Estender documentos do Word e livros de trabalho do Excel em complementos vsto em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Código de chamada em Add-ins VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Passo a passo: Código de chamada em um complemento VSTO da VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Personalizar recursos de interface de usuário usando interfaces de extensibilidade](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Como: Criar projetos de Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
