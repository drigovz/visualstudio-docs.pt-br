---
title: Modelos de item/modelos de projeto para itens de projeto do SharePoint
description: Criar modelos de item e modelos de projeto para itens de projeto do SharePoint. Criar assistentes para modelos de item e modelos de projeto.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 59710eb4651f363d669dc27b6190f8d224d9917f
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850631"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Criar modelos de item e modelos de projeto para itens de projeto do SharePoint

Ao definir um tipo de item de projeto personalizado do SharePoint, você pode associá-lo a um modelo de item ou a um modelo de projeto. Essa associação permite que outros desenvolvedores usem o item de projeto no Visual Studio. Você também pode criar um assistente para o modelo.

Por exemplo, o Visual Studio não inclui um modelo de projeto ou modelo de item para adicionar um campo a um site do SharePoint. Você pode definir um tipo de item de projeto do SharePoint que representa um campo e, em seguida, construir um modelo de item que outros desenvolvedores podem usar para adicionar o item de campo a um projeto do SharePoint. Ou, você pode construir um modelo de projeto para que os desenvolvedores possam criar um novo projeto do SharePoint que tenha o item de campo. Em ambos os casos, você também pode fornecer um assistente que aparece quando os desenvolvedores usam seu modelo. Este assistente pode coletar informações de desenvolvedores para configurar o novo item ou projeto.

