---
title: Introdução à programação de suplementos do VSTO
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 39cf3e8d59a2ced26f878da979fa87fc663b5bab
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253586"
---
# <a name="get-started-programming-vsto-add-ins"></a>Introdução à programação de suplementos do VSTO
  Você pode usar os suplementos do VSTO para automatizar Microsoft Office aplicativos, estender recursos do aplicativo e personalizar a interface do usuário do aplicativo. Para obter informações sobre como os suplementos do VSTO se comparam com outros tipos de soluções do Office que você pode criar usando o Visual Studio, consulte [visão geral &#40;do desenvolvimento de soluções do Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Criar projetos de suplemento do VSTO
 Crie projetos de suplemento do VSTO usando um dos modelos de projeto de suplemento do VSTO na caixa de diálogo **novo projeto** . Esses modelos incluem referências de assembly e arquivos de projeto necessários. O Visual Studio fornece modelos de projeto de suplemento do VSTO para a maioria dos aplicativos no Office.

 Para obter mais informações sobre como criar um projeto de suplemento do VSTO, consulte [como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio. Para obter mais informações sobre os modelos de projeto, consulte [visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md).

## <a name="develop-vsto-add-in-projects"></a>Desenvolver projetos de suplemento do VSTO
 Quando você cria um projeto de suplemento do VSTO, o Visual Studio cria automaticamente um arquivo de código *ThisAddIn. vb* (no [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) C#ou *ThisAddIn.cs* (in). Esse arquivo contém a `ThisAddIn` classe, que fornece a base para seu suplemento do VSTO. Você pode usar os membros dessa classe para executar o código quando o suplemento do VSTO é carregado ou descarregado, para acessar o modelo de objeto do aplicativo host e para estender recursos do aplicativo. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatizar aplicativos usando os modelos de objetos
 Os modelos de objeto do Microsoft Office aplicativos expõem muitos tipos que você pode programar em um suplemento do VSTO. Você pode usar esses tipos para automatizar o aplicativo. Por exemplo, você pode criar e enviar programaticamente uma mensagem de email no Outlook, ou pode abrir um documento e adicionar conteúdo no Word. Para obter mais informações sobre como acessar o modelo de objeto do aplicativo host no código, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

 Para obter mais informações sobre os modelos de objeto de aplicativos Microsoft Office específicos, consulte os seguintes tópicos:

- [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)

- [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)

- [Visão geral do modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)

- [Soluções do InfoPath](../vsto/infopath-solutions.md)

- [Soluções do PowerPoint](../vsto/powerpoint-solutions.md)

- [Soluções de projeto](../vsto/project-solutions.md)

- [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Personalizar a interface do usuário de aplicativos
 Há várias maneiras diferentes de personalizar a interface do usuário do aplicativo host usando um suplemento do VSTO:

- Para Excel e Word, você pode adicionar controles gerenciados a documentos. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

- Você pode personalizar a faixa de faixas se o aplicativo oferecer suporte a ela. Para obter mais informações, consulte [visão geral da faixa](../vsto/ribbon-overview.md)de visualização.

- Você pode criar um painel de tarefas personalizado se o aplicativo oferecer suporte a ele. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).

- Para o Outlook, você pode criar uma região de formulário personalizada. Para obter mais informações, consulte [criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).

- Para todos os aplicativos Microsoft Office, você pode exibir Windows Forms em seu suplemento do VSTO.

  Para obter mais informações sobre como personalizar a interface do usuário do Microsoft Office Applications, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Próximas etapas
 Para saber como criar suplementos do VSTO, consulte as instruções a seguir:

- [Passo a passo: Criar seu primeiro suplemento do VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Passo a passo: Criar seu primeiro suplemento do VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Passo a passo: Criar seu primeiro suplemento do VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Passo a passo: Criar seu primeiro suplemento do VSTO para o projeto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Passo a passo: Criar seu primeiro suplemento do VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Esses passo a passos apresentam a você as ferramentas de desenvolvimento do Office no Visual Studio e o modelo de programação para os suplementos do VSTO.

  Para obter uma lista de tópicos que orientam algumas das tarefas comuns em projetos do Office, consulte [tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Consulte também
- [Como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Introdução &#40;ao desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
