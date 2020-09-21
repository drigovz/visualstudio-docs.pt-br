---
title: Recursos disponíveis pelo aplicativo do Office e tipo de projeto
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24344a643e9ec2b4a7bb90dc62df67209b3eb183
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808175"
---
# <a name="features-available-by-office-application-and-project-type"></a>Recursos disponíveis pelo aplicativo do Office e tipo de projeto
  O Visual Studio tem vários tipos de modelos de projeto que dão suporte a diferentes cenários de negócios para Microsoft Office aplicativos, incluindo os seguintes tipos:

- Personalizações em nível de documento.

- Suplementos do VSTO.

  Nem todos os aplicativos podem usar cada tipo de projeto. Por exemplo, projetos de nível de documento estão disponíveis apenas para Microsoft Office Word e Microsoft Office Excel. Da mesma forma, alguns recursos estão disponíveis apenas para determinados tipos de projetos ou aplicativos. Por exemplo, o painel Ações está disponível apenas em projetos de nível de documento e as extensões de faixa de faixas estão disponíveis apenas para alguns aplicativos. Para obter mais informações sobre os diferentes tipos de projeto, consulte [visão geral do desenvolvimento de soluções do Office &#40;&#41;do VSTO ](../vsto/office-solutions-development-overview-vsto.md).

> [!NOTE]
> Os modelos de projeto do Office estão disponíveis apenas em algumas edições do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Para obter mais informações, consulte [configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Tipos de projeto disponíveis para diferentes aplicativos de Microsoft Office
 A tabela a seguir mostra os aplicativos que você pode usar com cada tipo de projeto.

|Tipos de projeto|Microsoft Office aplicativo|
|-------------------|----------------------------------|
|Personalizações no nível de documento|Excel<br /><br /> Word|
|Suplementos do VSTO|Excel<br /><br /> InfoPath (somente InfoPath 2013 e InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>Recursos disponíveis em diferentes tipos de projeto
 A tabela a seguir mostra quais tipos de projeto fornecem cada recurso.

|Recurso|Tipos de projeto que fornecem o recurso|Leitura adicional|
|-------------|--------------------------------------------|---------------------|
|Painel Ações.|Projetos de nível de documento.|[Visão geral do painel Ações](../vsto/actions-pane-overview.md)|
|Implantação do ClickOnce.|Projetos VS e de nível de documento.|[Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)|
|Painéis de tarefas personalizados.|Projetos de suplemento do VSTO para os seguintes aplicativos:<br /><br /> -Excel<br />-InfoPath (somente InfoPath 2013 e InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Palavra|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md)|
|Partes XML personalizadas.|Projetos de nível de documento.<br /><br /> Projetos de nível de aplicativo para os seguintes aplicativos:<br /><br /> -Excel<br />-PowerPoint<br />-Palavra|[Visão geral das partes XML personalizadas](../vsto/custom-xml-parts-overview.md)|
|Cache de dados.|Projetos de nível de documento.|[Dados armazenados em cache em personalizações em nível de documento](../vsto/cached-data-in-document-level-customizations.md)|
|Expor um objeto em um suplemento do VSTO para outras soluções de Microsoft Office.|Projetos de suplemento do VSTO.|[Chamar código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Os seguintes controles de host:<br /><br /> -Gráfico<br />-ListObject<br />-NamedRange<br />-Controles de conteúdo<br />-Indicador|Projetos de nível de documento.<br /><br /> Projetos de suplemento do VSTO para Word e Excel.|[Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)|
|Os seguintes controles de host:<br /><br /> - XMLMappedRange<br />-XMLNode<br />-XMLNodes|Projetos de nível de documento.|[Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)|
|Implantação de vários projetos.|Projetos de nível de documento.<br /><br /> Projetos de suplemento do VSTO.|[Walkthrough: implantar várias soluções do Office em um único instalador do ClickOnce](/previous-versions/dd465290(v=vs.110))|
|Regiões de formulário do Outlook.|Projetos de suplemento do VSTO para Outlook.|[Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)|
|Ações pós-implantação.|Projetos de nível de documento.<br /><br /> Projetos de suplemento do VSTO.|[Walkthrough: copiar um documento para o computador do usuário final após uma instalação do ClickOnce](/previous-versions/dd465291(v=vs.110))|
|Personalizações da faixa de das.|Projetos de nível de documento.<br /><br /> Projetos de suplemento do VSTO para os seguintes aplicativos:<br /><br /> -Excel<br />-InfoPath (somente InfoPath 2013 e InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Projeto<br />-Visio<br />-Palavra|[Visão geral da faixa de faixas](../vsto/ribbon-overview.md)|
|Designer de documento Visual.|Projetos de nível de documento.|[Projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Confira também
- [Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Visão geral do desenvolvimento de soluções do Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md)
- [Visão geral do painel Ações](../vsto/actions-pane-overview.md)
- [Visão geral da faixa de faixas](../vsto/ribbon-overview.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Dados armazenados em cache em personalizações em nível de documento](../vsto/cached-data-in-document-level-customizations.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)