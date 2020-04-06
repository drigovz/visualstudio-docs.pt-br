---
title: Propriedades e métodos estendidos por subtipos de projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706203"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propriedades e métodos estendidos por subtipos de projeto
Um subtipo de projeto tem muito poder para influenciar o comportamento do projeto porque ele é construído como um agregador de um projeto base. Esta seção resume alguns dos recursos que podem ser aprimorados ou modificados por subtipos de projeto.

## <a name="features-gained-by-aggregation"></a>Características adquiridas pela Agregação
 A tabela a seguir resume muitos dos métodos que a agregação permite que os subtipos do projeto se sobreponham em projetos base.

|Métodos substituídos pela Agregação|Subtipo do projeto|
|---------------------------------------|---------------------|
|De: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Habilita um subtipo de projeto para<br /><br /> - Alterar legenda e ícone do nó do projeto.<br />- Anular completamente `Browse` o objeto do projeto.<br />- Controle se o projeto pode ser renomeado.<br />- Ordem de classificação de controle.<br />- Controle o contexto do usuário para ajuda dinâmica.|
|De: <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permite que um subtipo de projeto controle quais serviços contextuais são fornecidos a designers e editores.|
|De: <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Habilita um subtipo de projeto para<br /><br /> - Participe do roteamento de comando para comandos de projeto.<br />- Adicionar, remover ou desativar os comandos ambiente do projeto e os comandos ativos do Solution Explorer.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Habilita o subtipo do projeto para filtrar o que o usuário vê na caixa de diálogo **Adicionar novo item.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Habilita um subtipo de projeto para<br /><br /> - Determine o gerador padrão dada uma extensão de arquivo.<br />- Mapeie um nome gerador humano legível para um objeto COM.|

## <a name="properties-used-by-project-subtypes"></a>Propriedades usadas pelos subtipos do projeto
 O ambiente e o sistema de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> projeto base podem usar as propriedades a partir e enumerações detalhadas na tabela a seguir para permitir que um subtipo de projeto controle vários recursos do sistema de projeto.

|Propriedade VSHPROPID|Subtipo do projeto|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Permite que um subtipo de projeto controle o conteúdo da caixa de diálogo **Adicionar item.** O subtipo do projeto pode fornecer uma nova especificação dos diretórios de modelos, adicionar novos tipos de itens, remover itens existentes e reorganizar um subconjunto dos itens na caixa de diálogo **Adicionar item** do projeto base.|
|`PropertyPagesCLSIDList`|Permite que um subtipo de projeto adicione ou remova páginas de propriedade independentes de configuração.|
|`CfgPropertyPagesCLSIDList`|Permite que um subtipo de projeto adicione ou remova páginas de propriedade dependentes da configuração.|
|`ExtObjectCATID`|Permite que um subtipo de projeto forneça um Extensor de Automação para objetos de itens de projeto ou projeto, conhecendo o Extender CATID. Por exemplo, um subtipo de `Project.Extender("<subtype>")` projeto pode fornecer um objeto personalizado.|
|`BrowseObjectCATID`|Permite que um subtipo de projeto `Browse` forneça um Extensor de Automação para o objeto conhecendo o Extender CATID. Por exemplo, um subtipo de projeto <xref:EnvDTE.Project.Properties%2A> pode adicionar propriedades extras à coleção.|
|`CfgBrowseObjectCATID`|Permite que um subtipo de projeto forneça um Extendador de Automação para a configuração do projeto. Por exemplo, um subtipo de projeto <xref:EnvDTE.Configuration.Properties%2A> pode adicionar propriedades extras à coleção.|
|`CfgExtObjectCATID`|Permite que um subtipo de projeto forneça um extensor de automação para o objeto de configuração.|
|`DefaultPlatformName`|Permite que um subtipo de projeto determine o nome da plataforma para os objetos de configuração do projeto.|

 O projeto base fornece uma implementação padrão das propriedades acima. O projeto base obtém-os solicitando `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o subtipo do projeto mais externo, permitindo assim que o subtipo do projeto sobreponha a implementação das propriedades.

## <a name="see-also"></a>Confira também
- [Design de subtipos de projeto](../../extensibility/internals/project-subtypes-design.md)
