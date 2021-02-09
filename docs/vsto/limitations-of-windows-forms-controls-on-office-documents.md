---
title: Limitações de controles de Windows Forms em documentos do Office
description: Saiba mais sobre as limitações de métodos de controle de Windows Forms e propriedades em documentos Microsoft Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc507d31f791a3f3d7addbcffc0b9b87963d443f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888713"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitações de controles de Windows Forms em documentos do Office

Há algumas diferenças entre os controles de Windows Forms que são adicionados a Microsoft Office documentos do Word ou Microsoft Office planilhas do Excel e controles de Windows Forms que são adicionados ao Windows Forms. Por exemplo, quando você adiciona um <xref:Microsoft.Office.Tools.Word.Controls.Button> controle a um documento, propriedades como <xref:System.Windows.Forms.Control.Dock> , <xref:System.Windows.Forms.Control.Anchor> e <xref:System.Windows.Forms.Control.TabIndex> não se comportam como você pode esperar.

Muitas dessas diferenças são causadas pela maneira como os controles de Windows Forms são hospedados em documentos. Quando um controle de Windows Forms é adicionado a um documento, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] insere um controle ActiveX que hospeda o controle de Windows Forms no documento. O controle de Windows Forms não é inserido diretamente no documento.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitações de métodos e propriedades de controles de Windows Forms

Há vários métodos e propriedades de Windows Forms controles que não funcionam da mesma maneira em um documento como fariam em um Windows Form e, portanto, é recomendável que eles não sejam usados. Por exemplo, definir propriedades como <xref:System.Windows.Forms.Control.Dock> e <xref:System.Windows.Forms.Control.Anchor> afeta apenas a posição do controle em relação ao controle ActiveX do contêiner, em vez do documento. Veja a seguir uma lista de métodos e propriedades sem suporte de controles de Windows Forms para Word e Excel:

- Propriedades sem suporte de controles do Excel:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Métodos e propriedades sem suporte de controles do Word:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Você também não pode definir <xref:System.Windows.Forms.Control.Left> a <xref:System.Windows.Forms.Control.Top> propriedade ou de Windows Forms controles que estão alinhados com o texto em um documento do Word. Windows Forms controles são adicionados de acordo com o texto nos seguintes casos:

- Você adiciona programaticamente um controle a um documento do Word e usa um método que especifica um intervalo para o local.

- Você adiciona um controle de Windows Forms a um documento do Word em tempo de design. Você pode alterar isso modificando o controle no designer.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Diferenças em controles de Windows Forms em documentos do Office

Os controles de Windows Forms geralmente têm o mesmo comportamento em um documento do Office como eles fazem em um formulário do Windows, mas existem algumas diferenças. A tabela a seguir descreve as diferenças existentes para controles de Windows Forms em documentos do Office.

