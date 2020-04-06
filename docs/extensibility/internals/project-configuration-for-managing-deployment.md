---
title: Configuração do projeto para gerenciamento de implantação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706704"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuração de projeto para gerenciar a implantação
Implantação é o ato de mover fisicamente os itens de saída de um processo de compilação para o local esperado para depuração e instalação. Por exemplo, um aplicativo Web pode ser construído em uma máquina local e, em seguida, colocado no servidor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]suporta duas maneiras pelas quais os projetos podem estar envolvidos na implantação:

- Como objeto do processo de implantação.

- Como gerente do processo de implantação.

  Antes que as soluções possam ser implantadas, você deve primeiro adicionar um projeto de implantação para configurar opções de implantação. Se o projeto de implantação ainda não existir, será perguntado se deseja criar um quando selecionar **'Implantar solução'** no menu **Construir** ou clicar com o botão direito do mouse na solução. Clicar **em Sim** abre a caixa de diálogo **Adicionar novo projeto** com o projeto **'Controle remoto' do Assistente** de Implante selecionado.

  O Assistente de Implantação Remota pede que o tipo de aplicativo (Windows ou Web), os grupos de saída do projeto incluam, quaisquer arquivos adicionais que você deseja incluir e o computador remoto para o qual você deseja implantar. A última página do assistente exibe um resumo das opções selecionadas.

  Projetos que são objeto de um processo de implantação produzem itens de saída que devem ser movidos para um ambiente alternativo. Esses itens de saída são descritos como parâmetros para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interface, cujo objetivo principal se permitir projetos para agrupar saídas. Para obter mais informações relacionadas à implementação de , consulte `IVsProjectCfg2` [Configuração do projeto para saída](../../extensibility/internals/project-configuration-for-output.md).

  Os projetos de implantação, que gerenciam o processo de implantação, habilitam o comando Deploy e respondem quando este comando é selecionado. Os projetos <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> de implantação implementam a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> para executar a implantação e fazem chamadas para a interface para relatar eventos de status de implantação.

  As configurações podem especificar dependências que afetam suas operações de compilação ou implantação. Construir ou implantar dependências são projetos que devem ser construídos ou implantados antes ou depois que as próprias configurações forem construídas ou implantadas. As dependências de construção <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> entre projetos são descritas com a interface e implantam dependências com a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interface. Para obter mais informações, consulte [Configuração do projeto para construção](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Confira também
- [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md)
- [Configuração de projeto para compilar](../../extensibility/internals/project-configuration-for-building.md)
- [Configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md)
