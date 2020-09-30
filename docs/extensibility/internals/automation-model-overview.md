---
title: Visão geral do modelo de automação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83df8926be9cd7217c514a2ed3f242bf8e121913
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584562"
---
# <a name="automation-model-overview"></a>Visão geral do modelo de automação
O modelo de automação consiste em um conjunto de objetos em que é possível escrever um suplemento ou uma extensão do Visual Studio. Um suplemento é um aplicativo que pode manipular o ambiente do Visual Studio e automatizar tarefas comuns. Uma extensão do Visual Studio pode criar componentes personalizados do Visual Studio ou adicionar à funcionalidade de componentes padrão, como o editor de texto.

## <a name="objects-in-the-automation-model"></a>Objetos no modelo de automação
 O modelo de automação consiste em grupos de objetos relacionados que controlam as principais facetas do ambiente comum. O diagrama a seguir mostra o amplo conjunto de objetos do Visual Studio que compõem o modelo de automação.

 ![Gráfico de objeto de automação do Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Para obter mais informações, consulte [estender o ambiente do Visual Studio](/previous-versions/esk3eey8(v=vs.140)).

 O ambiente fornece um modelo para diferentes áreas funcionais. Por exemplo, há um modelo de código para vários elementos que você pode encontrar no código. Há um modelo de documento para vários elementos de documento. Uma área, a área do projeto, é de interesse particular para os provedores de VSPackage. Você provavelmente desejará que seus novos tipos de projeto contribuam para o modelo de automação da mesma forma que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuem para o modelo de automação. Esse processo é descrito em [fornecer automação para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Locais onde você pode considerar a extensão do modelo de automação do ambiente:

- Project

- Documento

- Código

- Compilação

Para obter mais informações sobre automação, consulte [automação e extensibilidade para o Visual Studio](../../vs-2015/extensibility/extensibility-in-visual-studio.md?view=vs-2015&preserve-view=true). Este documento e os documentos aos quais ele fornece links, ajudam você a tomar decisões sobre como você deve fornecer automação para seu VSPackage.

## <a name="see-also"></a>Confira também
- [Como: criar um suplemento](/previous-versions/80493a3w(v=vs.140))