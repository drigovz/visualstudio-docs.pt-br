---
title: Tarefas comuns na programação do Office
description: Saiba como você pode programar em relação aos dados em uma personalização em nível de documento sem precisar usar o modelo de objeto do Microsoft Office Word ou Office Excel.
ms.custom: SEO-VS-2020SS
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 67b09d3881dcde1d404b7ff0c1096ced1ecb50ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910601"
---
# <a name="common-tasks-in-office-programming"></a>Tarefas comuns na programação do Office
  Este tópico foi criado para ajudá-lo a encontrar as respostas para as seguintes categorias de perguntas comuns sobre a programação de soluções do Office usando o Visual Studio.

- [Instalação e tarefas gerais](#projects).

- [Tarefas de personalização da interface do usuário](#ui).

- [Tarefas de automação do Excel](#excel).

- [Tarefas de automação do Word](#word).

- [Tarefas de dados](#data).

- [Tarefas de gerenciamento de documentos no servidor](#server).

- [Tarefas de segurança](#security).

- [Tarefas de implantação](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Instalação e tarefas gerais

- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Como: atualizar soluções do Office](/previous-versions/4bez6837(v=vs.140)).

- [Como instalar assemblies de interoperabilidade primária do Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

- [Como: direcionar aplicativos do Office por meio de assemblies de interoperabilidade primária](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

- [Como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Como: abrir soluções do Office sem executar código](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Como configurar informações de configuração para uma solução do Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Como mostrar a guia Desenvolvedor na faixa de faixas](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Como mostrar erros de interface do usuário do suplemento](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Tarefas de personalização da interface do usuário

### <a name="controls-on-documents-and-worksheets"></a>Controles em documentos e planilhas

- [Como: adicionar controles de Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Como adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [Como: adicionar controles de Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Como: adicionar controles de conteúdo a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md).

- [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

### <a name="task-panes-in-document-level-customizations"></a>Painéis de tarefas em personalizações em nível de documento

- [Como: adicionar um painel ações a documentos do Word ou a pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>Painéis de tarefas em suplementos do VSTO

- [Como: adicionar um painel de tarefas personalizado a um aplicativo](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Personalizações da faixa de das

- [Como: começar a personalizar a faixa de faixas](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Como alterar a posição de uma guia na faixa de faixas](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Como: personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md).

- [Como: adicionar controles ao modo de exibição de Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Como exportar uma faixa de faixas do designer de faixa de das faixas para XML da faixa de modo](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Regiões de formulário do Outlook

- [Como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Como: impedir que o Outlook exiba uma região de formulário](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Menus personalizados

- [Como: adicionar comandos a menus de atalho](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a> Tarefas de automação do Excel

- [Como exibir programaticamente uma cadeia de caracteres em uma célula de planilha](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).

- [Como criar programaticamente novas pastas de trabalho](../vsto/how-to-programmatically-create-new-workbooks.md).

- [Como: pastas de trabalho abertas programaticamente](../vsto/how-to-programmatically-open-workbooks.md).

- [Como: salvar pastas de trabalho programaticamente](../vsto/how-to-programmatically-save-workbooks.md).

- [Como: fechar pastas de trabalho programaticamente](../vsto/how-to-programmatically-close-workbooks.md).

- [Como: adicionar programaticamente novas planilhas a pastas de trabalho](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

- [Como: ocultar planilhas programaticamente](../vsto/how-to-programmatically-hide-worksheets.md).

- [Como: mover planilhas programaticamente dentro de pastas de trabalho](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).

- [Como: proteger pastas de trabalho programaticamente](../vsto/how-to-programmatically-protect-workbooks.md).

- [Como programaticamente fazer referência a intervalos de planilha no código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).

- [Como: aplicar estilos programaticamente a intervalos em pastas de trabalho](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).

- [Como alterar de forma programática a formatação nas linhas da planilha que contêm as células selecionadas](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).

- [Como: Pesquisar por programação de texto em intervalos de planilhas](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).

- [Como: imprimir planilhas programaticamente](../vsto/how-to-programmatically-print-worksheets.md).

- [Como executar cálculos do Excel programaticamente](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).

- [Como: classificar dados de forma programática em planilhas](../vsto/how-to-programmatically-sort-data-in-worksheets.md).

## <a name="word-automation-tasks"></a><a name="word"></a> Tarefas de automação do Word

- [Como: criar novos documentos programaticamente](../vsto/how-to-programmatically-create-new-documents.md).

- [Como: abrir documentos existentes programaticamente](../vsto/how-to-programmatically-open-existing-documents.md).

- [Como: salvar documentos programaticamente](../vsto/how-to-programmatically-save-documents.md).

- [Como: fechar documentos programaticamente](../vsto/how-to-programmatically-close-documents.md).

- [Como: inserir texto de forma programática em documentos do Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md).

- [Como: definir e selecionar intervalos por meio de programação em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

- [Como: redefinir intervalos programaticamente em documentos do Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).

- [Como: formatar texto de forma programática em documentos](../vsto/how-to-programmatically-format-text-in-documents.md).

- [Como: adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

- [Como: atualizar o texto do indicador programaticamente](../vsto/how-to-programmatically-update-bookmark-text.md).

- [Como: Pesquisar e substituir texto de forma programática em documentos](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).

- [Como: imprimir documentos programaticamente](../vsto/how-to-programmatically-print-documents.md).

- [Como: criar tabelas do Word programaticamente](../vsto/how-to-programmatically-create-word-tables.md).

- [Como: adicionar linhas e colunas programaticamente a tabelas do Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).

- [Como: contar programaticamente caracteres em documentos](../vsto/how-to-programmatically-count-characters-in-documents.md).

## <a name="data-tasks"></a><a name="data"></a> Tarefas de dados

### <a name="data-bound-controls"></a>Controles vinculados a dados

- [Como: preencher planilhas com dados de um banco de dado](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).

- [Como: popular documentos com dados de um banco de dado](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Como: preencher documentos com dados de serviços](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Como: preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md).

- [Como: popular documentos com dados de um banco de dado](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Como: preencher documentos com dados de serviços](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Como: atualizar uma fonte de dados com dados de um controle de host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Dados armazenados em cache em soluções de nível de documento

- [Como armazenar em cache dados para uso offline ou em um servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Como: armazenar em cache uma fonte de dados programaticamente em um documento do Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Como armazenar dados em cache em um documento protegido por senha](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Dados XML personalizados

- [Como: adicionar partes XML personalizadas a personalizações em nível de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [Como: adicionar partes XML personalizadas a documentos usando suplementos do VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Tarefas de gerenciamento de documentos no servidor

- [Como remover extensões de código gerenciado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Como: anexar extensões de código gerenciado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Tarefas de segurança

- [Como: assinar soluções do Office](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Tarefas de implantação

- [Como publicar uma solução do Office usando o ClickOnce](/previous-versions/bb386095(v=vs.110)).

- [Como publicar uma solução do Office em nível de documento em um servidor do SharePoint usando o ClickOnce](/previous-versions/bb608595(v=vs.110)).

- [Como instalar uma solução do ClickOnce Office](/previous-versions/bb608592(v=vs.110)).

- [Como instalar pré-requisitos em computadores de usuários finais para executar soluções do Office](/previous-versions/bb608608(v=vs.110)).

- [Como preparar o IIS para implantação de soluções do Office](/previous-versions/bb608629(v=vs.110)).

- [Como: atualizar soluções implantadas do Office](/previous-versions/bb157871(v=vs.110)).

- [Como alterar o caminho de instalação de uma solução do Office](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>Confira também
- [Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Recursos disponíveis pelo aplicativo do Office e tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md)
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)