---
title: Projetos do Office no ambiente do Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65f3a3abfe7e49872c7131a247d74612200bf42a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62978052"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Projetos do Office no ambiente do Visual Studio
  Os projetos do Microsoft Office têm uma experiência de desenvolvimento semelhante a outros tipos de projeto no Visual Studio, como projetos do Windows Forms. Quando você cria ou abre um projeto do Office, os itens do projeto aparecem no **Gerenciador de soluções**. Para projetos no nível de documento, o documento (isto é, o documento do Word ou a pasta de trabalho do Excel) é aberto no Visual Studio e se comporta como um designer visual.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="project-items-in-solution-explorer"></a>Itens de projeto no Gerenciador de Soluções
 Em um projeto de nível de documento, **Gerenciador de soluções** exibe os seguintes itens padrão:

- Nós do documento, da pasta de trabalho e das folhas que são personalizados pelo projeto. Esses nós servem como contêineres para os arquivos de código que são associados ao documento, à pasta de trabalho e às folhas.

- Arquivos de código que são associados ao documento, à pasta de trabalho e às folhas que são personalizados pelo projeto. Em projetos do Word, os arquivos de código são associados ao documento ou modelo do Word. Em projetos do Excel, os arquivos de código são associados à pasta de trabalho ou ao modelo do Excel, e a cada planilha e planilha de gráfico na pasta de trabalho ou no modelo.

