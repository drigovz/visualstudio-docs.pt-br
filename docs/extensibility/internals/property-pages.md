---
title: Páginas de Propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706051"
---
# <a name="property-pages"></a>Páginas de propriedade
Os usuários podem visualizar e alterar propriedades dependentes e independentes da configuração do projeto usando páginas de propriedade. Um botão **Páginas de propriedade** está ativado na janela **Propriedades** ou na barra de ferramentas do Solution Explorer para objetos que fornecem uma exibição de página de propriedade do objeto selecionado. As páginas de propriedade são criadas pelo ambiente e estão disponíveis para soluções e projetos. Eles podem, no entanto, também ser disponibilizados para itens de projeto que fazem uso de propriedades dependentes de configuração. Esse recurso pode ser usado quando arquivos dentro de um projeto requerem diferentes configurações do switch compilador para serem construídos corretamente.

## <a name="using-property-pages"></a>Usando páginas de propriedades
 Se uma página de propriedade já estiver exibida e a seleção for alterada (por exemplo, de uma solução para um projeto), as informações exibidas nas páginas serão exibidas para exibir as propriedades para a nova seleção. Se não houver propriedades no objeto que suporta páginas de propriedade, a página da propriedade está vazia.

 Se vários objetos forem selecionados, a página de propriedade exibirá a intersecção de propriedades para todos os itens selecionados. Se o item selecionado não contiver propriedades dependentes da configuração e o botão **Páginas de propriedade** na barra de ferramentas do Solution Explorer for clicado, o foco será alterado na janela Propriedades. Para obter mais informações relacionadas à janela e seleção propriedades, consulte [Propriedades de extensão](../../extensibility/internals/extending-properties.md).

 Se as propriedades forem exibidas para vários objetos e você alterar um valor em uma página de propriedade, todos os valores para os objetos serão definidos para o novo valor, mesmo que fossem inicialmente diferentes e a página estivesse em branco quando as propriedades de um objeto individual fossem exibidas.

 Existem dois tipos gerais de caixas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de diálogo **ProjectProperty Pages** disponíveis em . No primeiro, para projetos Visual Basic, por exemplo, as páginas de propriedade são exibidas usando um formato de campo, como mostrado na captura de tela a seguir. Na segunda, mostrada mais tarde nesta seção, a página de propriedade hospeda uma grade de propriedades semelhante à encontrada na Janela propriedades.

 ![Páginas de propriedade básicas visuais](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Caixa de diálogo Páginas de propriedade do projeto com formato de campo e estrutura de árvore

 A estrutura da árvore na caixa de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>diálogo Páginas de propriedade não é construída usando . O ambiente, baseado no nome de <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> nível <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> passado a ele pelas interfaces, o constrói.

 Existem apenas duas categorias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nível superior disponíveis nas páginas de Propriedade:

- Propriedades comuns, que exibe informações independentes de configuração para o objeto ou objeto selecionado. Como resultado, quando uma das subcategorias Propriedades Comuns é selecionada, as opções Configuração, Plataforma e Gerenciador de Configuração na parte superior da caixa de diálogo não estão disponíveis.

- Propriedades de configuração, que contém informações dependentes da configuração relacionadas a parâmetros de depuração, otimização e construção para a solução ou projeto.

  Você não pode criar nenhuma categoria de nível superior adicional, mas você pode `IVsPropertyPage`optar por não exibir uma ou outra na sua implementação de . Se, por exemplo, você não tiver nenhuma propriedade independente de configuração para exibir um objeto, você pode optar por não exibir a categoria Propriedades Comuns. Você exibe propriedades `ISpecifyPropertyPages` comuns se for implementada a partir do `ISpecifyPropertyPages` objeto de navegação do item e propriedades de configuração quando você implementa no objeto de configuração (a implementação `IVsCfg`do objeto , `IVsProjectCfg`e interfaces relacionadas).

  Cada categoria exibida em uma categoria de nível superior representa uma página de propriedade separada. As entradas de categoria e subcategoria disponíveis na `ISpecifyPropertyPages` `IVsPropertyPage`caixa de diálogo são determinadas pela sua implementação e .

  `IDispatch`objetos para itens no recipiente de seleção que têm `ISpecifyPropertyPages` propriedades a serem exibidas nas páginas de propriedade implementam para enumerar uma lista de IDs de classe. Os IDs de classe são `ISpecifyPropertyPages` passados como variáveis e são usados para instanciar as páginas de propriedade. A lista de IDs de `IVsPropertyPage` classe também é passada para criar a estrutura da árvore à esquerda da caixa de diálogo. As páginas de propriedade então `IDispatch` repassam `ISpecifyPropertyPages` informações para o objeto que implementa e preenche as informações de cada página.

  As propriedades do objeto de `IDispatch` navegação são recuperadas usando para cada objeto no recipiente de seleção.

  A `Help::DisplayTopicFromF1Keyword` implementação no vsPackage fornece a funcionalidade para o botão Ajuda.

  Para mais informações, consulte `IDispatch` e `ISpecifyPropertyPages`na biblioteca DoMSDN.

  O segundo tipo de páginas de propriedade exibidas nas amostras hospeda uma forma da grade de propriedades, como mostrado na captura de tela a seguir.

  ![Páginas de propriedade de VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Caixa de diálogo Páginas de propriedade com grade de propriedades

  As `IVSMDPropertyBrowser` interfaces `IVSMDPropertyGrid` e (declaradas em vsmanaged.h) são usadas para criar e preencher a grade de propriedades dentro de uma caixa de diálogo ou janela.

  A arquitetura dos projetos mudou consideravelmente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]em relação às versões passadas de . Em particular, a noção de qual projeto está ativo mudou. Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], não há conceito de um projeto ativo. Em ambientes de desenvolvimento anteriores, o projeto ativo era o projeto que a construção e a implantação de comandos seria padrão independentemente do contexto. Agora, os controles e arbitrais da solução que constroem e implantam comandos aplicam-se a quais projetos.

  O que antes era um projeto ativo agora é capturado de uma das três maneiras diferentes:

