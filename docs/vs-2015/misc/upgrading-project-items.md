---
title: Atualizando itens de projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698693"
---
# <a name="upgrading-project-items"></a>Atualizando Itens de Projeto
Se você adicionar ou gerenciar itens dentro de sistemas de projeto que não implementar, talvez seja necessário participar do processo de atualização do projeto. O Crystal Reports é um exemplo de um item que pode ser adicionado ao sistema de projeto.  
  
 Normalmente, os implementadores de item de projeto desejam aproveitar um projeto já totalmente instanciado e atualizado, pois eles precisam saber quais são as referências do projeto e quais outras propriedades do projeto existem para tomar uma decisão de atualização.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Para obter a notificação de atualização do projeto  
  
1. Defina o <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> sinalizador (definido em vsshell80. idl) na implementação do item do projeto. Isso faz com que o item de projeto VSPackage o carregamento automático quando o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell determina que um sistema de projeto está no processo de atualização.  
  
2. Avise a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface por meio do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> método.  
  
3. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface é acionada depois que a implementação do sistema do projeto concluiu suas operações de atualização e o novo projeto atualizado é criado. Dependendo do cenário, a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface é acionada após os <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> métodos, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> .  
  
### <a name="to-upgrade-the-project-item-files"></a>Para atualizar os arquivos de item de projeto  
  
1. Você deve gerenciar cuidadosamente o processo de backup de arquivo em sua implementação de item de projeto. Isso se aplica em particular para um backup lado a lado, onde o `fUpgradeFlag` parâmetro do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método é definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> , onde os arquivos cujo backup foi feito são colocados em arquivos que são designados como ". old". Os arquivos de backup mais antigos que a hora do sistema em que o projeto foi atualizado podem ser designados como obsoletos. Além disso, eles podem ser substituídos, a menos que você execute etapas específicas para evitar isso.  
  
2. No momento em que o item do projeto recebe uma notificação da atualização do projeto, o **Assistente de conversão do Visual Studio** ainda é exibido. Portanto, você deve usar os métodos da <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interface para fornecer mensagens de atualização para a interface do usuário do assistente.  
  
## <a name="see-also"></a>Consulte Também  
 [Assistente de conversão do Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Atualizando projetos personalizados](../misc/upgrading-custom-projects.md)