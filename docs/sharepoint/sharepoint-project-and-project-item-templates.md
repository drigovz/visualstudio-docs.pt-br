---
title: Modelos de projeto e item de projeto do SharePoint | Microsoft Docs
description: Examine as descrições do projeto do SharePoint e dos modelos de item do projeto disponíveis e como eles são usados.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8482a6185f670ce1bb340ff40fe277b751a39c06
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892327"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Modelos de projeto e item de projeto do SharePoint
  As seções a seguir descrevem o projeto do SharePoint e os modelos de item de projeto disponíveis e como eles são usados.

## <a name="project-and-project-item-templates-overview"></a>Visão geral de modelos de item de projeto e projeto
 Quando você cria um novo projeto do SharePoint no Visual Studio, um projeto do SharePoint é adicionado à solução junto com todos os itens de projeto exigidos por esse tipo de projeto. Por exemplo, se você criar um projeto de Web Part do Silverlight, o Visual Studio criará uma solução que contém um item de projeto de Web Part Visual e um item de projeto de aplicativo do Silverlight junto com todos os arquivos exigidos por esses itens de projeto. Os modelos de item de projeto são usados para adicionar itens de projeto a um projeto existente do SharePoint, como adicionar um receptor de eventos, uma coluna de site ou uma lista.

 Para obter informações sobre os conceitos básicos do SharePoint, consulte [blocos de construção do SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Os usuários avançados podem criar modelos de item de projeto e projeto personalizados. Para obter mais informações, consulte [estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Modelos de projeto
 A seguir está uma lista de modelos de projeto do SharePoint. Para exibir os modelos de projeto do SharePoint no Visual Studio, na caixa de diálogo **novo projeto** , expanda o nó **do SharePoint** em **Visual C#** ou **Visual Basic** e, em seguida, escolha **2010**.

### <a name="sharepoint-2010-project"></a>Projeto do SharePoint 2010
 O conteúdo de um *projeto do sharepoint 2010* é incluído em cada modelo de projeto do SharePoint. Um projeto do SharePoint 2010 contém:

- Um arquivo de projeto.

- Uma página de propriedades do projeto.

- Uma pasta **References** que lista todas as referências de assembly no projeto.

- Uma pasta de **recursos** que contém um arquivo de configuração *. Feature* , usado para implantar recursos no SharePoint Server.

- Uma pasta de **pacote** que contém um arquivo *Package. Package* , usado para implantar a solução no SharePoint.

- Um arquivo Key. SNK (chave de nome forte) que é usado para assinar o assembly com um nome forte, para aumentar a segurança.

### <a name="sharepoint-2010-silverlight-web-part"></a>Web Part do Silverlight do SharePoint 2010
 Os projetos de *Web Part do Silverlight para sharepoint 2010* permitem criar Web Parts para o SharePoint que exibem aplicativos do Silverlight. Ao criar esse projeto, você pode especificar se deseja adicionar um novo aplicativo do Silverlight a ele ou fazer referência a um existente. Para obter mais informações, consulte [Create Web Parts for SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) and [Walkthrough: criar uma Web Part do Silverlight que exibe o OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Web Part Visual do SharePoint 2010
 Um projeto de *Web Part Visual do SharePoint 2010* inclui um arquivo de definição de *Elements.xml* , um item de **Web Part** e um item de **controle de usuário** . Você pode criar a aparência da Web Part Visual arrastando ou copiando controles da caixa de ferramentas do Visual Studio para a superfície do controle de usuário. Para obter mais informações, consulte [como: criar uma Web Part do SharePoint usando um designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [bloco de construção: Web Parts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Importar pacote de solução do SharePoint 2010
 *Importar projetos de pacote de solução do sharepoint 2010* permite importar todo ou parte de um site existente do SharePoint 2010, exportado para um arquivo de solução do SharePoint (*. wsp*) no Visual Studio. Depois de importado para o Visual Studio, você pode personalizar seus itens e reimplantá-los. Para obter mais informações, consulte [importar itens de um site existente do SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importar fluxo de trabalho reutilizável do SharePoint 2010
 *Importar projetos de fluxo de trabalho reutilizáveis do SharePoint 2010* permite importar um fluxo de trabalho reutilizável e declarativo criado no SharePoint Designer 2010 para o Visual Studio. O fluxo de trabalho é exportado do site do SharePoint como um arquivo *. wsp* . Depois de importado para o Visual Studio, você pode personalizá-lo, adicionar código a ele e, em seguida, implantá-lo em um site do SharePoint. Para obter mais informações, consulte [Walkthrough: importar um fluxo de trabalho reutilizável do SharePoint Designer para o Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Modelos de item de projeto
 A seguir está uma lista de modelos de item de projeto do SharePoint. Os modelos de item de projeto adicionam arquivos à solução do SharePoint para dar suporte à funcionalidade do SharePoint, como colunas de site, listas e tipos de conteúdo. Por exemplo, a adição de uma coluna de site à sua solução adiciona um projeto de coluna de site que contém um arquivo de definição de *Elements.xml* . A adição de uma Web Part Visual adiciona um projeto de Web Part Visual à sua solução que contém um arquivo de *Elements.xml* , um item de controle de usuário e um item de Web Part Visual.

 Para exibir os modelos de item de projeto do SharePoint, em **Gerenciador de soluções**, abra o menu de atalho para um projeto do SharePoint e escolha **Adicionar**, **novo item**. Expanda o nó **do SharePoint** sob o **Visual C#** ou **Visual Basic** e escolha **2010**.

### <a name="application-page-farm-solution-only"></a>Página de aplicativo (somente solução de farm)
 Um item de **página de aplicativo (somente solução de farm)** permite que você projete uma [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] página da Web para um site do SharePoint. As páginas de aplicativos podem ser usadas somente em soluções de farm. Você pode adicionar este item de projeto somente a soluções de farm. Para obter mais informações, consulte [como: criar uma página de aplicativo](../sharepoint/how-to-create-an-application-page.md) e o [tipo de página de _layouts de aplicativo](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modelo de conectividade de dados corporativos (somente solução de farm)
 Um item de **modelo de conectividade de dados corporativos (somente solução de farm)** permite integrar dados corporativos ao SharePoint. Os dados de negócios podem vir de aplicativos de servidor back-end, como o [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] Siebel e o SAP (Service Advertising Protocol). Modelos de conectividade de dados corporativos podem ser usados somente em soluções de farm. Você pode adicionar este item de projeto somente a soluções de farm. Para obter mais informações, consulte [como criar um modelo de BDC](../sharepoint/how-to-create-a-bdc-model.md), [como usar um arquivo de recurso para especificar nomes, propriedades e permissões localizadas](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)e [o que há de novo: serviços](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14))corporativos de conectividade.

### <a name="content-type"></a>Tipo de conteúdo
 Itens de *tipo de conteúdo* permitem criar tipos de conteúdo personalizados com base em um tipo de conteúdo (base) existente, como um documento, um anúncio ou uma tarefa. Um tipo de conteúdo personalizado fornece os mesmos atributos e campos que o tipo de conteúdo base, juntamente com qualquer coluna de site (campos) que você definir. Por exemplo, você pode criar um tipo de conteúdo de contato personalizado com base no tipo de conteúdo de contato base que vem no SharePoint. Você pode personalizar o tipo de conteúdo alterando as colunas de site existentes ou adicionando mais colunas de site àquelas já incluídas no tipo de conteúdo base.

> [!NOTE]
> Devido a uma limitação do SharePoint, você não pode criar um tipo de conteúdo de solução de farm com base em um tipo de conteúdo de solução em área restrita.

 Para obter mais informações, consulte [Walkthrough: criar uma coluna de site, tipo de conteúdo e lista para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [bloco de construção: tipo de conteúdo](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Elemento vazio
 *Elementos vazios* são usados com mais frequência para definir itens de projeto do SharePoint que não têm um projeto ou modelo de item de projeto no Visual Studio. Quando você adiciona um elemento vazio ao seu projeto, um nó chamado EmptyElement [x] (onde [x] é um número exclusivo \) é criado. EmptyElement [x] contém um único arquivo chamado *Elements.xml.* Use [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instruções para definir os elementos desejados no *Elements.xml*.

### <a name="event-receiver"></a>Receptor de eventos
 Os *receptores de eventos* manipulam eventos para itens no site do SharePoint, como quando um item é adicionado a uma lista, quando um item da Web é excluído ou quando um fluxo de trabalho é iniciado. O modelo de item de projeto receptor de eventos permite que você manipule

- Lista os eventos

- Eventos de item de lista

- Listar eventos de email

- Eventos da Web

- Listar eventos de fluxo de trabalho

  O item de projeto receptor de eventos cria uma pasta **receptor de eventos** com um único arquivo de classe que contém manipuladores de eventos para todos os eventos que você especificou quando criou o projeto no **Assistente para personalização do SharePoint**. A classe receptor de evento pode manipular eventos que ocorrem no site do SharePoint quando itens como arquivos, campos, itens, listas, anexos, Web Parts e fluxos de trabalho são adicionados, atualizados, excluídos ou removidos. Para obter mais informações, consulte [como: criar um receptor de eventos e um](../sharepoint/how-to-create-an-event-receiver.md) bloco de [construção: manipulação de eventos](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>List
 Uma lista é uma instância de uma definição de lista do SharePoint de base reutilizável, como um calendário ou uma lista de tarefas. Depois de adicionar uma lista à sua solução, o designer de lista permite que você adicione colunas de site à lista e crie colunas de lista personalizadas. Isso inclui colunas de site de tipos de conteúdo. Você pode especificar a *exibição* da lista, que determina as colunas que serão exibidas na lista. Para obter mais informações, consulte [Walkthrough: criar uma coluna de site, tipo de conteúdo e lista para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [bloco de construção: listas e bibliotecas de documentos](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Módulo
 Os *módulos* (não devem ser confundidos com [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos) contêm todos os arquivos que você deseja implantar no servidor do SharePoint, como imagens ou anotações. O item de projeto de módulo contém um nó de **módulo** . O nó de módulo contém dois modelos de item de projeto: um arquivo de definição XML, que atua como um manifesto para o módulo e um arquivo de *sample.txt* , um arquivo de espaço reservado. Para obter mais informações, consulte [usar módulos para incluir arquivos na solução e nos](../sharepoint/using-modules-to-include-files-in-the-solution.md) [módulos](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Fluxo de trabalho Sequencial (somente solução de farm)
 Um *fluxo de trabalho Sequencial* é uma série de etapas de lógica de negócios, executadas em sequência, até que a última etapa seja concluída. Os fluxos de trabalho seqüenciais são usados para gerenciar processos que envolvem itens do SharePoint, como listas e documentos. Você pode criar fluxos de trabalho (globais) em nível de site ou fluxos de trabalho de nível de lista (local) e pode selecionar se um fluxo de trabalho é iniciado automaticamente ou manualmente. Este item de projeto só pode ser usado em soluções de farm. Você pode adicionar este item de projeto somente a soluções de farm. Para obter mais informações, consulte [criar soluções de fluxo de trabalho do SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [fluxos de trabalho no SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e [o que há de novo: aprimoramentos de fluxo de trabalho](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Web Part do Silverlight
 Os itens de projeto de *Web Part do Silverlight* permitem criar Web Parts para o SharePoint que exibem aplicativos do Silverlight. Ao adicionar esse item de projeto à sua solução, você pode escolher se deseja adicionar um novo aplicativo do Silverlight ou fazer referência a um existente posteriormente. Para obter mais informações, consulte [Create Web Parts for SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) and [Walkthrough: criar uma Web Part do Silverlight que exibe o OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Coluna do site
 Uma *coluna de site*, também conhecida como um *campo*, é um dos elementos mais básicos que você pode adicionar a um projeto do SharePoint. Uma coluna de site representa um tipo de dados, como um número de telefone, um comentário de texto ou o nome da cidade de um contato em uma lista de contatos. Para obter mais informações, consulte [criar colunas de site, tipos de conteúdo e listas para SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) e [colunas](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definição de site (somente solução de farm)
 Os itens de projeto de *definição de site* contêm uma pasta de definição de site que inclui os seguintes arquivos:

- Uma página default. aspx, usada como a página da Web padrão para o site.

- Um arquivo de *onet.xml* que define os componentes do site.

- Um arquivo xml WebTemp que especifica as configurações de definição de site que aparecem na seção **seleção de modelo** da página **novo site do SharePoint** .

  Depois de adicionar uma definição de site, você adiciona código e arquivos para introduzir a funcionalidade. Este item de projeto só pode ser usado em soluções de farm. Você pode adicionar este item de projeto somente a soluções de farm. Para obter mais informações, consulte [criar definições de site para o SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) e [definições de site e configurações](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Fluxo de trabalho da máquina de estado (somente solução de farm)
 Um *fluxo de trabalho de máquina de estado* é um conjunto de Estados, transições e ações de lógica de negócios. As etapas em um fluxo de trabalho de máquina de estado não são executadas em sequência; em vez disso, eles são disparados por ações e Estados. Como um fluxo de trabalho seqüencial, os fluxos de trabalho de máquina de estado são associados a itens do SharePoint, como listas e documentos. Mais uma vez, você pode criar fluxos de trabalho em nível de site (global) ou fluxos de trabalho em nível de lista (local). Você também pode selecionar se um fluxo de trabalho é iniciado automaticamente ou manualmente. Este item de projeto só pode ser usado em soluções de farm. Você pode adicionar este item de projeto somente a soluções de farm. Para obter mais informações, consulte [criar soluções de fluxo de trabalho do SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [fluxos de trabalho no SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e [o que há de novo: aprimoramentos de fluxo de trabalho](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Controle de usuário (somente solução de farm)
 Um *controle de usuário* é um controle personalizado e reutilizável ao qual você pode adicionar outros controles ASP.net e controles do SharePoint. O controle de usuário pode ser adicionado a páginas de aplicativo e Web Parts que são executadas no SharePoint. Este item de projeto só pode ser usado em soluções de farm. Você pode adicionar este item de projeto somente a soluções de farm. Para obter mais informações, consulte [criando controles reutilizáveis para Web Parts ou páginas de aplicativo](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Web Part Visual
 Um item de projeto de *Web Part Visual* inclui um arquivo de definição de *Elements.xml* , um item de **Web Part** e um item de **controle de usuário** . Você pode criar a aparência da Web Part Visual arrastando ou copiando controles da caixa de ferramentas do Visual Studio para a superfície do controle de usuário. Para obter mais informações, consulte [como: criar uma Web Part do SharePoint usando um designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [bloco de construção: Web Parts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Web Part
 Uma *Web Part* é um controle do lado do servidor executado dentro de um tipo especial de página chamado página de Web Parts. Eles são os blocos de construção de páginas que aparecem em um site do SharePoint. O item de Web Part fornece arquivos que permitem que você projete uma Web Part para um site do SharePoint. Para obter mais informações, consulte [como: criar uma Web Part do SharePoint e um](../sharepoint/how-to-create-a-sharepoint-web-part.md) [bloco de construção: Web Parts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Confira também
- [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Produtos e Tecnologias SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
