---
title: Soluções do Outlook
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b27f874766853fb5239c96ec178233935484d1b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551478"
---
# <a name="outlook-solutions"></a>Soluções do Outlook
  O Visual Studio fornece modelos de projeto que você pode usar para criar suplementos do VSTO para Microsoft Office Outlook. Você pode usar os suplementos do VSTO para automatizar o Outlook, estender os recursos do Outlook ou personalizar a interface do usuário do Outlook. Para obter mais informações sobre os suplementos do VSTO, consulte [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>Criar um projeto de suplemento do VSTO do Outlook
 Crie projetos do Outlook usando o modelo de projeto de **suplemento do Outlook** na caixa de diálogo **novo projeto** . Esse modelo inclui as referências de assembly necessárias e os arquivos de projeto.

 Para obter mais informações sobre como criar um projeto de suplemento do VSTO, consulte [como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio. Para obter mais informações sobre os modelos de projeto, consulte [visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md).

## <a name="outlook-vsto-add-in-programming-model"></a>Modelo de programação de suplemento do VSTO do Outlook
 Quando você cria um projeto de suplemento do VSTO do Outlook, o Visual Studio gera uma classe `ThisAddIn`, chamada, que é a base da sua solução. Essa classe fornece um ponto de partida para escrever seu código e também expõe o modelo de objeto do Outlook para seu suplemento do VSTO.

 Para obter mais informações sobre `ThisAddIn` a classe e outros recursos que você pode usar em um suplemento do VSTO, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatizar o Outlook usando o modelo de objeto do Outlook
 O modelo de objeto do Outlook expõe muitos tipos que você pode usar para automatizar o Outlook. Esses tipos permitem que você escreva código para realizar tarefas comuns:

- Crie e envie mensagens de email programaticamente.

- Enviar novas solicitações de reunião.

- Pesquisar itens em pastas do Outlook.

  Para obter mais informações, consulte [visão geral do modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Personalizar a interface do usuário de um aplicativo do Outlook

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Adicione guias personalizadas à faixa de faixas de um inspetor do Outlook.|[Visão geral da faixa de faixas](../vsto/ribbon-overview.md)|
|Adicione grupos personalizados a uma guia interna em um inspetor do Outlook.|[Como: Personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md)|
|Adicionar um painel de tarefas personalizado que aparece em um inspetor do Outlook|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md).|
|Adicione uma região de formulário que estenda ou substitua formulários existentes do Outlook.|[Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)|

 Para obter mais informações sobre como personalizar a interface do usuário do Outlook e de outros aplicativos Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Visão geral do modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)|Fornece uma visão geral dos objetos que são fornecidos pelo modelo de objeto do Outlook.|
|[Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)|Explica as ferramentas fornecidas pelo Visual Studio que facilitam o design, o desenvolvimento e a depuração de regiões de formulário.|
|[Passo a passo: Criar seu primeiro suplemento do VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Mostra como criar um suplemento do VSTO para Microsoft Office Outlook.|
|[Outlook 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199013)|A área da biblioteca MSDN, na qual você pode encontrar artigos e documentação de referência sobre o desenvolvimento de soluções do Outlook (não específico ao desenvolvimento do Office usando o Visual Studio).|
