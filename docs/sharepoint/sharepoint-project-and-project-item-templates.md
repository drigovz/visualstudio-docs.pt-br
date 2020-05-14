---
title: Modelos de itens de projeto e projeto do SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649221"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Modelos de itens de projeto e projeto do SharePoint
  As seções a seguir descrevem os modelos de itens de projeto e de projeto disponíveis do SharePoint e como eles são usados.

## <a name="project-and-project-item-templates-overview"></a>Visão geral dos modelos de itens de projeto e projeto
 Quando você cria um novo projeto SharePoint no Visual Studio, um projeto sharePoint é adicionado à solução juntamente com todos os itens de projeto exigidos por esse tipo de projeto. Por exemplo, se você criar um projeto Silverlight Web Part, o Visual Studio criará uma solução que contém um item de projeto Visual Web Part e um item de projeto de aplicativo Silverlight, juntamente com todos os arquivos exigidos por esses itens do projeto. Os modelos de itens do projeto são usados para adicionar itens de projeto a um projeto SharePoint existente, como adicionar um receptor de evento, coluna do site ou lista.

 Para obter informações sobre os fundamentos do SharePoint, consulte [SharePoint Foundation Building Blocks](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Usuários avançados podem criar modelos personalizados de itens de projeto e projeto. Para obter mais informações, consulte [Estender o sistema de projeto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Modelos de projeto
 A seguir está uma lista de modelos de projeto do SharePoint. Para visualizar os modelos de projeto do SharePoint no Visual Studio, na caixa de diálogo **Novo Projeto,** expanda o nó **SharePoint** em **visual C#** ou **Visual Basic**e escolha **2010**.

### <a name="sharepoint-2010-project"></a>Projeto SharePoint 2010
 O conteúdo de um *Projeto SharePoint 2010* está incluído em todos os modelos de projeto do SharePoint. Um projeto SharePoint 2010 contém:

- Um arquivo de projeto.

- Uma página de propriedades do projeto.

- Uma pasta **de referências** listando todas as referências de montagem no projeto.

- Uma pasta **Recursos** que contém um arquivo de configuração *.feature,* usado para implantar recursos no servidor SharePoint.

- Uma pasta **Pacote** que contém um arquivo *Package.package,* usado para implantar a solução no SharePoint.

- Um arquivo key.snk (chave de nome forte) que é usado para assinar o conjunto com um nome forte, para maior segurança.

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight web parte
 Os projetos *do SharePoint 2010 Silverlight Web Part* permitem criar peças web para o SharePoint que exibem aplicativos Silverlight. Ao criar este projeto, você pode especificar se deve adicionar um novo aplicativo Silverlight a ele ou fazer referência a um já existente. Para obter mais informações, consulte [Criar peças da Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e Passo a [Passo: Crie uma parte da web silverlight que exibe OData for SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 visual web parte
 Um projeto *SharePoint 2010 Visual Web Part* inclui um arquivo de definição *Elements.xml,* um item **da Web Part** e um item de controle de **usuário.** Você pode projetar a aparência da parte visual da web arrastando ou copiando controles da Caixa de Ferramentas do Visual Studio para a superfície do controle do usuário. Para obter mais informações, consulte [Como: Criar uma parte web do SharePoint usando um designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [bloco de construção: peças da Web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Pacote de solução Import SharePoint 2010
 Os projetos *do Pacote de Soluções Do SharePoint 2010* permitem importar todo ou parte de um site existente do SharePoint 2010, exportado para um arquivo de solução SharePoint *(.wsp),* para o Visual Studio. Uma vez importado para o Visual Studio, você pode personalizar seus itens e reimplantá-los. Para obter mais informações, consulte [Importar itens de um site do SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importar fluxo de trabalho SharePoint 2010 reutilizável
 *Import e laborable SharePoint 2010 Os* projetos de fluxo de trabalho permitem importar um fluxo de trabalho reutilizável e declarativo criado no SharePoint Designer 2010 para o Visual Studio. O fluxo de trabalho é exportado do site do SharePoint como um arquivo *.wsp.* Uma vez importado para o Visual Studio, você pode personalizá-lo, adicionar código a ele e, em seguida, implantá-lo em um site do SharePoint. Para obter mais informações, consulte [Passo a Passo: Importe um fluxo de trabalho reutilizável do SharePoint Designer para o Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Modelos de itens de projeto
 A seguir está uma lista de modelos de itens de projeto do SharePoint. Os modelos de itens do projeto adicionam arquivos à solução SharePoint para suportar a funcionalidade do SharePoint, como colunas de sites, listas e tipos de conteúdo. Por exemplo, adicionar uma coluna de site à sua solução adiciona um projeto de coluna do site que contém um arquivo de definição *Elements.xml.* Adicionar uma parte visual da web adiciona um projeto de parte visual da web à sua solução que contém um arquivo *Elements.xml,* um item de controle do usuário e um item de parte visual da web.

 Para visualizar os modelos de itens do projeto SharePoint, no **Solution Explorer,** abra o menu de atalho para um projeto SharePoint e escolha **Adicionar**, **Novo Item**. Expanda o nó **SharePoint** em **visual C#** ou **Visual Basic**e escolha **2010**.

### <a name="application-page-farm-solution-only"></a>Página de aplicação (somente solução agrícola)
 Um item **da Página de Aplicativo (Somente Solução de Fazenda)** permite que você desenhe uma [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] página da Web para um site do SharePoint. Páginas de aplicativos só podem ser usadas em soluções agrícolas. Você pode adicionar este item do projeto apenas às soluções agrícolas. Para obter mais informações, consulte [Como: Criar uma página de aplicativo](../sharepoint/how-to-create-an-application-page.md) e aplicativo _layouts Tipo de [Página](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modelo de conectividade de dados de negócios (somente solução agrícola)
 Um item **do Business Data Connectivity Model (Somente farm Solution)** permite integrar dados de negócios ao SharePoint. Os dados de negócios podem vir de [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]aplicativos de servidor back-end, como o Siebel e o Service Advertising Protocol (SAP). Os modelos de conectividade de dados de negócios só podem ser usados em soluções agrícolas. Você pode adicionar este item do projeto apenas às soluções agrícolas. Para obter mais informações, consulte [Como: Criar um modelo BDC](../sharepoint/how-to-create-a-bdc-model.md), [Como: Usar um arquivo de recursos para especificar nomes, propriedades e permissões localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)e [o que há de novo: Serviços de conectividade de negócios](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Tipo de conteúdo
 *Os* itens do Tipo de conteúdo permitem criar tipos de conteúdo personalizados com base em um tipo de conteúdo (base) existente, como um documento, um anúncio ou uma tarefa. Um tipo de conteúdo personalizado fornece os mesmos atributos e campos que o tipo de conteúdo base juntamente com quaisquer colunas (campos) do site definidas. Por exemplo, você pode criar um tipo de conteúdo de contato personalizado que é baseado no tipo de conteúdo de contato base que vem no SharePoint. Você pode personalizar o tipo de conteúdo alterando as colunas de site existentes ou adicionando mais colunas de site às já incluídas no tipo de conteúdo base.

> [!NOTE]
> Devido a uma limitação do SharePoint, você não pode criar um tipo de conteúdo de solução agrícola com base em um tipo de conteúdo de solução sandboxed.

 Para obter mais informações, consulte [Passo a passo: Crie uma coluna de site, tipo de conteúdo e liste para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [Building Block: Tipo de conteúdo](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Elemento vazio
 *Elementos vazios* são mais usados para definir itens de projeto do SharePoint que não possuem um modelo de projeto ou item de projeto no Visual Studio. Quando você adiciona um elemento vazio ao seu projeto, um nó chamado EmptyElement[x](onde [x] é criado um número\) único. EmptyElement[x] contém um único arquivo chamado *Elements.xml.* Use [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] as instruções para definir os elementos desejados em *Elements.xml*.

### <a name="event-receiver"></a>Receptor de eventos
 *Os receptores de eventos* lidam com eventos para itens no site do SharePoint, como quando um item é adicionado a uma lista, quando um item da Web é excluído ou quando um fluxo de trabalho é iniciado. O modelo de item do projeto do receptor de eventos permite que você manuseie

- Lista os eventos

- Listar eventos de itens

- Listar eventos de e-mail

- Eventos web

- Listar eventos de fluxo de trabalho

  O item do projeto receptor de eventos cria uma pasta **Receptora de Eventos** com um arquivo de classe única que contém manipuladores de eventos para todos os eventos especificados quando você criou o projeto no **Assistente de Personalização do SharePoint**. A classe receptora de eventos pode lidar com eventos que ocorrem no site do SharePoint quando itens como arquivos, campos, itens, listas, anexos, peças da Web e fluxos de trabalho são adicionados, atualizados, excluídos ou removidos. Para obter mais informações, consulte [Como criar um receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md) e Building [Block: Event Handling](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>Lista
 Uma lista é uma instância de uma definição de lista de base reutilizável do SharePoint, como um calendário ou uma lista de tarefas. Depois de adicionar uma lista à sua solução, o List Designer permite adicionar colunas de site à lista e criar colunas de lista personalizadas. Isso inclui colunas de sites de tipos de conteúdo. Você pode especificar a *exibição* da lista, que determina as colunas que aparecerão na lista. Para obter mais informações, consulte [Passo a Passo: Crie uma coluna de site, tipo de conteúdo e liste para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [Building Block: Lists and Document Libraryes](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Módulo
 *Os módulos* (para [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] não ser confundidos com módulos) contêm quaisquer arquivos que você deseja implantar no servidor SharePoint, como imagens ou notas. O item do projeto do módulo contém um nó **de módulo.** O nó do módulo contém dois modelos de itens do projeto: um arquivo de definição XML, que funciona como um manifesto para o módulo, e um arquivo *sample.txt,* um arquivo de espaço reservado. Para obter mais informações, consulte [Usar módulos para incluir arquivos na solução](../sharepoint/using-modules-to-include-files-in-the-solution.md) e [módulos](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Fluxo de trabalho seqüencial (somente solução agrícola)
 Um *fluxo de trabalho sequencial* é uma série de etapas lógicas de negócios, realizadas em sequência, até que a última etapa seja concluída. Fluxos de trabalho seqüenciais são usados para gerenciar processos que envolvem itens do SharePoint, como listas e documentos. Você pode criar fluxos de trabalho em nível de site (global) ou fluxos de trabalho de nível de lista (local) e pode selecionar se um fluxo de trabalho é iniciado automaticamente ou manualmente. Este item do projeto só pode ser usado em soluções agrícolas. Você pode adicionar este item do projeto apenas às soluções agrícolas. Para obter mais informações, consulte [Criar soluções de fluxo de trabalho do SharePoint,](../sharepoint/creating-sharepoint-workflow-solutions.md) [fluxos de trabalho no SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e [O que há de novo: melhorias no fluxo de trabalho](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Parte da teia de Silverlight
 Os itens do projeto *de parte da web silverlight* permitem criar peças web para o SharePoint que exibem aplicativos Silverlight. Quando você adiciona este item do projeto à sua solução, você pode escolher se deve adicionar um novo aplicativo Silverlight ou referenciar um existente mais tarde. Para obter mais informações, consulte [Criar peças da Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e Passo a [Passo: Crie uma parte da web silverlight que exibe OData for SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Coluna do site
 Uma *coluna de site*, também conhecida como *campo*, é um dos elementos mais básicos que você pode adicionar a um projeto SharePoint. Uma coluna do site representa um tipo de dados, como um número de telefone, um comentário de texto ou o nome da cidade de um contato em uma lista de contatos. Para obter mais informações, consulte [Criar colunas de site, tipos de conteúdo e listas para SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) e [Colunas](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definição do local (somente solução agrícola)
 *Os* itens do projeto de definição do site contêm uma pasta de definição de site que inclui os seguintes arquivos:

- Uma página padrão .aspx, usada como página web padrão para o site.

- Um arquivo *onet.xml* que define os componentes do site.

- Um arquivo webtemp xml que especifica as configurações de definição de site que aparecem na seção **Seleção** de modelos da página **Novo Site do SharePoint.**

  Depois de adicionar uma definição de site, você adiciona código e arquivos para introduzir a funcionalidade. Este item do projeto só pode ser usado em soluções agrícolas. Você pode adicionar este item do projeto apenas às soluções agrícolas. Para obter mais informações, consulte [Criar definições de site para Definições](../sharepoint/creating-site-definitions-for-sharepoint.md) [e Configurações do Site e do Site](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Fluxo de trabalho da máquina estatal (somente solução agrícola)
 Um *fluxo de trabalho de máquinas estatais* é um conjunto de estados, transições e ações lógicas de negócios. As etapas em um fluxo de trabalho de máquina de estado não são executadas em seqüência; em vez disso, são desencadeadas por ações e estados. Como um fluxo de trabalho seqüencial, os fluxos de trabalho das máquinas estaduais estão associados a itens do SharePoint, como listas e documentos. Mais uma vez, você pode criar fluxos de trabalho em nível de local (global) ou fluxos de trabalho de nível de lista (local). Você também pode selecionar se um fluxo de trabalho é iniciado automaticamente ou manualmente. Este item do projeto só pode ser usado em soluções agrícolas. Você pode adicionar este item do projeto apenas às soluções agrícolas. Para obter mais informações, consulte [Criar soluções de fluxo de trabalho do SharePoint,](../sharepoint/creating-sharepoint-workflow-solutions.md) [fluxos de trabalho no SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))e [O que há de novo: melhorias no fluxo de trabalho](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Controle do usuário (somente solução agrícola)
 Um *controle de usuário* é um controle personalizado e reutilizável ao qual você pode adicionar outros controles de ASP.NET e controles SharePoint. O controle do usuário pode ser adicionado às páginas do aplicativo e às partes da Web que são executadas no SharePoint. Este item do projeto só pode ser usado em soluções agrícolas. Você pode adicionar este item do projeto apenas às soluções agrícolas. Para obter mais informações, consulte [Criando controles reutilizáveis para peças da Web ou páginas de aplicativos.](creating-reusable-controls-for-web-parts-or-application-pages.md)

### <a name="visual-web-part"></a>Parte visual da web
 Um item de projeto *de parte visual da Web* inclui um arquivo de definição *Elements.xml,* um item **da Web Part** e um item de controle de **usuário.** Você pode projetar a aparência da parte visual da web arrastando ou copiando controles da Caixa de Ferramentas do Visual Studio para a superfície do controle do usuário. Para obter mais informações, consulte [Como: Criar uma parte web do SharePoint usando um designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [bloco de construção: peças da Web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Web Part
 Uma *parte da Web* é um controle do lado do servidor que é executado dentro de um tipo especial de página chamada Página de Parte da Web. Eles são os blocos de construção de páginas que aparecem em um site do SharePoint. O item de parte da Web fornece arquivos que permitem projetar uma parte da Web para um site do SharePoint. Para obter mais informações, consulte [Como: Criar uma parte web do SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) e [building block: Web Parts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Confira também
- [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Produtos e Tecnologias SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