- O projeto Startup

   Você pode especificar um projeto ou projetos da página de propriedade da solução que será iniciada quando o usuário pressionar F5 ou selecionar Executar no menu Construir. Isso funciona de forma semelhante ao antigo projeto ativo no sentido de que seu nome é exibido no Solution Explorer com fonte em negrito.

   Você pode recuperar o projeto de inicialização `DTE.Solution.SolutionBuild.StartupProjects`como uma propriedade no modelo de automação chamando . Em um VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> você <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> chama os métodos. `IVsSolutionBuildManager`está disponível como `QueryService` um serviço por SID_SVsSolutionBuildManager. Para obter mais informações, consulte [Project Configuration Object](../../extensibility/internals/project-configuration-object.md) and Solution [Configuration](../../extensibility/internals/solution-configuration.md).

- Configuração ativa de compilação de soluções

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tem uma configuração de solução ativa, `DTE.Solution.SolutionBuild.ActiveConfiguration`disponível no modelo de automação por meio da implementação . Uma configuração de solução é uma coleção que contém uma configuração de projeto para cada projeto na solução (cada projeto pode ter várias configurações, em várias plataformas, com nomes diferentes). Para obter mais informações relacionadas às páginas de propriedade da solução, consulte [Configuração da solução](../../extensibility/internals/solution-configuration.md).

- Projeto atualmente selecionado

   Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> o método para recuperar a hierarquia do projeto e o item do projeto ou itens selecionados. Da DTE, você `SelectedItems.SelectedItem.Project` usaria `SelectedItems.SelectedItem.ProjectItem` os métodos. Há código de amostra sob esses [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] títulos nos documentos principais.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md)
- [Objeto de configuração de projeto](../../extensibility/internals/project-configuration-object.md)
- [Configuração da solução](../../extensibility/internals/solution-configuration.md)
