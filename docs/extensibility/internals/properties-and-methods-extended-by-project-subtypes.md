---
title: Propriedades e métodos estendidos por subtipos de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f5f67ac70b7ca6d5151a9115f20be88f6984d52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725341"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propriedades e métodos estendidos por subtipos de projeto
Um subtipo de projeto tem muita potência para influenciar o comportamento do projeto, pois ele é construído como um agregador de um projeto base. Esta seção resume alguns dos recursos que podem ser aprimorados ou modificados por subtipos de projeto.

## <a name="features-gained-by-aggregation"></a>Recursos obtidos pela agregação
 A tabela a seguir resume muitos dos métodos que a agregação permite que os subtipos de projeto sejam substituídos em projetos base.

|Métodos substituídos por agregação|Subtipo de projeto|
|---------------------------------------|---------------------|
|De <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Habilita um subtipo de projeto para<br /><br /> -Alterar a legenda e o ícone do nó do projeto.<br />-Substituir completamente o objeto `Browse` do projeto.<br />-Controlar se o projeto pode ser renomeado.<br />-Ordem de classificação de controle.<br />-Controle o contexto do usuário para obter ajuda dinâmica.|
|De <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Habilita um subtipo de projeto para controlar quais serviços contextuais são fornecidos aos designers e editores.|
|De <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Habilita um subtipo de projeto para<br /><br /> -Participar do comando roteamento de comandos de projeto.<br />-Adicionar, remover ou desabilitar os comandos de ambiente do projeto e Gerenciador de Soluções comandos ativos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Habilita o subtipo de projeto para filtrar o que o usuário vê na caixa de diálogo **Adicionar novo item** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Habilita um subtipo de projeto para<br /><br /> -Determinar o gerador padrão fornecido por uma extensão de arquivo.<br />-Mapeie um nome de gerador legível por humanos para um objeto COM.|

## <a name="properties-used-by-project-subtypes"></a>Propriedades usadas por subtipos de projeto
 O ambiente e o sistema de projeto base podem usar as propriedades de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> enumerações detalhadas na tabela a seguir para habilitar um subtipo de projeto para controlar vários recursos do sistema de projeto.

|Propriedade VSHPROPID|Subtipo de projeto|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Permite que um subtipo de projeto controle o conteúdo da caixa de diálogo **Adicionar item** . O subtipo de projeto pode fornecer uma nova especificação de diretórios de modelo, adicionar novos tipos de itens, remover itens existentes e reorganizar um subconjunto dos itens na caixa de diálogo **Adicionar item** do projeto base.|
|`PropertyPagesCLSIDList`|Permite que um subtipo de projeto adicione ou remova páginas de propriedades independentes de configuração.|
|`CfgPropertyPagesCLSIDList`|Permite que um subtipo de projeto adicione ou remova páginas de propriedades dependentes de configuração.|
|`ExtObjectCATID`|Permite que um subtipo de projeto forneça um extensor de automação para os objetos de projeto ou item de projeto sabendo o CATID do extensor. Por exemplo, um subtipo de projeto pode fornecer um objeto de `Project.Extender("<subtype>")` personalizado.|
|`BrowseObjectCATID`|Permite que um subtipo de projeto forneça um extensor de automação para o objeto `Browse` sabendo o CATID do extensor. Por exemplo, um subtipo de projeto pode adicionar propriedades extras à coleção de <xref:EnvDTE.Project.Properties%2A>.|
|`CfgBrowseObjectCATID`|Permite que um subtipo de projeto forneça um extensor de automação para o objeto de procura de configuração de projeto. Por exemplo, um subtipo de projeto pode adicionar propriedades extras à coleção de <xref:EnvDTE.Configuration.Properties%2A>.|
|`CfgExtObjectCATID`|Permite que um subtipo de projeto forneça um extensor de automação para o objeto de configuração.|
|`DefaultPlatformName`|Permite que um subtipo de projeto determine o nome da plataforma para os objetos de configuração do projeto.|

 O projeto base fornece uma implementação padrão das propriedades acima. O projeto base Obtém esses dados chamando `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> no subtipo de projeto mais externo, permitindo assim que o subtipo do projeto substitua a implementação das propriedades.

## <a name="see-also"></a>Consulte também
- [Design de subtipos de projeto](../../extensibility/internals/project-subtypes-design.md)