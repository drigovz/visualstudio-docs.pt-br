---
title: Desenvolvimento do Office e do SharePoint no Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce0084d6bf734ee8a9de63b0cf3da73504b0d4e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800938"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Desenvolvimento do Office e do SharePoint no Visual Studio
  Você pode estender Microsoft Office e SharePoint criando um aplicativo leve ou suplemento que os usuários baixam da [Office Store](https://store.office.com/) ou de um catálogo organizacional ou criando uma solução baseada em .NET Framework que os usuários instalam em um computador.

 Neste tópico:

- [Criar suplementos para Office e SharePoint](#Apps)

- [Criar um suplemento do VSTO](#Add-ins)

- [Criar uma solução do SharePoint](#Solutions)

## <a name="create-add-ins-for-office-and-sharepoint"></a><a name="Apps"></a> Criar suplementos para Office e SharePoint
 O Office 2013 e o SharePoint 2013 apresentam um novo modelo de suplemento que ajuda você a criar, distribuir e monetizar suplementos que estendem o Office e o SharePoint.  Esses suplementos podem ser executados no Office ou no SharePoint Online, e os usuários podem interagir com eles a partir de vários dispositivos.

 Descubra como usar o novo modelo de [suplemento do Office](/office/dev/add-ins/overview/office-add-ins) para estender a experiência do Office para seus usuários.

 Esses suplementos têm pequenos vestígios em comparação com os suplementos e soluções do VSTO, e você pode criá-los usando quase qualquer tecnologia de programação da Web, como HTML5, JavaScript, CSS3 e XML.  Para começar, use o Office Developer Tools no Visual Studio, que permite criar projetos, escrever código e executar os suplementos em um navegador.

 ![Aplicativos para o Office e modelo conceitual do SharePoint](../vsto/media/officeandsharepointapps2015.png "Aplicativos para o Office e modelo conceitual do SharePoint")

### <a name="build-an-office-add-in"></a>Criar um suplemento do Office
 Para estender a funcionalidade do Office, crie um suplemento do Office. Basicamente, é uma página da web hospedada em um aplicativo do Office, como Excel, Word, Outlook e PowerPoint. Seu aplicativo pode adicionar funcionalidade a documentos, planilhas, mensagens de email, compromissos, apresentações e projetos.

 Você pode vender seu aplicativo na Office Store.  A [Office Store](https://store.office.com/) torna mais fácil monetizar seus suplementos, gerenciar atualizações e acompanhar a telemetria. Você também pode publicar seu aplicativo para usuários por meio de um aplicativo de aplicativos no SharePoint ou no Exchange Server.

 O seguinte aplicativo do Office mostra os dados da planilha em um mapa do Bing.

 ![Aplicativo de conteúdo para Office](../vsto/media/appforoffice.png "Aplicativo de conteúdo para Office")

 **Saiba mais**

|Para|Consulte|
|--------|---------|
|Saiba mais sobre os suplementos do Office e crie um.|[Suplementos do Office](/office/dev/add-ins/publish/publish)|
|Compare as diferentes maneiras pelas quais você pode estender o Office e decida se deve usar um aplicativo ou um suplemento do Office.|[Roteiro para suplementos do Office, VSTO e VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|

### <a name="build-a-sharepoint-add-in"></a>Criar um suplemento do SharePoint
 Para estender o SharePoint para seus usuários, crie um suplemento do SharePoint. Basicamente, ele é um aplicativo autônomo pequeno e fácil de usar que resolve a necessidade de seus usuários ou negócios.

 Você pode vender seu aplicativo para SharePoint na [Office Store](https://store.office.com/). Você também pode publicar seu suplemento para usuários por meio de um catálogo de suplementos no SharePoint.  Os proprietários de sites podem instalar, atualizar e desinstalar seu suplemento em seus sites do SharePoint sem a ajuda de um servidor de farm ou administrador de conjunto de sites.

 Aqui está um exemplo de um aplicativo para o SharePoint que ajuda os usuários a gerenciar contatos comerciais.

 ![Aplicativo Business Contact Manager para SharePoint](../vsto/media/appforsharepoint.png "Aplicativo Business Contact Manager para SharePoint")

 **Saiba mais**

|Para|Consulte|
|--------|---------|
|Saiba mais sobre os suplementos do SharePoint e crie um.|[Suplementos do SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|Compare suplementos para o SharePoint com soluções tradicionais do SharePoint.|[Suplementos do SharePoint em comparação com as soluções do SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Escolha se deseja criar um suplemento do SharePoint ou uma solução do SharePoint.|[Decidir entre suplementos do SharePoint e soluções do SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="create-a-vsto-add-in"></a><a name="Add-ins"></a> Criar um suplemento do VSTO
 Crie um suplemento do VSTO para o Office 2007 ou o Office 2010 de destino ou estenda o Office 2013 e o Office 2016 além do que é possível com os suplementos do Office. Os suplementos do VSTO são executados somente na área de trabalho. Os usuários precisam instalar suplementos do VSTO, de modo que normalmente são mais difíceis de implantar e dar suporte ao.  No entanto, seu suplemento do VSTO pode ser integrado mais próximo ao Office. Por exemplo, ele pode adicionar controles à Faixa de Opções do Office e executar tarefas de automação avançadas como mesclar documentos ou modificar gráficos. Você pode aproveitar o .NET Framework e usar o C# e o Visual Basic para interagir com objetos do Office.

 Veja um exemplo do que um suplemento do VSTO pode fazer. Este suplemento do VSTO adiciona controles da faixa de, um painel de tarefas personalizado e uma caixa de diálogo ao PowerPoint.

 ![Solução de suplemento do PowerPoint](../vsto/media/powerpointaddin.png "Solução de suplemento do PowerPoint")

 **Saiba mais**

|Para|Ler|
|--------|----------|
|Compare as diferentes maneiras pelas quais você pode estender o Office e decida se deve usar um suplemento do VSTO ou um suplemento do Office.|[Roteiro para suplementos do Office, VSTO e VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|
|Crie um suplemento do VSTO.|[Suplementos do VSTO criados com o Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="create-a-sharepoint-solution"></a><a name="Solutions"></a> Criar uma solução do SharePoint
 Crie uma solução do SharePoint para direcionar o SharePoint Foundation 2010 e o SharePoint Server 2010, ou para estender o SharePoint 2013 e o SharePoint 2016 de maneiras além das possíveis com um suplemento do SharePoint.

 Soluções do SharePoint exigem servidores de farm do SharePoint no local. Os administradores devem instalá-los e, como soluções são executada no SharePoint, podem afetar o desempenho do servidor. No entanto, soluções fornecem maior acesso a objetos do SharePoint. Além disso, quando você cria uma solução do SharePoint, pode utilizar o .NET Framework e usar C# e Visual Basic para interagir com objetos do SharePoint.

 **Saiba mais**

|Para|Consulte|
|--------|---------|
|Compare as soluções do SharePoint com os suplementos do SharePoint.|[Suplementos do SharePoint em comparação com as soluções do SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Criar uma solução do SharePoint.|[Criar soluções do SharePoint](../sharepoint/create-sharepoint-solutions.md)|
