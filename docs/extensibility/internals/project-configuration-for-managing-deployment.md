---
title: Configuração de projeto para gerenciamento de implantação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ffa661d8bf33219a3a2956cef3e456c9b5f1146
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726013"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuração de projeto para gerenciar a implantação
A implantação é o ato de mover fisicamente os itens de saída de um processo de compilação para o local esperado para depuração e instalação. Por exemplo, um aplicativo Web pode ser criado em um computador local e, em seguida, colocado no servidor.

 o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dá suporte a duas maneiras em que os projetos podem estar envolvidos na implantação:

- Como o assunto do processo de implantação.

- Como o gerente do processo de implantação.

  Antes que as soluções possam ser implantadas, você deve primeiro adicionar um projeto de implantação para configurar as opções de implantação. Se o projeto de implantação ainda não existir, você será perguntado se deseja criar um ao selecionar **implantar solução** no menu **Compilar** ou clicar com o botão direito do mouse na solução. Clicar em **Sim** abre a caixa de diálogo **Adicionar novo projeto** com o projeto do **Assistente de implantação remota** selecionado.

  O assistente de implantação remota solicita o tipo de aplicativo (Windows ou Web), os grupos de saída do projeto a serem incluídos, os arquivos adicionais que você deseja incluir e o computador remoto no qual você deseja implantar. A última página do assistente exibe um resumo das opções selecionadas.

  Os projetos que são o assunto de um processo de implantação produzem itens de saída que devem ser movidos para um ambiente alternativo. Esses itens de saída são descritos como parâmetros para a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, cuja principal finalidade é permitir que os projetos agrupem saídas. Para obter mais informações relacionadas à implementação de `IVsProjectCfg2`, consulte [configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md).

  Projetos de implantação, que gerenciam o processo de implantação, habilitam o comando implantar e respondem quando esse comando é selecionado. Projetos de implantação implementam a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> para executar a implantação e fazer chamadas para a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> para relatar eventos de status de implantação.

  As configurações podem especificar dependências que afetam suas operações de compilação ou implantação. Compilar ou implantar dependências são projetos que devem ser compilados ou implantados antes ou depois que as próprias configurações são criadas ou implantadas. As dependências de compilação entre projetos são descritas com a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> e implantam dependências com a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>. Para obter mais informações, consulte [configuração de projeto para compilação](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Consulte também
- [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md)
- [Configuração do projeto para compilação](../../extensibility/internals/project-configuration-for-building.md)
- [Configuração do projeto para saída](../../extensibility/internals/project-configuration-for-output.md)