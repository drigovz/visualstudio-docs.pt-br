---
title: Visão geral dos controles de Windows Forms em documentos do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a101f22bccb3624eccff1edcea502c9350991392
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254908"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Visão geral dos controles de Windows Forms em documentos do Office
  Os controles de Windows Forms são objetos com os quais os usuários podem interagir para inserir ou manipular dados. Em projetos de nível de documento para Microsoft Office Excel e Microsoft Office Word, você pode adicionar controles de Windows Forms ao documento ou pasta de trabalho em seu projeto em tempo de design ou pode adicionar esses controles programaticamente em tempo de execução. Você pode adicionar esses controles programaticamente a qualquer documento ou planilha aberta em tempo de execução em um suplemento do VSTO para Excel ou Word.

 Para obter mais informações, confira [Como: Adicione controles de Windows Forms a documentos](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)do Office.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="use-windows-forms-controls"></a>Usar controles de Windows Forms

Você pode adicionar Windows Forms controles a documentos e a elementos da interface do usuário personalizáveis, incluindo painéis de ações, painéis de tarefas personalizados e Windows Forms. Os controles de Windows Forms geralmente têm o mesmo comportamento em documentos como nesses outros elementos da interface do usuário, mas existem algumas diferenças. Para obter informações, consulte [limitações de controles de Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

A decisão de adicionar Windows Forms controles a um documento ou a algum outro elemento de interface do usuário depende de vários fatores. Ao criar a interface do usuário da sua solução, considere os usos dos controles de Windows Forms, conforme descrito na tabela a seguir.

Em um documento.
- Quando você quiser exibir os controles 100% do tempo.

- Quando você deseja que os usuários insiram dados diretamente no documento, por exemplo, em documentos baseados em formulários em que a superfície de edição está bloqueada.

- Quando você deseja que os controles sejam exibidos em linha com os dados no documento. Por exemplo, se você estiver adicionando botões a cada linha de um objeto de lista, você desejaria que eles fiquem alinhados a cada item de lista.

No painel ações ou em um painel de tarefas personalizado.
- Quando você quiser fornecer informações contextuais ao usuário.

- Quando você deseja que apenas os resultados apareçam no documento, e não os controles de consulta e os dados.

- Quando você quiser garantir que os controles não sejam impressos com o documento.

- Quando você quiser garantir que os controles não interfiram na exibição do documento.

Em um formulário do Windows.
- Quando você quiser controlar o tamanho da interface do usuário.

- Quando você deseja impedir que os usuários ocultem ou excluam os controles.

- Quando você quiser obter entrada do usuário e impedir que o usuário faça nada no documento até que a entrada seja recebida.

## <a name="add-windows-forms-controls-programmatically"></a>Adicionar controles de Windows Forms programaticamente
 Você pode adicionar controles de Windows Forms a documentos do Word e planilhas do Excel em tempo de execução. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fornece métodos auxiliares para adicionar os controles de Windows Forms mais comuns. Esses métodos auxiliares permitem que você adicione controles rapidamente ao seu documento do Office e acesse a funcionalidade de controle de Windows Forms combinada e a funcionalidade relacionada ao Office desses controles.

 Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="use-windows-forms-controls-in-document-level-projects"></a>Usar controles de Windows Forms em projetos de nível de documento
 Alguns aspectos do uso de controles de Windows Forms em documentos são exclusivos para projetos de nível de documento, que permitem que você projete a interface do usuário do seu documento usando o designer do Visual Studio.

### <a name="create-custom-user-controls"></a>Criar controles de usuário personalizados
 Você pode adicionar um controle de usuário ao seu projeto e, em seguida, adicioná-lo à **caixa de ferramentas**. Em seguida, você pode arrastar o controle de usuário diretamente para o documento da mesma maneira que adicionaria um controle de Windows Forms ao seu documento. Há algumas coisas para ter em mente quando você cria controles de usuário:

- Não crie um controle de usuário **lacrado** . Quando você arrasta o controle para o documento, o Visual Studio gera uma classe wrapper derivada do controle de usuário para estendê-lo e dar suporte ao seu uso no documento. Se o controle de usuário estiver **lacrado**, o Visual Studio não poderá gerar a classe wrapper.

- Os controles de usuário devem <xref:System.Runtime.InteropServices.ComVisibleAttribute> ter o atributo definido como **true**. Os controles de usuário criados dentro de um projeto do Office têm esse atributo definido como **true** por padrão, mas os controles de usuário que fazem parte de projetos externos podem não ter esse atributo definido como **true**.

- Depois de adicionar um controle de usuário ao documento, não renomeie ou exclua <xref:System.Windows.Forms.UserControl> a classe do projeto. Se você precisar alterar o nome de um controle de usuário, deverá primeiro excluí-lo do documento e, em seguida, adicioná-lo novamente depois que o nome tiver sido alterado.

### <a name="arrange-controls-at-design-time"></a>Organizar controles em tempo de design
 Se você adicionar vários controles aos documentos do Word e do Excel em tempo de design, poderá definir rapidamente o alinhamento de todos os controles selecionados usando as barras de ferramentas **Microsoft Office Word** e **Microsoft Office Excel** no Visual Studio. Essas barras de ferramentas estão disponíveis somente quando um documento ou planilha é aberto no designer.

 Ao selecionar vários controles no designer, você pode usar os seguintes botões nessas barras de ferramentas para organizar os controles:

- **Alinhar à esquerda**

- **Alinhar centros**

- **Alinhar direitos**

- **Alinhar partes superiores**

- **Alinhar meios**

- **Alinhar partes inferiores**

- **Igualar espaçamento horizontal**

- **Igualar espaçamento vertical**

> [!NOTE]
> Em projetos do Word, esses botões serão habilitados somente se os controles selecionados não estiverem alinhados com o texto. Por padrão, os controles que você adiciona ao documento em tempo de design estão alinhados com o texto.

### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Impedir que dados antigos apareçam em pastas de trabalho do Excel durante o carregamento
 Quando você adiciona controles de Windows Forms a documentos ou planilhas em tempo de design, os controles permanecem no documento quando o usuário fecha o documento. Os controles adicionados em tempo de design também são chamados de *controles estáticos*.

 Quando uma pasta de trabalho do Excel que contém controles estáticos é aberta, a pasta de trabalho exibe um bitmap do controle em um controle ActiveX até que o código de personalização seja executado e carregue o controle real. O Excel cria esse bitmap e o armazena na pasta de trabalho sempre que a pasta de trabalho é salva. O bitmap mostra o controle como ele apareceu na última vez em que a pasta de trabalho foi salva, incluindo todos os dados que o controle estava exibindo. Para obter mais informações sobre o controle ActiveX que contém Windows Forms controles e bitmaps, consulte [limitações de controles de Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

 Em determinadas condições, o código não é carregado e apenas o bitmap é exibido, como quando o usuário abre a pasta de trabalho no modo de design. Além disso, se o usuário abrir a pasta de trabalho em um computador que não [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tem o instalado, a personalização não poderá ser executada para carregar os controles e, portanto, apenas o bitmap do controle estará visível. Você sempre deve remover informações pessoais de controles em pastas de trabalho antes de salvar a pasta de trabalho e enviá-la a outro usuário para garantir que suas informações pessoais não sejam divulgadas acidentalmente.

### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Corresponder o tamanho do controle ao tamanho da célula em uma planilha do Excel
 Você pode definir o controle a ser redimensionado automaticamente quando o tamanho da célula pai for alterado. Para obter mais informações, confira [Como: Redimensionar controles nas células](../vsto/how-to-resize-controls-within-worksheet-cells.md)da planilha.

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Adicionar componentes que são compartilhados por todas as planilhas
 Você pode adicionar componentes que deseja compartilhar entre todas as planilhas, como um <xref:System.Data.DataSet>, ao designer de pasta de trabalho em vez de às planilhas. O componente será exibido na bandeja do componente.

### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Fórmula para inserir controles em uma planilha do Excel
 Ao selecionar um controle no Excel, você verá **= Inserir ("WinForms. Control. host", "")** na **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.

### <a name="layout-style-of-controls-on-a-word-document"></a>Estilo de layout dos controles em um documento do Word
 Quando você adiciona um controle ao documento do Word em um projeto de nível de documento usando o designer do Visual Studio, o controle é adicionado em linha com texto. Para alterar o estilo de layout do controle, clique com o botão direito do mouse no controle e clique em **Formatar controle**. Selecione um estilo de disposição na página **layout** da caixa de diálogo **Formatar objeto** .

 Quando você adiciona um controle a um documento do Word em tempo de execução, você pode especificar o estilo de layout do novo controle usando `Add`a *classe de controle*diferente <xref:Microsoft.Office.Tools.Word.ControlCollection> \<> sobrecargas de método da classe:

- Para adicionar o controle em linha com texto, use uma sobrecarga que aceite um <xref:Microsoft.Office.Interop.Word.Range> que especifique o local do controle.

- Para adicionar o controle como uma forma flutuante, use uma sobrecarga que aceite as coordenadas esquerda e superior do controle.

  Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Se você abrir um modelo do Word no Visual Studio Designer, os controles não embutidos no modelo podem não estar visíveis porque o Visual Studio abre o modelo no modo de exibição **normal** . Para exibir os controles, altere a exibição para **layout de impressão**.

### <a name="controls-outside-the-main-document-body"></a>Controles fora do corpo do documento principal
 Não há suporte para controles de Windows Forms dentro de um cabeçalho ou rodapé, ou dentro de um subdocumento.

### <a name="add-components-at-design-time"></a>Adicionar componentes em tempo de design
 Determinados controles ou componentes não são visíveis no documento e, em vez disso, são exibidos em uma bandeja de componentes. O Visual Studio fornece uma bandeja de componentes para cada janela de documento. A bandeja do componente aparecerá na tela somente se houver componentes no documento.

## <a name="see-also"></a>Consulte também
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Visão geral do painel Ações](../vsto/actions-pane-overview.md)
- [Controles do Windows Forms](/dotnet/framework/winforms/controls/index)
- [Limitações de controles de Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Como: Adicionar controles de Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Como: Redimensionar controles dentro de células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Como: Ocultar controles em planilhas ao imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Passo a passo: Alterar a formatação da planilha usando controles de caixa de seleção](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Passo a passo: Alterar a formatação do documento usando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)
- [Passo a passo: Exibir texto em uma caixa de texto em uma planilha usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Passo a passo: Exibir texto em uma caixa de texto em um documento usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)
- [Limitações de controles de Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Passo a passo: Atualizar um gráfico em um documento usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)
- [Passo a passo: Atualizar um gráfico em uma planilha usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
