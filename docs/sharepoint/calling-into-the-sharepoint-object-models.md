---
title: Chamando os modelos de objeto do SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24634143a40f7b163c0b658bddb5596041868033
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62988405"
---
# <a name="call-into-the-sharepoint-object-models"></a>Chamar para os modelos de objeto do SharePoint
  Quando você cria extensões para as ferramentas do SharePoint no Visual Studio, talvez seja necessário chamar as APIs do SharePoint para executar determinadas tarefas. Por exemplo, se você criar uma etapa de implantação personalizada para projetos do SharePoint, talvez precise chamar as APIs do SharePoint para executar algumas das tarefas para implantar soluções.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] fornecem dois modelos de objeto diferentes que você pode usar nas extensões de ferramentas do SharePoint: um modelo de objeto de servidor e um modelo de objeto de cliente. Cada modelo de objeto tem benefícios e desvantagens no contexto das extensões de ferramentas do SharePoint.

 Para obter uma visão geral dos modelos de objeto do SharePoint, consulte [visão geral do modelo de programação das extensões de ferramentas do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Usar o modelo de objeto de cliente em projetos de extensão
 Ao desenvolver uma extensão para as ferramentas do SharePoint, você pode usar o modelo de objeto do cliente em seu projeto como qualquer outro conjunto de APIs gerenciadas. Você pode adicionar referências a assemblies no modelo de objeto do cliente ao seu projeto e pode chamar APIs no modelo de objeto do cliente diretamente do seu código.

 No entanto, o modelo de objeto de cliente tem duas desvantagens no contexto das extensões de ferramentas do SharePoint:

- O modelo de objeto de cliente fornece apenas um subconjunto do modelo de objeto de servidor. Se você precisar usar a funcionalidade do SharePoint que não é exposta no modelo de objeto do cliente, você deve usar o modelo de objeto do servidor.

- Embora o uso do modelo de objeto de cliente nas extensões de ferramentas do SharePoint deva funcionar na maioria dos casos, você pode encontrar alguns cenários em que as chamadas para o modelo de objeto do cliente não funcionam conforme o esperado. O modelo de objeto de cliente foi projetado para ser usado em aplicativos cliente para chamar sites do SharePoint em um farm ou servidor remoto. As ferramentas do SharePoint no Visual Studio funcionam apenas com uma instalação local do SharePoint no computador de desenvolvimento. Portanto, ao usar o modelo de objeto de cliente em uma extensão de ferramentas do SharePoint, você chama um site do SharePoint no computador local, que não é como o modelo de objeto de cliente foi projetado para ser usado.

  Para obter instruções que demonstram como usar o modelo de objeto de cliente em uma extensão das ferramentas do SharePoint no Visual Studio, consulte [passo a passos: chamar no modelo de objeto de cliente do SharePoint em uma extensão Gerenciador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Usar o modelo de objeto de servidor em projetos de extensão
 O modelo de objeto de servidor é um superconjunto do modelo de objeto de cliente. Ao usar o modelo de objeto de servidor, você pode usar todos os recursos que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] expor programaticamente.

 As extensões de ferramentas do SharePoint podem usar APIs no modelo de objeto de servidor, mas não podem chamar as APIs diretamente. O modelo de objeto de servidor pode ser chamado somente de um processo de 64 bits que tem como alvo o .NET Framework 3,5. No entanto, as extensões de ferramentas do SharePoint exigem o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e são executadas no processo do Visual Studio de 32 bits. Isso impede que as extensões das ferramentas do SharePoint referenciem os assemblies no modelo de objeto do SharePoint Server diretamente.

 Se você quiser usar o modelo de objeto de servidor em uma extensão de ferramentas do SharePoint, deverá criar um *comando do SharePoint* personalizado para chamar a API. Você define o comando do SharePoint em um assembly secundário que pode chamar diretamente o modelo de objeto de servidor. Em seu projeto de extensão, você chama o comando do SharePoint indiretamente usando o método ExecuteCommand de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto.

 Para obter mais informações sobre como criar e usar comandos do SharePoint, consulte [como: criar um comando do SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) e [como executar um comando do SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Para obter informações sobre como implantar comandos do SharePoint, consulte [implantar extensões para as ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Para obter instruções detalhadas que demonstram como criar e usar comandos do SharePoint, consulte [passo a passos: criar uma etapa de implantação personalizada para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) e [passo a passos: estender Gerenciador de servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Entenda como os comandos do SharePoint são executados
 Os assemblies que definem comandos do SharePoint são carregados em um processo de host de 64 bits chamado *vssphost4.exe*. Depois de chamar um comando do SharePoint em uma extensão de ferramentas do SharePoint, o comando é executado por *vssphost4.exe* em vez do processo do Visual Studio de 32 bits (*devenv.exe*). Você pode controlar alguns aspectos de como os comandos do SharePoint são executados definindo valores no registro. Para obter mais informações, consulte [extensões de depuração para as ferramentas do SharePoint no Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Confira também
- [Como: criar um comando do SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Como executar um comando do SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Visão geral do modelo de programação das extensões de ferramentas do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
