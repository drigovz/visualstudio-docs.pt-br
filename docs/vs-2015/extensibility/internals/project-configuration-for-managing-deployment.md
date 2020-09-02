---
title: Configuração de projeto para gerenciamento de implantação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5b16c3392e9432ba540130d45f6907de15b51ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429945"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuração de projeto para gerenciar a implantação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A implantação é o ato de mover fisicamente os itens de saída de um processo de compilação para o local esperado para depuração e instalação. Por exemplo, um aplicativo Web pode ser criado em um computador local e, em seguida, colocado no servidor.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o oferece suporte a duas maneiras em que os projetos podem estar envolvidos na implantação:  
  
- Como o assunto do processo de implantação.  
  
- Como o gerente do processo de implantação.  
  
  Antes que as soluções possam ser implantadas, você deve primeiro adicionar um projeto de implantação para configurar as opções de implantação. Se o projeto de implantação ainda não existir, você será perguntado se deseja criar um ao selecionar **implantar solução** no menu **Compilar** ou clicar com o botão direito do mouse na solução. Clicar em **Sim** abre a caixa de diálogo **Adicionar novo projeto** com o projeto do **Assistente de implantação remota** selecionado.  
  
  O assistente de implantação remota solicita o tipo de aplicativo (Windows ou Web), os grupos de saída do projeto a serem incluídos, os arquivos adicionais que você deseja incluir e o computador remoto no qual você deseja implantar. A última página do assistente exibe um resumo das opções selecionadas.  
  
  Os projetos que são o assunto de um processo de implantação produzem itens de saída que devem ser movidos para um ambiente alternativo. Esses itens de saída são descritos como parâmetros para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interface, cuja principal finalidade é permitir que os projetos agrupem saídas. Para obter mais informações relacionadas à implementação do `IVsProjectCfg2` , consulte [configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md).  
  
  Projetos de implantação, que gerenciam o processo de implantação, habilitam o comando implantar e respondem quando esse comando é selecionado. Projetos de implantação implementam a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface para executar a implantação e fazer chamadas para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interface para relatar eventos de status de implantação.  
  
  As configurações podem especificar dependências que afetam suas operações de compilação ou implantação. Compilar ou implantar dependências são projetos que devem ser compilados ou implantados antes ou depois que as próprias configurações são criadas ou implantadas. As dependências de compilação entre projetos são descritas com a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interface e implantam dependências com a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interface. Para obter mais informações, consulte [configuração de projeto para compilação](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md)   
 [Configuração do projeto para compilação](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md)
