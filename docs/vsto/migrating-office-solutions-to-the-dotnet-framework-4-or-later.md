---
title: Migrar soluções do Office para o .NET Framework 4 ou posterior
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9531f0495bd0dc0a9f095ff71fdfd84fc8d1380
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189785"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrar soluções do Office para o .NET Framework 4 ou posterior
  Se a estrutura de destino de um projeto do Office for alterada para a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, algumas etapas adicionais poderão ser necessárias para continuar a executar a solução em computadores de usuário final e de desenvolvimento. Para obter mais informações, consulte [as alterações necessárias para executar projetos do Office que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Além disso, o projeto pode não compilar mais. Alguns recursos dos projetos do Office têm modelos de programação diferentes para diferentes versões do .NET Framework. Quando a estrutura de destino de um projeto do Office é alterada para a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, você deve fazer as seguintes alterações de código no projeto:

- [Atualize os projetos do Excel e do Word que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Atualize as personalizações da faixa de na de projetos do Office que você migra para o .NET Framework 4 ou o .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Atualize as regiões de formulário nos projetos do Outlook que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  A estrutura de destino de um projeto do Office é alterada quando você atualiza o projeto de uma versão anterior do Visual Studio. Para obter mais informações, consulte [atualizar e migrar soluções do Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Para obter mais informações sobre por que alguns recursos em projetos do Office têm um modelo de programação diferente quando você direciona o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, consulte [alterações no design de projetos do Office que visam o .NET Framework 4 ou o .NET Framework 4,5 e o](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) [Visual Visão geral do Studio Tools for Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Consulte também
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Como: direcionar uma versão do .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Solucionar erros em soluções do Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Suporte adicional para erros em soluções do Office](../vsto/additional-support-for-errors-in-office-solutions.md)
