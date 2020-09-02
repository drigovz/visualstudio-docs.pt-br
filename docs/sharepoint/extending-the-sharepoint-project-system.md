---
title: Estendendo o sistema de projeto do SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dce10c2bc44eb4fde6a6e38417d136ea5e9ba41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62557018"
---
# <a name="extend-the-sharepoint-project-system"></a>Estender o sistema de projeto do SharePoint
  Você pode criar soluções do SharePoint usando um conjunto de modelos de projeto e modelos de item no Visual Studio. Esses modelos atendem aos requisitos de vários cenários de desenvolvimento, mas você pode descobrir alguns casos em que eles não fornecem funcionalidade necessária. Nesses casos, você pode estender o sistema de projeto do SharePoint.

## <a name="overview-of-the-sharepoint-project-system"></a>Visão geral do sistema de projeto do SharePoint
 O sistema de projeto do SharePoint é baseado no componente fundamental dos *itens de projeto do SharePoint*. Um item de projeto do SharePoint representa uma única personalização do SharePoint, como uma definição de lista, Web Part ou tipo de conteúdo.

 Um projeto do SharePoint é um projeto do Visual Studio que inclui um ou mais itens de projeto do SharePoint. Os projetos do SharePoint também contêm componentes adicionais que definem como os itens de projeto são agrupados em recursos e pacotes para implantação.

 Para obter mais informações sobre o conteúdo de itens de projeto do SharePoint e projetos do SharePoint, consulte [criar modelos de item e modelos de projeto para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Como estender o sistema de projeto do SharePoint
 Você pode estender o sistema de projeto do SharePoint das seguintes maneiras:

- Defina seus próprios tipos de item de projeto do SharePoint e associe-os a novos modelos de item ou modelos de projeto no Visual Studio. Por exemplo, você pode definir um tipo de item de projeto do SharePoint para criar uma ação personalizada ou um campo. Para obter mais informações, consulte [definir tipos personalizados de item de projeto do SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Estenda os tipos de item de projeto do SharePoint que já estão instalados no Visual Studio. Por exemplo, você pode adicionar um item de menu de atalho a um item de projeto no **Gerenciador de soluções** e personalizar o item de projeto quando um desenvolvedor escolher o item de menu. Para obter mais informações, consulte [estender itens de projeto do SharePoint](../sharepoint/extending-sharepoint-project-items.md).

- Estenda projetos do SharePoint. Por exemplo, você pode adicionar manipuladores de eventos para executar tarefas específicas quando itens são adicionados ou removidos de projetos do SharePoint. Para obter mais informações, consulte [estender projetos do SharePoint](../sharepoint/extending-sharepoint-projects.md).

- Estenda o comportamento de empacotamento e implantação de itens de projeto do SharePoint e projetos do SharePoint. Por exemplo, você pode criar suas próprias etapas de implantação para executar ao implantar ou cancelar um projeto ou pode executar tarefas personalizadas adicionais quando o Visual Studio executar determinadas etapas de implantação. Para obter mais informações, consulte [estender o empacotamento e a implantação do SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Tarefas comuns de desenvolvimento
 Você pode executar as seguintes tarefas comuns em extensões do sistema de projeto do SharePoint:

- Salve dados de cadeia de caracteres personalizados com itens de projeto e em vários tipos diferentes de arquivos de projeto. Para obter mais informações, consulte [salvar dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Converter um objeto no sistema de projeto do SharePoint em um objeto correspondente no modelo de objeto de automação do Visual Studio ou no modelo de objeto de integração ou vice-versa. Para obter mais informações, consulte [conver entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>Confira também
- [Definir tipos de item de projeto personalizados do SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Estender itens de projeto do SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Estender projetos do SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Estender o empacotamento e a implantação do SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Salvar dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Converter entre os tipos do sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Estenda as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Conceitos e recursos de programação para extensões de ferramentas do SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
