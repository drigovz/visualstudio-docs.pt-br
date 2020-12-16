---
title: Personalização da interface do usuário do Office
description: Saiba como você pode personalizar a interface do usuário de aplicativos Microsoft Office usando as ferramentas de desenvolvedor do Office no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 289b055ab84dd9c2c440b55f3d64fe1fe39b8e1b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527582"
---
# <a name="office-ui-customization"></a>Personalização da interface do usuário do Office
  Você pode personalizar a interface do usuário de aplicativos Microsoft Office usando as ferramentas de desenvolvedor do Office no Visual Studio. Este tópico descreve os recursos de interface do usuário que você pode personalizar nas seguintes seções:

- [Comparação de recursos da interface do usuário](#Comparison)

- [Painéis de ações e painéis de tarefas personalizados](#Actions)

- [Interface do usuário da faixa de para personalizada](#Ribbon)

- [Modo de exibição de Backstage](#Backstage)

- [Regiões de formulário do Outlook](#FormRegion)

- [Controles em documentos](#Controls)

- [Menus de atalho](#Shortcut)

## <a name="comparison-of-ui-features"></a><a name="Comparison"></a> Comparação de recursos da interface do usuário
 A tabela a seguir compara os principais recursos da interface do usuário que você pode personalizar em projetos Microsoft Office.

|Recurso|Tipos de projeto com suporte|Aplicativos Microsoft Office com suporte|
|-------------|-----------------------------|---------------------------------------------|
|Painel Ações|Personalizações no nível de documento|Excel<br /><br /> Word|
|Painéis de tarefas personalizados|Suplementos do VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|Interface do usuário da faixa de para personalizada|Personalizações no nível de documento<br /><br /> Suplementos do VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Modo de exibição de Backstage|Personalizações no nível de documento<br /><br /> Suplementos do VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Regiões de formulário do Outlook|Suplementos do VSTO|Outlook|
|Controles em documentos|Personalizações no nível de documento<br /><br /> Suplementos do VSTO|Excel<br /><br /> Word|
|Menus de atalho|Personalizações no nível de documento<br /><br /> Suplementos do VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|

## <a name="actions-panes-and-custom-task-panes"></a><a name="Actions"></a> Painéis de ações e painéis de tarefas personalizados
 Os painéis de tarefas são painéis de interface do usuário que normalmente são encaixados em um lado de uma janela em um aplicativo Microsoft Office. Quase todos os Microsoft Office aplicativos incluem painéis de tarefas internos. Um exemplo de um painel de tarefas é o painel de tarefas ajuda do Word.

 As ferramentas de desenvolvimento do Office no Visual Studio fornecem duas maneiras diferentes de personalizar os painéis de tarefas:

- Você pode adicionar um painel ações a uma personalização no nível do documento. Por padrão, o painel Ações é exibido no lado direito do aplicativo, à direita do documento. No entanto, o painel Ações também pode ser exibido à esquerda, à parte superior ou inferior do documento.

- Você pode adicionar um painel de tarefas personalizado a um suplemento do VSTO. Os usuários podem encaixar painéis de tarefas personalizados em diferentes lados da janela do aplicativo, ou podem arrastar painéis de tarefas personalizados para qualquer local na janela.

  Os painéis de ações e os painéis de tarefas personalizados fornecem funcionalidade hospedando uma variedade de controles para ajudar os usuários com tarefas como entrada de dados. Em comparação com um grupo de faixa de faixas, painéis de ações e painéis de tarefas personalizados fornecem uma área muito maior para incluir texto e controles.

  Para obter mais informações sobre os painéis de ações, consulte [visão geral do painel Ações](../vsto/actions-pane-overview.md). Para obter mais informações sobre painéis de tarefas personalizados, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).

## <a name="custom-ribbon-ui"></a><a name="Ribbon"></a> Interface do usuário da faixa de para personalizada
 Você pode personalizar a interface do usuário da faixa de Ribbon para expor a funcionalidade que você adiciona aos aplicativos no Office. A faixa de opção é uma maneira de organizar comandos relacionados (na forma de controles) para que eles sejam mais fáceis de localizar. Você pode criar suas próprias guias e grupos de faixa de e para dar aos usuários acesso à funcionalidade que você fornece em sua solução. A maioria dos recursos que foram acessados usando os menus e as barras de ferramentas em versões anteriores do sistema de Microsoft Office agora pode ser acessada usando a faixa de faixas.

 Para obter mais informações, consulte [visão geral da faixa](../vsto/ribbon-overview.md)de visualização.

## <a name="backstage-view"></a><a name="Backstage"></a> Modo de exibição de Backstage
 Em aplicativos do Office, clicar na guia **arquivo** abre o modo de exibição Backstage. O modo de exibição de Backstage fornece uma interface do usuário que combina tarefas e ações em nível de arquivo e substitui a funcionalidade semelhante disponível no botão de Microsoft Office no sistema de Microsoft Office de 2007. O modo de exibição de Backstage é totalmente extensível usando XML.

 O Visual Studio não fornece um designer ou APIs para personalizar o modo de exibição de Backstage. No entanto, se você adicionar um item de faixa de visualização **(XML)** ao seu projeto do Office, poderá adicionar XML ao arquivo XML da faixa de faixas para personalizar o modo de exibição de Backstage. Para obter mais informações sobre itens de **faixa de faixas (XML)** , consulte [Ribbon XML](../vsto/ribbon-xml.md).

 Para obter mais informações sobre como personalizar o modo de exibição de Backstage, consulte [introdução ao modo de exibição de Backstage do office 2010 para desenvolvedores](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) e [Personalizar o modo de exibição do Backstage do Office 2010 para desenvolvedores](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

## <a name="outlook-form-regions"></a><a name="FormRegion"></a> Regiões de formulário do Outlook
 Use regiões de formulário para adicionar funcionalidade personalizada a formulários padrão do Microsoft Office Outlook. Você pode criar regiões de formulário que estendam qualquer formulário existente com campos ou controles adicionais. Se você criar uma nova região de formulário usando as ferramentas de desenvolvimento do Office no Visual Studio, poderá usar somente Windows Forms controles na região do formulário. Se você importar uma região de formulário que foi criada no Outlook, poderá usar apenas controles nativos do Outlook.

 Você pode criar regiões de formulário que ocupem áreas diferentes da interface do usuário do Outlook. Por exemplo, as regiões de formulário adjacentes são exibidas na parte inferior da primeira página de um formulário, e cada região de formulário adjacente é recolhível. Você também pode adicionar uma região de formulário separada que é exibida como uma página de formulário adicional completa e que pode aparecer em qualquer formulário padrão ou personalizado existente.

 Para obter mais informações, consulte [criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="controls-on-documents"></a><a name="Controls"></a> Controles em documentos
 Você pode adicionar uma variedade de controles a documentos do Word e planilhas do Excel. Por exemplo, talvez você queira adicionar um controle de seletor de data a um documento para que o usuário possa inserir datas em um formato padrão ou colocar um botão em uma planilha para enviar dados a um banco de dado.

 Ao desenvolver projetos de nível de documento para Excel ou Word, você pode usar o designer do Visual Studio para adicionar controles ao documento ou pasta de trabalho em seu projeto em tempo de design ou pode adicionar controles programaticamente em tempo de execução. Ao desenvolver projetos de suplemento do VSTO para Excel ou Word, você pode adicionar controles programaticamente a qualquer documento ou pasta de trabalho aberta em tempo de execução.

 Para obter mais informações, consulte Visão geral de [itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md) e [controles do Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="shortcut-menus"></a><a name="Shortcut"></a> Menus de atalho
 Um menu de atalho é exibido quando você clica com o botão direito do mouse em um documento ou em uma janela de aplicativo. Você pode definir um menu de atalho para aparecer depois que um evento ocorrer, como quando um usuário clica com o botão direito do mouse em um documento, pasta de trabalho ou controle de host. Você pode adicionar vários comandos de menu ou controles diferentes a um menu de atalho. Crie menus de atalho usando XML. Se você adicionar um item **da faixa (XML)** ao seu projeto do Office, você poderá adicionar XML ao arquivo XML da faixa de para criar menus de atalho. Para obter mais informações sobre como usar o XML para criar menus de atalho, consulte [como adicionar comandos a menus de atalho](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="see-also"></a>Veja também
- [Visão geral da faixa de faixas](../vsto/ribbon-overview.md)
- [Visão geral dos controles do Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Visão geral do painel Ações](../vsto/actions-pane-overview.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Painéis de tarefas personalizados](../vsto/custom-task-panes.md)
- [Usar controles WPF em soluções do Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Como: mostrar a guia Desenvolvedor na faixa de das](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [Como mostrar erros de interface do usuário do suplemento](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Walkthrough: coletar dados usando um formulário do Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