|Funcionalidade|Diferença|
|-------------------|----------------|
|Ordem das guias de controle|Não é possível tabular os controles colocados em uma planilha do Excel ou em um documento do Word.|
|Agrupamento de controle|Você não pode usar um <xref:System.Windows.Forms.GroupBox> controle para conter outros controles em um documento do Office. Quando você adiciona vários botões de opção diretamente ao documento, os botões de opção não são mutuamente exclusivos. Você pode escrever código para tornar os botões de opção mutuamente exclusivos; no entanto, a abordagem preferida é adicionar os botões de opção a um controle de usuário e, em seguida, adicionar o controle de usuário ao documento. Para obter mais informações, consulte o exemplo de controles do Word ou exemplos de controles do Excel em [exemplos de desenvolvimento do Office e passo a passos](../vsto/office-development-samples-and-walkthroughs.md).|
|Tipo de controle|Windows Forms controles usados em documentos são encapsulados em uma classe fornecida pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que fornece aos controles funcionalidade adicional específica para a planilha do Excel ou documento do Word. Por exemplo, se você tiver um controle de **botão** em uma planilha do Excel, certifique-se de especificar o tipo como <xref:Microsoft.Office.Tools.Excel.Controls.Button> em vez de <xref:System.Windows.Forms.Button> ao referenciar ou converter o objeto.|
|Posição e tamanho do controle|O tamanho e a posição do controle são determinados pelas propriedades que fazem parte do controle ActiveX do contêiner. As propriedades do controle ActiveX usam valores diferentes das propriedades equivalentes de um controle de Windows Forms. Quando você define as `Top` `Left` Propriedades,, `Height` ou `Width` de um controle, ele é medido em pontos, em vez de pixels.|
|Posição de controle em documentos do Word|Se você adicionar controles a um layout baseado em fluxo, tenha em mente que os controles fluirão com o conteúdo conforme o conteúdo é alterado. Você não pode ancorar o controle em um parágrafo ao arrastá-lo da **caixa de ferramentas** porque o controle é adicionado ao documento do Word em linha com texto. Se você usar outro método para adicionar o controle, como clicar duas vezes no controle, o controle será inserido de acordo com a opção do Word que você definiu para inserir imagens.<br /><br /> Você não pode definir `Left` a `Top` propriedade ou de um controle que está embutido em texto.<br /><br /> Não é possível posicionar controles em um cabeçalho ou rodapé, ou dentro de um subdocumento.|
|Eventos de controle|Quando o controle é selecionado, ele gera eventos na seguinte ordem:<br /><br /> uma.  `Enter`<br />2.  `GotFocus`<br /><br /> Quando o controle é desmarcado, ele gera eventos na seguinte ordem:<br /><br /> uma.  `Leave`<br />2.  `Validating`<br />Beta.  `Validated`<br />quatro.  `LostFocus`|
|Dimensionamento de controle|Quando você altera a configuração de zoom de um documento para algo diferente de 100%, os controles são desabilitados, embora eles pareçam ser dimensionados com o documento. Por exemplo, se você clicar em um botão quando o documento estiver no nível de zoom de 130%, ele mostrará uma mensagem informando que o controle foi desabilitado até que o zoom seja definido como 100%. Os controles funcionarão corretamente quando você alterar o zoom para 100%.|
|Valores de propriedade de controle|Embora as propriedades de controles em um Windows Form sejam definidas como um valor inteiro, elas são definidas como um único para controles em um documento do Word. No Excel, os valores de propriedade de controles são definidos como um duplo. Se a `Height` `Width` propriedade e de um controle em uma planilha exceder o tamanho da planilha ou da tela, o valor será truncado.|
|Redimensionamento de controle|Se você redimensionar um controle no documento usando um dos oito identificadores de dimensionamento, as novas dimensões de controle não serão refletidas na janela **Propriedades** até que o controle seja reselecionado.|
|Comportamento do controle|Os controles em uma planilha do Excel podem se comportar de modo não previsível quando a janela da planilha é dividida. Por exemplo, o acesso a uma <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> na planilha pode estar disponível apenas em uma das janelas.|
|Nomenclatura de controle|Você não pode usar palavras reservadas para controles de nome. Por exemplo, se você adicionar um <xref:Microsoft.Office.Tools.Excel.Controls.Button> a uma planilha e alterar o nome para o **sistema**, ocorrerão erros quando você compilar o projeto.|
|Adicionando controles programaticamente|Não use o construtor do controle para adicionar um controle ao seu documento em tempo de execução. Em vez disso, use os métodos auxiliares fornecidos pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Por exemplo, use o <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> método para adicionar um botão a uma planilha. Se você quiser adicionar um controle que não é suportado por esses métodos auxiliares, você pode usar o `AddControl` método. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Copiando controles|Se você copiar um controle de Windows Forms e colá-lo em um documento em tempo de execução, um controle ActiveX de contêiner vazio será colado no documento. O controle de Windows Forms não aparece no novo local e o código por trás do controle original não é copiado para o controle ActiveX de contêiner.|

## <a name="limitations-in-document-level-projects"></a>Limitações em projetos de nível de documento

Algumas limitações do uso de controles de Windows Forms em documentos são exclusivas para projetos de nível de documento.

### <a name="control-support-at-design-time"></a>Controlar o suporte em tempo de design

Determinados controles de Windows Forms são removidos da **caixa de ferramentas** quando uma planilha do Excel ou documento do Word é aberto no designer do Visual Studio. Isso ocorre devido a limitações técnicas ou porque a funcionalidade já está disponível no Word ou no Excel. Os projetos do Excel e do Word dão suporte a todos os controles de Windows Forms e outros componentes que aparecem na **caixa de ferramentas** quando o documento tem foco, e você também pode adicionar controles de terceiros a uma planilha ou documento.

> [!NOTE]
> Todos os controles são removidos da **caixa de ferramentas** quando um documento é protegido. Para obter informações sobre a proteção de documentos, consulte [proteção de documentos em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Os controles de terceiros devem ter o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo definido como **true** para serem usados em uma solução do Office.

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

Se você criar um projeto do Office de nível de documento que usa um documento do Word ou uma pasta de trabalho do Excel existente que contém controles ActiveX, a funcionalidade dos controles ActiveX não será perdida; no entanto, não há suporte para adicionar novos controles ActiveX a seus documentos no Visual Studio. Por exemplo, se o documento do Word tiver um botão da caixa de ferramentas de **controle** que executa uma macro Visual Basic for Applications (VBA), ele continuará a executar a macro depois que o documento tiver sido usado em um projeto do Office. No entanto, é recomendável que você remova os controles ActiveX e as macros do VBA e substitua-os por controles de Windows Forms e código gerenciado.

## <a name="see-also"></a>Confira também

- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Visão geral dos controles de Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Como: adicionar controles de Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
