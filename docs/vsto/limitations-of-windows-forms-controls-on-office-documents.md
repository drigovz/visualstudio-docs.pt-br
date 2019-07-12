---
title: Limitações de controles de Windows Forms em documentos do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d5cb4bf5788e1d30933a807e2e97e064118fc076
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823402"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitações de controles de Windows Forms em documentos do Office

Há algumas diferenças entre os controles de formulários do Windows que são adicionados a documentos do Microsoft Office Word ou planilhas do Microsoft Office Excel e controles de formulários do Windows que são adicionados ao Windows Forms. Por exemplo, quando você adiciona uma <xref:Microsoft.Office.Tools.Word.Controls.Button> como o controle para um documento, as propriedades <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, e <xref:System.Windows.Forms.Control.TabIndex> não se comportar como esperado.

Muitas dessas diferenças são causadas pela maneira como esse formulários do Windows controles são hospedados em documentos. Quando um controle dos Windows Forms é adicionado a um documento, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incorpora um controle ActiveX que, em seguida, hospede o controle de formulários do Windows no documento. O controle Windows Forms não é inserido diretamente no documento.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitações de métodos e propriedades de controles do Windows Forms

Há uma série de métodos e propriedades de controles de formulários do Windows que não funcionam da mesma forma em um documento como fariam em um formulário do Windows e, portanto, é recomendável que elas não usada. Por exemplo, definir propriedades como <xref:System.Windows.Forms.Control.Dock> e <xref:System.Windows.Forms.Control.Anchor> só afeta a posição do controle em relação à caixa de controles ActiveX, em vez do documento. A seguir está uma lista de métodos sem suporte e as propriedades de controles de formulários do Windows para o Word e Excel:

- Não há suporte para propriedades de controles do Excel:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Não há suporte para métodos e propriedades de controles do Word:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Você também não é possível definir a <xref:System.Windows.Forms.Control.Left> ou <xref:System.Windows.Forms.Control.Top> propriedade dos controles de formulários do Windows que estão de acordo com o texto em um documento do Word. Controles dos Windows Forms são adicionados em conformidade com o texto nos seguintes casos:

- Programaticamente, você adiciona um controle a um documento do Word e usa um método que especifica um intervalo para o local.

- Você pode adicionar um controle dos Windows Forms a um documento do Word em tempo de design. Você pode alterar isso modificando o controle no designer.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Diferenças em controles dos Windows Forms em documentos do Office

Controles de formulários do Windows geralmente têm o mesmo comportamento em um documento do Office, como eles em um formulário do Windows, mas existem algumas diferenças. A tabela a seguir descreve as diferenças que existem para controles dos Windows Forms em documentos do Office.