- Arquivos de projeto que você não tem pretensão de editar diretamente. Para obter mais informações, consulte [arquivos de projeto ocultos](#hiddenfiles).

  Em um projeto de suplemento do VSTO, **Gerenciador de soluções** exibe os seguintes itens padrão:

- O nó do aplicativo. Esse nó tem o mesmo nome que o aplicativo host, como **Word**, **Excel**ou **Outlook**. O nó do aplicativo contém o arquivo de código ThisAddIn. Ele também fornece o **namespace para a propriedade do item de host** . Para obter mais informações sobre essa propriedade, consulte [Propriedades em projetos do Office](../vsto/properties-in-office-projects.md).

- O arquivo de código ThisAddIn. Esse arquivo contém a `ThisAddIn` classe gerada para seu suplemento do VSTO. Para obter mais informações sobre essa classe, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

- Arquivos de projeto que você não tem pretensão de editar diretamente. Para obter mais informações, consulte [arquivos de projeto ocultos](#hiddenfiles).

### <a name="temporary-certificates"></a>Certificados temporários
 Os projetos do Office também incluem um certificado temporário chamado *Project Name*_TemporaryKey. pfx. Esse certificado é usado para assinar o aplicativo e os manifestos de implantação do projeto durante o desenvolvimento. Para obter mais informações, consulte [Grant Trust to Office Solutions](../vsto/granting-trust-to-office-solutions.md) and [Secure Office Solutions](../vsto/securing-office-solutions.md).

### <a name="hidden-project-files"></a><a name="hiddenfiles"></a> Arquivos de projeto ocultos
 Vários arquivos de projeto são ocultados por padrão. Esses arquivos são gerados pelo Visual Studio e diferem por tipo de projeto. Para exibir os arquivos ocultos, clique em **Mostrar todos os arquivos** em **Gerenciador de soluções**.

 Não modifique os arquivos de projeto ocultos. A alteração direta desses arquivos não tem suporte e pode corromper seu projeto. Os arquivos de projeto ocultos são regenerados sempre que determinadas alterações ocorrerem no documento. Se você fizer alterações manuais em um arquivo de projeto oculto, essas alterações serão perdidas quando o arquivo for regenerado.

## <a name="document-designer-in-document-level-projects"></a>Designer de documentos em projetos de nível de documento
 Os projetos no nível de documento do Excel e Word fornecem um designer que hospeda o documento que é associado ao seu projeto no Visual Studio. O designer permite modificar o documento sem precisar sair do ambiente do Visual Studio.

 Para abrir um documento no designer, clique duas vezes no arquivo de código em **Gerenciador de soluções** associado ao documento. Por exemplo, para abrir a planilha **Plan1** no designer em um projeto do Excel, clique duas vezes no arquivo de código **Plan1** .

 Ao modificar o documento no designer, você pode aproveitar a funcionalidade nativa do aplicativo do Office. Por exemplo, é possível digitar texto no documento ou em uma planilha, ou usar a Faixa de Opções para executar tarefas como adicionar uma tabela ou um gráfico. Por padrão, o mapeamento do atalho de teclado é padronizado para o mapeamento do Visual Studio. Para usar mapeamentos de atalho de teclado do Office, altere as configurações no nó **Microsoft Office configurações de teclado** na caixa de diálogo **Opções** no menu **ferramentas** .

### <a name="controls-on-documents"></a>Controles em documentos
 Você pode arrastar *controles de host* e controles de Windows Forms da **caixa de ferramentas** do Visual Studio para a superfície de design do documento. Os controles de host são versões especializadas de objetos do Office, como controles de conteúdo do Word e intervalos do Excel, que podem ser usados em projetos do Office criados usando o Visual Studio. Os controles de host têm recursos adicionais que não estão disponíveis nos objetos do Office correspondentes, como associação de dados e eventos adicionais.

 Para obter mais informações, consulte Visão geral de [itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md) e [controles do Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Planilhas e pastas de trabalho do Excel no designer
 Ao abrir uma planilha no designer, você pode modificá-la da mesma forma que o faz quando ela é aberta diretamente no Excel. Se você clicar duas vezes na célula de uma planilha, a célula é alterada para o modo de edição. Se você clicar duas vezes em uma célula que contém um controle de host, o editor de código será aberto e o Visual Studio gerará o manipulador de eventos padrão para o controle. Para navegar para outras planilhas, você pode clicar nas guias da planilha na parte inferior do designer.

 Quando você abre a pasta de trabalho no designer, não há superfície de design. O modo de exibição de design da pasta de trabalho é uma grande bandeja de componente que preenche o designer.

 A pasta de trabalho e cada folha dela têm um arquivo de código associado. Cada arquivo de código contém uma classe de *item de host* gerada que representa a pasta de trabalho ou planilha. Para obter mais informações, consulte [automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md).

### <a name="word-documents-in-the-designer"></a>Documentos do Word no designer
 Ao abrir o documento no designer, você pode modificá-lo da mesma forma que o faz quando ele é aberto diretamente no Word. Se você clicar duas vezes em uma palavra no documento, essa palavra será selecionada. No entanto, se a palavra estiver dentro de um controle de host, o editor de códigos será aberto e o Visual Studio vai gerar o manipulador de eventos padrão para o controle.

 O documento tem um arquivo de código associado. O arquivo de código contém uma classe de *item de host* gerada que representa o documento. Para obter mais informações, consulte [documentar item de host](../vsto/document-host-item.md).

### <a name="design-mode-vs-runtime-mode"></a>Modo de design versus modo de tempo de execução
 Quando um documento é aberto no ambiente do Visual Studio, ele está sempre no *modo de design*. Algumas tarefas, como arrastar um controle de host para a superfície de documento, podem ser executadas somente no modo de design.

 Para exibir o documento no *modo de tempo de execução*, você deve abrir o aplicativo e o documento fora do Visual Studio. Também é possível compilar e executar o projeto, que abrirá automaticamente o documento e o aplicativo fora do Visual Studio.

## <a name="code-editor"></a>Editor de Códigos
 O Editor de Códigos permite exibir e modificar os arquivos de código visíveis na sua solução. Esses arquivos contêm o código que define o comportamento da sua solução.

 Para obter mais informações sobre o editor de código, consulte [escrever código no editor de código e de texto](../ide/writing-code-in-the-code-and-text-editor.md). Para obter mais informações sobre como escrever código em projetos do Office, consulte [escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md).

## <a name="properties-window"></a>Janela de Propriedades
 A janela **Propriedades** exibe propriedades para itens de projeto que são selecionados em **Gerenciador de soluções**e para elementos de interface do usuário que são selecionados no designer, como controles ou o documento em um projeto de nível de documento. Algumas propriedades são específicas do aplicativo e do documento, enquanto outras são iguais em todos os projetos.

## <a name="data-sources-window"></a>janela Fontes de Dados
 Você pode usar a janela **fontes de dados** em projetos do Office de nível de documento para arrastar uma fonte de dados para o documento e criar um controle associado à fonte de dados. Para obter mais informações, confira [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Confira também

- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)
- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Propriedades em projetos do Office](../vsto/properties-in-office-projects.md)
