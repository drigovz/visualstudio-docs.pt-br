---
title: Propriedades e métodos estendidos por subtipos do projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ba57cb5ff2bdeb4c1d6038704642b41d3b9d7a9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012905"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propriedades e métodos estendidos por subtipos de projeto
Um subtipo de projeto tem uma grande quantidade de energia para influenciar o comportamento do projeto porque ele é criado como um agregador de um projeto de base. Esta seção resume alguns dos recursos que podem ser aprimorados ou modificados por subtipos do projeto.  
  
## <a name="features-gained-by-aggregation"></a>Recursos obtidos pela agregação  
 A tabela a seguir resume a muitos dos métodos que permite a agregação subtipos do projeto substituir em projetos de base.  
  
|Métodos substituídos por agregação|Subtipo de projeto|  
|---------------------------------------|---------------------|  
|De <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Permite que um subtipo de projeto para<br /><br /> -Alterar a legenda e o ícone do nó do projeto.<br />-Substituir o projeto completamente `Browse` objeto.<br />-Controla se o projeto pode ser renomeado.<br />-Controle de ordem de classificação.<br />-O contexto de usuário control para obter ajuda dinâmica.|  
|De <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permite que um subtipo de projeto controlar quais serviços contextuais são fornecidos para designers e editores.|  
|De <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Permite que um subtipo de projeto para<br /><br /> -Participe de roteamento de comando para comandos de projeto.<br />-Adicionar, remover ou desabilitar os comandos de ambiente de projeto e comandos ativos do Gerenciador de soluções.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Permite que o subtipo de projeto filtrar o que o usuário vê na **Adicionar Novo Item** caixa de diálogo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Permite que um subtipo de projeto para<br /><br /> -Determine o gerador de padrão, dado uma extensão de arquivo.<br />-Mapear um nome de gerador legível por humanos para um objeto COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Propriedades usadas por subtipos do projeto  
 O sistema de projeto base e o ambiente pode usar as propriedades de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> enumerações detalhadas na tabela a seguir para habilitar um subtipo de projeto controlar vários recursos do sistema de projeto.  
  
|Propriedade VSHPROPID|Subtipo de projeto|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Permite que um subtipo de projeto controlar o conteúdo a **Adicionar Item** caixa de diálogo. O subtipo de projeto pode fornecer uma nova especificação de diretórios de modelo, adicionar novos tipos de itens, remover itens existentes e reorganizar um subconjunto dos itens do projeto base **Adicionar Item** caixa de diálogo.|  
|`PropertyPagesCLSIDList`|Permite que um subtipo de projeto Adicionar ou remover páginas de propriedades de configuração independente.|  
|`CfgPropertyPagesCLSIDList`|Permite que um subtipo de projeto Adicionar ou remover páginas de propriedades de configuração dependente.|  
|`ExtObjectCATID`|Permite que um subtipo de projeto fornecer um extensor de automação para o projeto ou objetos de item ao conhecer o CATID do extensor. Por exemplo, um subtipo de projeto pode fornecer um personalizado `Project.Extender("<subtype>")` objeto.|  
|`BrowseObjectCATID`|Permite que um subtipo de projeto fornecer um extensor de automação para o `Browse` objeto Conhecendo o CATID do extensor. Por exemplo, um subtipo de projeto pode adicionar propriedades extras para o <xref:EnvDTE.Project.Properties%2A> coleção.|  
|`CfgBrowseObjectCATID`|Permite que um subtipo de projeto fornecer um extensor de automação para o objeto de procura de configuração do projeto. Por exemplo, um subtipo de projeto pode adicionar propriedades extras para o <xref:EnvDTE.Configuration.Properties%2A> coleção.|  
|`CfgExtObjectCATID`|Permite que um subtipo de projeto fornecer um extensor de automação para o objeto de configuração.|  
|`DefaultPlatformName`|Permite que um subtipo de projeto determinar o nome da plataforma para objetos de configuração do projeto.|  
  
 O projeto base fornece uma implementação padrão das propriedades acima. O projeto base obtém essas chamando `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> no subtipo de projeto mais externo, permitindo assim que o subtipo de projeto substituir a implementação das propriedades.  
  
## <a name="see-also"></a>Consulte também  
 [Design de subtipos de projeto](../../extensibility/internals/project-subtypes-design.md)