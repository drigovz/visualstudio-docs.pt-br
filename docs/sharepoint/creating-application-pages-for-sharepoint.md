---
title: Criando páginas de aplicativo para o SharePoint | Microsoft Docs
description: Criar páginas de aplicativo para o SharePoint. Uma página de aplicativo é uma página da Web ASP.NET que é projetada para uso em um site do SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1228ef551235fd616803d6e05057ee50f0ea7ec4
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850436"
---
# <a name="create-application-pages-for-sharepoint"></a>Criar páginas de aplicativo para o SharePoint
  Uma *página de aplicativo* é uma página da Web ASP.NET que é projetada para uso em um site do SharePoint. As páginas de aplicativo são um tipo especializado de página ASP.NET. A principal diferença entre uma página de aplicativo e uma página ASP.NET padrão é que uma página de aplicativo contém conteúdo que é mesclado com uma página mestra do SharePoint. Uma página mestra permite que as páginas do aplicativo compartilhem a mesma aparência e comportamento de outras páginas em um site.

 O Visual Studio permite que você projete páginas de aplicativo usando um designer. O designer exibe uma área de conteúdo para cada espaço reservado de conteúdo que é definido em uma página mestra. Você pode criar a página do aplicativo arrastando controles para essas áreas de conteúdo.

## <a name="application-pages"></a>Páginas do aplicativo
 As páginas de aplicativo são compartilhadas em todos os sites no servidor, enquanto uma página do site é específica para um site. Para obter mais informações, [tipos de página do SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

 Por padrão, a maioria das páginas que aparecem quando você cria um site do SharePoint são páginas do site. Uma página do site pode ser adicionada a uma biblioteca de páginas do SharePoint. Os usuários podem personalizar uma página do site usando ferramentas como o SharePoint Designer. Uma página do site também pode hospedar recursos como Web Parts dinâmicos e zonas de Web Part.

 As páginas do aplicativo não podem fazer essas coisas. No entanto, uma página de aplicativo é o melhor tipo de página a ser criada se você quiser que a página contenha código personalizado. Embora você possa adicionar código personalizado a uma página do site, o código para de ser executado quando o usuário personaliza a página usando ferramentas como o SharePoint Designer.

> [!NOTE]
> O Visual Studio não fornece modelos que ajudam a criar páginas de site para um site do SharePoint. Para obter mais informações, consulte [tipos de página do SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

## <a name="create-an-application-page"></a>Criar uma página de aplicativo
 Para criar uma página de aplicativo, adicione um item de **página de aplicativo** a um projeto do SharePoint. Quando você cria uma página de aplicativo, o Visual Studio adiciona as seguintes pastas ao seu projeto:

|Pasta|Descrição|
|------------|-----------------|
|Layouts|Mapeia para o diretório virtual _layouts do sistema de arquivos do SharePoint.|
|Subpasta layouts|Contém os arquivos que compõem a página do aplicativo. Por padrão, essa pasta tem o mesmo nome que o seu projeto. Você pode renomear essa pasta a qualquer momento. Quando você executa o projeto, o Visual Studio implanta essa pasta no diretório virtual _layouts do sistema de arquivos do SharePoint.|

 O Visual Studio adiciona os seguintes arquivos ao seu projeto:

|Arquivo|Descrição|
|----------|-----------------|
|Arquivo de paginação ASP.NET (*. aspx*)|Contém a marcação XML que define a página.|
|Arquivo de código de página do aplicativo|Contém o código por trás da página do aplicativo. Adicione o código que manipula eventos a esse arquivo.|
|Arquivo de código do designer de página do aplicativo|Contém o código que é gerado pelo designer. Não edite este arquivo diretamente.|

## <a name="design-and-debug-an-application-page"></a>Criar e depurar uma página de aplicativo
 Crie o conteúdo de uma página de aplicativo usando o modo de exibição de designer no Visual Studio. Esse designer aparece quando você abre a página do aplicativo em seu projeto (clicando duas vezes nele ou abrindo o menu de atalho e escolhendo **abrir**) e, em seguida, escolhe o botão **design** na parte inferior do editor.

> [!NOTE]
> Você pode criar a página somente na exibição de **origem** do designer. O modo de exibição de **design** do designer está desabilitado para páginas de aplicativo.

 Você pode depurar uma página de aplicativo da mesma forma que depuraria outros itens de projeto do SharePoint no Visual Studio. Quando você inicia o depurador do Visual Studio, o Visual Studio abre o site do SharePoint.

 Para exibir a página do aplicativo, você deve navegar manualmente até o local da página do aplicativo (por exemplo: http://<em>server_name</em>/_layouts/*Project_Name*/ApplicationPage1.aspx).

 Para obter mais informações sobre como depurar projetos do SharePoint, consulte [solução de problemas de soluções do SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Escolher uma página mestra
 Por padrão, um item de **página de aplicativo** faz referência à página mestra do site que você está usando para depurar seu projeto. Essa página é denominada v4. Master e você pode encontrá-la listada na **Galeria de páginas mestras** do site do SharePoint.

 Você pode alterar explicitamente qual página mestra é usada pela página do aplicativo definindo o `MasterPageFile` atributo do `Page` elemento Application. (Por exemplo: `MasterPageFile="~/_layouts/applicationv4.master"` ). Na verdade, você deve definir esse atributo se as páginas mestras dinâmicas não estiverem habilitadas no servidor do SharePoint. Para obter mais informações sobre páginas mestras no SharePoint, consulte [páginas mestras](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14)).

## <a name="see-also"></a>Confira também
- [Desenvolvimento do SharePoint Foundation em detalhes](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [Visão geral do ASP.NET](/aspnet/overview)
- [Páginas da Web do ASP.NET](/aspnet/web-pages/index)
