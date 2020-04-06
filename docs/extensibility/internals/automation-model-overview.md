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
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710002"
---
# <a name="automation-model-overview"></a>Visão geral do modelo de automação
O modelo de automação consiste em um conjunto de objetos contra os quais você pode escrever um complemento ou extensão do Visual Studio. Um complemento é um aplicativo que pode manipular o ambiente do Visual Studio e automatizar tarefas comuns. Uma extensão do Visual Studio pode criar componentes personalizados do Visual Studio ou adicionar à funcionalidade de componentes padrão, como o editor de texto.

## <a name="objects-in-the-automation-model"></a>Objetos no modelo de automação
 O modelo de automação consiste em grupos relacionados de objetos que controlam as principais facetas do ambiente comum. O diagrama a seguir mostra o extenso conjunto de objetos do Visual Studio que compõem o modelo de automação.

 ![Gráfico de objetos de automação do Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Para obter mais informações, consulte [Estender o ambiente do Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 O ambiente fornece um modelo para diferentes áreas funcionais. Por exemplo, há um modelo de código para vários elementos que você pode encontrar em código. Há um modelo de documento para vários elementos de documento. Uma área, a área do projeto, é de particular interesse para os provedores de VSPackage. Você provavelmente vai querer que seus novos tipos de projeto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuam para o modelo de automação da mesma forma que e contribuam para o modelo de automação. Esse processo é descrito em [Fornecer automação para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Lugares onde você pode considerar estender o modelo de automação do ambiente:

- Project

- Document

- Código

- Build

Para obter mais informações sobre automação, consulte [Automação e extensibilidade para Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Este documento e os documentos aos seus links aos que ele fornece links, ajudam você a tomar decisões sobre como você deve fornecer automação para o seu VSPackage.

## <a name="see-also"></a>Confira também
- [Como: Criar um complemento](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
