---
title: Migrar soluções do Office para o .NET Framework 4 ou posterior
titleSuffix: ''
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
ms.openlocfilehash: 86b975b7e84c69ff072df06e0a2c7701ab1909e7
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584484"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrar soluções do Office para o .NET Framework 4 ou posterior
  Se a estrutura de destino de um projeto do Office for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, algumas etapas adicionais podem ser necessárias para continuar a executar a solução em computadores de usuário final e de desenvolvimento. Para obter mais informações, consulte [as alterações necessárias para executar projetos do Office que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Além disso, o projeto pode não compilar mais. Alguns recursos dos projetos do Office têm modelos de programação diferentes para diferentes versões do .NET Framework. Quando a estrutura de destino de um projeto do Office é alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, você deve fazer as seguintes alterações de código no projeto:

- [Atualize os projetos do Excel e do Word que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Atualize as personalizações da faixa de na de projetos do Office que você migra para o .NET Framework 4 ou o .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Atualize as regiões de formulário nos projetos do Outlook que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  A estrutura de destino de um projeto do Office é alterada quando você atualiza o projeto de uma versão anterior do Visual Studio. Para obter mais informações, consulte [atualizar e migrar soluções do Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Para obter mais informações sobre por que alguns recursos em projetos do Office têm um modelo de programação diferente quando você visa o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, consulte [alterações no design de projetos do Office direcionados para a .NET Framework 4 ou a .NET Framework 4,5 e a](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) [visão geral do ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Confira também
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Como definir uma versão do .NET Framework como destino](../ide/visual-studio-multi-targeting-overview.md)
- [Solucionar erros em soluções do Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Suporte adicional para erros em soluções do Office](../vsto/additional-support-for-errors-in-office-solutions.md)