Modelos de item e modelos de projeto são arquivos *. zip* que contêm arquivos que são usados pelo Visual Studio para criar um projeto ou item de projeto. Para obter mais informações sobre os conceitos básicos dos modelos de item e modelos de projeto, consulte [criar modelos de projeto e item](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Criar modelos de item
 Quando você cria um modelo de item para um item de projeto do SharePoint, há alguns arquivos que são sempre necessários e arquivos opcionais que podem ser usados por determinados tipos de itens de projeto. Para obter instruções que demonstram como definir um tipo de item de projeto do SharePoint e criar um modelo de item para ele, consulte [Walkthrough: Criar item de projeto de ação personalizada com um modelo de item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 A tabela a seguir lista os arquivos necessários para criar um modelo de item para um item de projeto do SharePoint.

|Arquivo necessário|Descrição|
|-------------------|-----------------|
|Um arquivo *. COMDATA*|Esse arquivo XML especifica o conteúdo e o comportamento padrão do item de projeto. Esse arquivo deve ser incluído no modelo de item. Para obter mais informações sobre o conteúdo de arquivos *. OnData* , consulte [referência de esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Um arquivo *. vstemplate* .|Esse arquivo fornece ao Visual Studio as informações necessárias para exibir o modelo na caixa de diálogo **Adicionar novo item** e criar um item de projeto a partir do modelo. Esse arquivo deve ser incluído no modelo de item. Para obter mais informações, consulte [arquivos de metadados de modelo do Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Um assembly de extensão do Visual Studio que implementa a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface.|Esse assembly define o comportamento de tempo de execução do item de projeto. Esse assembly deve ser incluído no pacote VSIX com o modelo de item. Para obter mais informações, consulte [definir tipos personalizados de item de projeto do SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md) e [implantar extensões para as ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 A tabela a seguir lista alguns dos arquivos opcionais mais comuns que podem ser incluídos no modelo de item. Alguns tipos de itens de projeto podem exigir outros arquivos não listados aqui.

| Arquivo opcional | Descrição |
|----------------------| - |
| *Elements.xml* | Um arquivo de *elemento de recurso* . Esse arquivo define a interface do usuário e o comportamento da personalização criada pelo item de projeto. Cada tipo de personalização, como instâncias de lista, tipos de conteúdo ou ações personalizadas, tem um esquema diferente que define o conteúdo desse arquivo. Para obter mais informações, consulte [bloco de construção: recursos](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) e [esquemas](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14))de recursos. |
| *Schema.xml* | O arquivo de esquema para definições de lista. Para obter mais informações, consulte [bloco de construção: listas e bibliotecas de documentos](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) e [Schema.xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)). |
| *. WebPart* | Um arquivo de *definição de Web Part* . Este arquivo contém configurações de propriedade para uma Web Part. Para obter mais informações, consulte [bloco de construção: Web Parts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)). |
| *.ascx* | Um arquivo UserControl do ASP.NET. Esse arquivo define a interface do usuário de uma Web Part Visual. |
| *. aspx* | Um arquivo de paginação ASP.NET. Este arquivo contém marcação XML que define uma página de aplicativo. |
| arquivos *. cs* ou *. vb* | Esses arquivos de código definem o comportamento das personalizações do SharePoint que têm um modelo de programação que pode ser acessado do Visual C# ou Visual Basic código, como páginas de aplicativo, Web Parts e fluxos de trabalho. |

## <a name="create-project-templates"></a>Criar modelos de projeto
 Quando você cria um modelo de projeto do SharePoint, há alguns arquivos que são sempre necessários e arquivos opcionais que podem ser usados por determinados tipos de projetos. Normalmente, os projetos do SharePoint incluem pelo menos um item de projeto do SharePoint. No entanto, isso não é obrigatório. Por exemplo, você pode definir um modelo de projeto do SharePoint que se destina a ser usado apenas para implantar soluções do SharePoint criadas em outros projetos.

 Para obter instruções que demonstram como definir um tipo de item de projeto do SharePoint e criar um modelo de projeto para ele, consulte [Walkthrough: criar um item de projeto de coluna de site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 A tabela a seguir lista os arquivos que devem ser incluídos em um modelo de projeto do SharePoint.

|Arquivo necessário|Descrição|
|-------------------|-----------------|
|Um arquivo *. vstemplate*|Esse arquivo fornece ao Visual Studio as informações necessárias para exibir o modelo na caixa de diálogo **novo projeto** e criar um projeto a partir do modelo. Para obter mais informações, consulte [arquivos de metadados de modelo do Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Um arquivo *. csproj* ou *. vbproj*|Este é o arquivo de projeto. Ele define o conteúdo e as definições de configuração do projeto.|
|*Pacote. Package*|Esse arquivo define o pacote de implantação para o projeto. Quando você usa o designer de pacote para personalizar o pacote de solução para seu projeto, o Visual Studio armazena dados sobre o pacote de solução neste arquivo.<br /><br /> Ao criar um modelo de projeto personalizado do SharePoint, recomendamos que você inclua apenas o conteúdo mínimo necessário no arquivo *Package. Package* e configure o pacote de solução usando as APIs no <xref:Microsoft.VisualStudio.SharePoint.Packages> namespace em uma extensão associada ao modelo de projeto. Se você fizer isso, o modelo de projeto será protegido contra alterações futuras na estrutura do arquivo *Package. Package* . Para obter um exemplo que demonstra como criar um *pacote.* arquivo de pacote com apenas o mínimo de conteúdo necessário, consulte [Walkthrough: criar um item de projeto de coluna de site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se você quiser modificar o arquivo *Package. Package* diretamente, poderá verificar o conteúdo usando o esquema em *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\PackageModelSchema.xsd*.|
|*Package.Template.xml*|Esse arquivo fornece a base para o arquivo de manifesto da solução (*manifest.xml*) para o pacote de solução do SharePoint (*. wsp*) que é gerado a partir do projeto. Você pode adicionar conteúdo a esse arquivo se desejar especificar algum comportamento que não se destina a ser alterado pelos usuários do tipo de projeto. Para obter mais informações, consulte [bloco de construção: soluções](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) e [esquema de solução](/sharepoint/dev/schema/solution-schema).<br /><br /> Quando você cria um pacote de solução do projeto, o Visual Studio mescla o conteúdo do *pacote. Package* e os arquivos de *Package.Template.xml* no arquivo de manifesto da solução. Para obter mais informações sobre como criar pacotes de solução, consulte [como criar um pacote de solução do SharePoint usando tarefas do MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 A tabela a seguir lista os arquivos opcionais que podem ser incluídos no modelo de projeto.

|Arquivo opcional|Descrição|
|-------------------|-----------------|
|itens de projeto do SharePoint|Você pode incluir um ou mais arquivos. COMDATA que definem tipos de item de projeto do SharePoint. Cada arquivo *. COMDATA* deve ter uma <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementação correspondente em um assembly de extensão que está incluído no pacote VSIX com o modelo de projeto. Para obter mais informações, consulte [criar modelos de item](#create-item-templates).<br /><br /> Normalmente, os projetos do SharePoint incluem pelo menos um item de projeto do SharePoint. No entanto, isso não é obrigatório.|
|*\<featureName>. recurso*|Esse arquivo define um recurso do SharePoint que é usado para agrupar vários itens de projeto para implantação. Quando você usa o designer de recursos para personalizar um recurso em seu projeto, o Visual Studio armazena dados sobre o recurso neste arquivo. Se você quiser agrupar os itens do projeto em diferentes recursos, poderá incluir vários arquivos *. Feature* .<br /><br /> Quando você cria um modelo de projeto personalizado do SharePoint, é recomendável incluir apenas o mínimo de conteúdo necessário em cada arquivo *. Feature* e configurar recursos usando as APIs no <xref:Microsoft.VisualStudio.SharePoint.Features> namespace em uma extensão associada ao modelo de projeto. Se você fizer isso, o modelo de projeto será protegido contra alterações futuras na estrutura do arquivo *. Feature* . Para obter um exemplo que demonstra como criar um arquivo *. Feature* com apenas o mínimo de conteúdo necessário, consulte [passo a passos: criar um item de projeto de coluna de site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se você quiser modificar um arquivo *. Feature* diretamente, poderá verificar o conteúdo usando o esquema em *% arquivos de programas (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName>.Template.xml*|Esse arquivo fornece a base para o arquivo de manifesto de recurso (*Feature.xml*) para cada recurso gerado no projeto. Você pode adicionar conteúdo a esse arquivo se desejar especificar algum comportamento que não se destina a ser alterado pelos usuários do tipo de projeto. Para obter mais informações, consulte [bloco de construção: recursos](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) e arquivos de [Feature.xml](/sharepoint/dev/schema/feature-xml-files) .<br /><br /> Quando você cria um pacote de solução do projeto, o Visual Studio mescla o conteúdo de cada par do arquivo *\<featureName> . feature* e *\<featureName>.Template.xml* arquivos em um arquivo de manifesto de recurso. Para obter mais informações sobre como criar pacotes de solução, consulte [como criar um pacote de solução do SharePoint usando tarefas do MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Criar assistentes para modelos de item e modelos de projeto
 Depois de definir um tipo de item de projeto do SharePoint e associá-lo a um item ou modelo de projeto, você também pode criar um assistente. O assistente exibe quando um desenvolvedor usa o modelo de item para adicionar o item de projeto do SharePoint a um projeto ou quando um desenvolvedor usa o modelo de projeto para criar um novo projeto que contém o item de projeto do SharePoint. O assistente pode ser usado para coletar informações de desenvolvedores e para inicializar o novo item de projeto do SharePoint.

 Para obter orientações que demonstram como criar assistentes para modelos de item e modelos de projeto, consulte [passo a passos: criar um item de projeto de ação personalizada com um modelo de item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) e [passo a passos: criar um item de projeto de coluna de site com um modelo de projeto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Confira também

- [Definir tipos de item de projeto personalizados do SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Walkthrough: criar um item de projeto de ação personalizada com um modelo de item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Walkthrough: criar um item de projeto de ação personalizada com um modelo de item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Walkthrough: criar um item de projeto de coluna de site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Walkthrough: criar um item de projeto de coluna de site com um modelo de projeto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
