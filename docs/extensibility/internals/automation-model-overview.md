---
title: Visão geral do modelo de automação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ea38dc79bd557f17bbae8276dd112304c9a40fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186727"
---
# <a name="automation-model-overview"></a>Visão geral do modelo de automação
O modelo de automação consiste em um conjunto de objetos em que é possível escrever um suplemento ou uma extensão do Visual Studio. Um suplemento é um aplicativo que pode manipular o ambiente do Visual Studio e automatizar tarefas comuns. Uma extensão do Visual Studio pode criar componentes personalizados do Visual Studio ou adicionar à funcionalidade de componentes padrão, como o editor de texto.

## <a name="objects-in-the-automation-model"></a>Objetos no modelo de automação
 O modelo de automação consiste em grupos de objetos relacionados que controlam as principais facetas do ambiente comum. O diagrama a seguir mostra o amplo conjunto de objetos do Visual Studio que compõem o modelo de automação.

 ![Gráfico de objeto de automação do Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Para obter mais informações, consulte [estender o ambiente do Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 O ambiente fornece um modelo para diferentes áreas funcionais. Por exemplo, há um modelo de código para vários elementos que você pode encontrar no código. Há um modelo de documento para vários elementos de documento. Uma área, a área do projeto, é de interesse particular para os provedores de VSPackage. Você provavelmente desejará que seus novos tipos de projeto contribuam para o modelo de automação praticamente da mesma forma que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuir para o modelo de automação. Esse processo é descrito em [fornecer automação para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Locais onde você pode considerar a extensão do modelo de automação do ambiente:

- Projeto

- Documento

- Código

- Build

Para obter mais informações sobre automação, consulte [automação e extensibilidade para o Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Este documento e os documentos aos quais ele fornece links, ajudam você a tomar decisões sobre como você deve fornecer automação para seu VSPackage.

## <a name="see-also"></a>Consulte também
- [Como: criar um suplemento](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)