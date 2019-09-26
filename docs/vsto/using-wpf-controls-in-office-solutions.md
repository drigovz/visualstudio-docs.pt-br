---
title: Usar controles WPF em soluções do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0540ac17ca64f24ead19b8b3655175d12fa42e41
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253972"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Usar controles WPF em soluções do Office

Embora as soluções criadas usando as ferramentas de desenvolvimento do Office no Visual Studio sejam projetadas para trabalhar diretamente com controles Windows Forms, você também pode usar controles WPF em suas soluções. Windows Presentation Foundation (WPF) é uma alternativa ao Windows Forms para criar interfaces do usuário. O WPF usa uma linguagem de marcação chamada Extensible Application Markup Language (XAML) para fornecer novas técnicas para incorporar a interface do usuário, mídia e documentos. Para obter mais informações, consulte [visão geral do WPF](../designers/introduction-to-wpf.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Qualquer elemento de interface do usuário que pode hospedar Windows Forms controles em uma solução do Office também pode hospedar controles WPF. Eles incluem os seguintes elementos:

- Documentos e planilhas em personalizações em nível de documento.

- Painéis de ações em personalizações em nível de documento.

- Painéis de tarefas personalizados em suplementos do VSTO.

- Regiões de formulário em suplementos do VSTO para Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Adicionar controles WPF a projetos do Office em tempo de design

Você não pode adicionar controles WPF diretamente a elementos de interface do usuário em soluções do Office. Em vez disso, adicione um item de **controle de usuário (WPF)** ao seu projeto e use-o como a superfície de design para controles do WPF. Em seguida, adicione o controle de usuário do WPF a um elemento de interface de usuário em seu projeto.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Para adicionar controles WPF a um painel Ações, ao painel de tarefas personalizado ou à região de formulário

1. Abra um projeto ao qual você deseja adicionar um painel de tarefas personalizado, um painel ações ou uma região de formulário.

2. Adicione um item de **controle de usuário (WPF)** ao seu projeto.

3. Na **caixa de ferramentas**, adicione controles WPF à superfície de design do controle de usuário do WPF.

     Por padrão, quando o designer de controle de usuário do WPF está aberto, a **caixa de ferramentas** contém apenas controles WPF.

4. Compile o projeto.

5. Adicione um painel Ações, uma região de formulário ou um painel de tarefas personalizado ao seu projeto:

    - Para regiões de formulário, adicione um item de **região de formulário do Outlook** ao projeto. Para obter mais informações, confira [Como: Adicione uma região de formulário a um projeto](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)de suplemento do Outlook.

    - Para painéis de ações, adicione um **controle painel de ações** ou um item de **controle de usuário** ao projeto. Para obter mais informações, confira [Como: Adicione um painel ações a documentos do Word ou a pastas](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)de trabalho do Excel.

    - Para painéis de tarefas personalizados, adicione um item de **controle de usuário** ao projeto. Para obter mais informações, confira [Como: Adicione um painel de tarefas personalizado a um](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)aplicativo.

6. Na guia **controles de usuário WPF** do ProjectName da **caixa de ferramentas**, arraste o controle de usuário do WPF para o designer do painel Ações, região de formulário ou painel de tarefas personalizado.

     O Visual Studio cria automaticamente <xref:System.Windows.Forms.Integration.ElementHost> um objeto que hospeda o controle de usuário do WPF no elemento da interface do usuário.

7. Recompile o projeto.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Para adicionar controles do WPF a um documento ou planilha em um projeto de nível de documento

1. Abra um projeto de nível de documento para Word ou Excel.

2. Adicione um item de **controle de usuário (WPF)** ao seu projeto.

3. Na **caixa de ferramentas**, adicione controles WPF à superfície de design do controle de usuário do WPF.

4. Compile o projeto.

5. Adicione um item de **controle de usuário** (ou seja, um Windows Forms controle de usuário) ao projeto.

6. Abra o designer para o controle de usuário Windows Forms.

7. Na guia **controles de usuário WPF** do ProjectName da **caixa de ferramentas**, arraste o controle de usuário do WPF para o designer.

     O Visual Studio cria automaticamente <xref:System.Windows.Forms.Integration.ElementHost> um objeto que hospeda o controle de usuário do WPF no controle de usuário Windows Forms.

8. Escreva o código que adiciona programaticamente o controle de usuário Windows Forms ao documento ou pasta de trabalho. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Não é possível arrastar o Windows Forms controle de usuário para o documento ou planilha no designer.

9. Recompile o projeto.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Hospedar controles WPF usando a classe ElementHost

O Visual Studio fornece recursos que ajudam a usar controles de Windows Forms em suas soluções do Office, mas não fornece recursos semelhantes para controles WPF. Por exemplo, você pode adicionar Windows Forms controles a documentos e planilhas em tempo de design arrastando controles da **caixa de ferramentas**ou em tempo de execução usando métodos auxiliares. No entanto, essas ferramentas não estão disponíveis para controles WPF.

Os controles do WPF <xref:System.Windows.Forms.Integration.ElementHost> usam a classe como uma camada de integração entre um controle de Windows Forms ou formulário e os controles do WPF. Quando você adiciona controles WPF à sua solução em tempo de design, o Visual Studio gera <xref:System.Windows.Forms.Integration.ElementHost> automaticamente um objeto para você.

## <a name="wpf-resources"></a>Recursos do WPF

Para obter mais informações sobre problemas de arquitetura e design para hospedar controles WPF em Windows Forms controles e formulários, consulte os seguintes tópicos:

- [Arquitetura de entrada de interoperabilidade Windows Forms e WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Mapeamento de propriedades Windows Forms e WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [Interoperação do WPF e Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Controles dos Windows Forms e controles do WPF equivalentes](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Para obter mais informações sobre como adicionar controles WPF a Windows Forms controles e formulários no Visual Studio em tempo de design, consulte os seguintes tópicos:

- [Passo a passo: Criar novo conteúdo do WPF em Windows Forms em tempo de design](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Passo a passo: Organizar o conteúdo do WPF em Windows Forms em tempo de design](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Passo a passo: Conteúdo do WPF de estilo](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Consulte também

- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
- [Visão geral dos controles de Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Visão geral do painel Ações](../vsto/actions-pane-overview.md)
- [Painéis de tarefas personalizados](../vsto/custom-task-panes.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Como: Adicionar um painel de ações a documentos do Word ou a pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Como: Adicionar um painel de tarefas personalizado a um aplicativo](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Como: Adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
