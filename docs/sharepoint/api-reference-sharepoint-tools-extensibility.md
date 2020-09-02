---
title: Referência de API (extensibilidade de ferramentas do SharePoint) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, reference for project and tools extensibility
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 37639068b74b5d99864871355a8b9ef36906f6cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62987984"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>Referência de API (extensibilidade de ferramentas do SharePoint)
  Esta seção contém documentação de referência de API para estender as ferramentas do SharePoint no Visual Studio.

## <a name="in-this-section"></a>Nesta seção
 <xref:Microsoft.VisualStudio.SharePoint>

 Contém tipos que você usa para estender o sistema de projeto do SharePoint. Por exemplo, você pode estender os projetos internos do SharePoint e os itens do projeto, ou pode criar seus próprios itens de projeto.

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 Contém tipos que você pode usar para criar *comandos personalizados do SharePoint*. Um comando do SharePoint é um método que chama o modelo de objeto do SharePoint Server a partir de uma extensão de ferramentas do SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Deployment>

 Contém tipos que você usa para estender o processo de implantação para projetos do SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer>

 Contém tipos que você usa para estender nós do SharePoint no **Gerenciador de servidores** ou para definir seus próprios tipos de nós.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>

 Contém tipos que você pode usar para obter informações sobre nós de **Gerenciador de servidores** internos que representam componentes individuais em um site do SharePoint, como um nó que representa uma lista, um campo ou um tipo de conteúdo.

 <xref:Microsoft.VisualStudio.SharePoint.Features>

 Contém tipos que você usa para acessar a definição de um recurso em um projeto do SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Packages>

 Contém tipos que você usa para acessar a definição de pacote em um projeto do SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>

 Contém tipos que você usa para autenticar e se comunicar com aplicativos para SharePoint que são implantados em sites remotos do SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>

 Contém tipos que você usa para criar comandos remotos do SharePoint, que são usados com aplicativos para SharePoint que são implantados em sites remotos do SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Tasks>

 Contém tipos que o Visual Studio usa como tarefas de compilação para empacotar e depurar projetos do SharePoint, aplicativos para o Office e aplicativos para SharePoint. Esta API dá suporte à infraestrutura do Office e do SharePoint e não se destina a ser usada diretamente de seu código.

 <xref:Microsoft.VisualStudio.SharePoint.Validation>

 Contém tipos que você usa para personalizar o recurso e o comportamento de validação do pacote para um projeto do SharePoint.

## <a name="see-also"></a>Confira também
- [Referência &#40;extensibilidade de ferramentas do SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Visão geral do modelo de programação das extensões de ferramentas do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Estenda o nó conexões do SharePoint no Gerenciador de Servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Estender o empacotamento e a implantação do SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Chamar para os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