|Funcionalidade|Diferença|
|-------------------|----------------|
|Ordem de tabulação do controle|Você não pode visualizar os controles colocados em uma planilha do Excel ou um documento do Word.|
|Agrupamento de controle|Não é possível usar um <xref:System.Windows.Forms.GroupBox> controle contenha outros controles em um documento do Office. Quando você adiciona vários botões de opção diretamente para o documento, os botões de opção não são mutuamente exclusivos. Você pode escrever código para tornar os botões de opção mutuamente excludentes; No entanto, a abordagem preferida é adicionar os botões de opção para um controle de usuário e, em seguida, adicione o controle de usuário ao documento. Para obter mais informações, consulte o exemplo de controles do Word ou Excel Controls Sample em [exemplos de desenvolvimento do Office e instruções passo a passo](../vsto/office-development-samples-and-walkthroughs.md).|
|Tipo de controle|Controles de formulários do Windows usados em documentos são encapsulados em uma classe fornecida pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que fornece funcionalidade adicional específica os controles para o documento do Word ou planilha do Excel. Por exemplo, se você tiver um **botão** control em uma planilha do Excel, certifique-se de especificar o tipo como <xref:Microsoft.Office.Tools.Excel.Controls.Button> em vez de <xref:System.Windows.Forms.Button> quando referenciando ou convertendo o objeto.|
|Controle de posição e tamanho|O tamanho e posição do controle é determinada pelas propriedades que fazem parte do contêiner de controle ActiveX. As propriedades do controle ActiveX levam valores diferentes de propriedades equivalentes de um controle Windows Forms. Quando você define o `Top`, `Left`, `Height`, ou `Width` propriedades de um controle, ele é medido em pontos, em vez de pixels.|
|Posição do controle em documentos do Word|Se você adicionar controles a um layout baseado em fluxo, tenha em mente que os controles fará o fluxo com o conteúdo como as alterações de conteúdo. Você não é possível ancorar o controle a um parágrafo quando você arrasta-o do **caixa de ferramentas** porque o controle é adicionado ao documento do Word com texto. Se você usar outro método para adicionar o controle, como duas vezes no controle, o controle é inserido de acordo com a opção do Word que você definiu para a inserção de imagens.<br /><br /> Não é possível definir a `Left` ou `Top` propriedade de um controle que está alinhado com texto.<br /><br /> Você não pode colocar controles em um cabeçalho ou rodapé ou dentro de um subdocumento.|
|Eventos de controle|Quando o controle for selecionado, ela gera eventos na seguinte ordem:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Quando o controle estiver desmarcado, ela gera eventos na seguinte ordem:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Dimensionamento do controle|Quando você altera a configuração de zoom de um documento para algo diferente de 100%, os controles são desativados, embora eles sejam exibidos para dimensionar com o documento. Por exemplo, se você clicar em um botão quando o documento estiver no zoom % 130, ele mostrará uma mensagem de que o controle foi desativado até que o zoom é definido como 100%. Os controles funcionará corretamente quando você altera o zoom para 100%.|
|Valores de propriedade de controle|Embora as propriedades de controles em um formulário do Windows são definidas em um valor inteiro, eles são definidos para um único para controles em um documento do Word. No Excel, os valores de propriedade dos controles são definidos para um duplo. Se o `Height` e `Width` propriedade de um controle em uma planilha excede o tamanho da planilha ou da tela, o valor é truncado.|
|Redimensionamento do controle|Se você redimensionar um controle no documento usando um dos oito alças de dimensionamento, as novas dimensões do controle não são refletidas na **propriedades** janela até que o controle é remarcado.|
|Comportamento de controle|Controles em uma planilha do Excel podem se comportar de forma imprevisível quando a janela de planilha é dividida. Por exemplo, acesso a um <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> na planilha podem estar disponíveis apenas em uma das janelas.|
|Nomeação de controle|É possível usar palavras reservadas para nomear controles. Por exemplo, se você adicionar um <xref:Microsoft.Office.Tools.Excel.Controls.Button> em uma planilha e altere o nome para **sistema**, erros ocorrem quando você compila o projeto.|
|Adicionando controles de programaticamente|Não use o construtor do controle para adicionar um controle ao documento em tempo de execução. Em vez disso, use os métodos auxiliares fornecidos pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por exemplo, use o <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> método para adicionar um botão em uma planilha. Se você quiser adicionar um controle que não é compatível com esses métodos auxiliares, você pode usar o `AddControl` método. Para obter mais informações, consulte [adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Copiar controles|Se você copiar um controle Windows Forms e cole-o em um documento em tempo de execução, um contêiner vazio controle ActiveX é colado no documento. O controle Windows Forms não aparecem no novo local e code-behind do controle original não é copiado para o contêiner de controle ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Limitações em projetos de nível de documento

Algumas limitações do uso de controles Windows Forms em documentos são exclusivas a projetos no nível de documento.

### <a name="control-support-at-design-time"></a>Suporte de controle em tempo de design

Determinados controles de formulários do Windows são removidos do **caixa de ferramentas** quando uma planilha do Excel ou um documento do Word é aberto no designer do Visual Studio. Isso ocorre devido a limitações técnicas ou porque a funcionalidade já está disponível no Word ou Excel. Projetos do Excel e Word dão suporte a todos os controles do Windows Forms e outros componentes que aparecem na **caixa de ferramentas** quando o documento tem o foco, e você também pode adicionar controles de terceiros para uma planilha ou um documento.

> [!NOTE]
> Todos os controles são removidos do **caixa de ferramentas** quando um documento está protegido. Para obter informações sobre a proteção do documento, consulte [documentar a proteção em nível de documento soluções](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Controles de terceiros devem ter o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo definido como **verdadeiro** para ser usado em uma solução do Office.

Os seguintes controles e componentes não estão disponíveis na **caixa de ferramentas**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Suporte para controles ActiveX herdados

Se você criar um projeto do Office em nível de documento que usa um documento do Word existente ou uma pasta de trabalho do Excel que contém controles ActiveX, a funcionalidade dos controles ActiveX não está perdida; No entanto, não há nenhum suporte para adicionar novos controles ActiveX a seus documentos no Visual Studio. Por exemplo, se seu documento do Word possui um botão do **controle** caixa de ferramentas que executa uma macro Visual Basic for Applications (VBA), ele continuará a executar a macro depois que o documento foi usado em um projeto do Office. No entanto, é recomendável remover os controles ActiveX e macros VBA e substituí-los com controles de Windows Forms e o código gerenciado.

## <a name="see-also"></a>Consulte também

- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Controles de formulários do Windows na visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Como: Adicionar controles dos Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
