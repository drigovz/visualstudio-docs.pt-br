---
title: Páginas de propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51487b35686da9676f201a157ddb8e47afb75ce8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725053"
---
# <a name="property-pages"></a>Páginas de propriedade
Os usuários podem exibir e alterar propriedades dependentes de configuração de projeto e independentes usando páginas de propriedades. Um botão **páginas de propriedades** é habilitado na janela **Propriedades** ou na barra de ferramentas Gerenciador de soluções para objetos que fornecem uma exibição de página de propriedades do objeto selecionado. As páginas de propriedades são criadas pelo ambiente e estão disponíveis para soluções e projetos. No entanto, eles também podem ser disponibilizados para itens de projeto que fazem uso de propriedades dependentes de configuração. Esse recurso pode ser usado quando arquivos dentro de um projeto exigem configurações de comutador de compilador diferentes para serem compilados corretamente.

## <a name="using-property-pages"></a>Usando páginas de propriedades
 Se uma página de propriedades já estiver sendo exibida e a seleção for alterada (por exemplo, de uma solução para um projeto), as informações exibidas nas páginas serão alteradas para exibir as propriedades da nova seleção. Se não houver nenhuma propriedade no objeto que ofereça suporte a páginas de propriedades, a página de propriedades estará vazia.

 Se vários objetos forem selecionados, a página de Propriedades exibirá a interseção de propriedades de todos os itens selecionados. Se o item selecionado não contiver propriedades dependentes de configuração e o botão **páginas de propriedades** na barra de ferramentas Gerenciador de soluções for clicado, o foco será alterado para o janela Propriedades. Para obter mais informações relacionadas ao janela Propriedades e à seleção, consulte [estendendo propriedades](../../extensibility/internals/extending-properties.md).

 Se as propriedades forem exibidas para vários objetos e você alterar um valor em uma página de propriedades, todos os valores dos objetos serão definidos para o novo valor, mesmo se forem inicialmente diferentes e a página ficar em branco quando as propriedades de um objeto individual forem exibidas.

 Há dois tipos gerais de caixas de diálogo de **páginas ProjectProperty** disponíveis no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Na primeira, para projetos Visual Basic, por exemplo, as páginas de propriedades são exibidas usando um formato de campo, conforme mostrado na captura de tela a seguir. No segundo, mostrado mais adiante nesta seção, a página de propriedades hospeda uma grade de propriedades semelhante àquela encontrada na janela Propriedades.

 ![Visual Basic páginas de propriedades](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Caixa de diálogo páginas de propriedades do projeto com formato de campo e estrutura de árvore

 A estrutura de árvore na caixa de diálogo páginas de propriedades não é criada usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. O ambiente, com base no nome de nível passado para ele pelo <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> e as interfaces de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>, o compila.

 Há apenas duas categorias de nível superior disponíveis em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] páginas de propriedades:

- Propriedades comuns, que exibe informações independentes de configuração para o objeto ou objetos selecionados. Como resultado, quando uma das subcategorias de propriedades comuns estiver selecionada, as opções configuração, plataforma e Configuration Manager na parte superior da caixa de diálogo não estarão disponíveis.

- Propriedades de configuração, que contêm informações dependentes de configuração relacionadas aos parâmetros de depuração, otimização e compilação para a solução ou o projeto.

  Não é possível criar nenhuma categoria adicional de nível superior, mas você pode optar por não exibir uma ou outra em sua implementação de `IVsPropertyPage`. Se, por exemplo, você não tiver nenhuma propriedade independente de configuração para exibir um objeto, poderá optar por não exibir a categoria de propriedades comuns. Você exibirá Propriedades comuns se `ISpecifyPropertyPages` for implementada do objeto de procura e das propriedades de configuração do item ao implementar `ISpecifyPropertyPages` no objeto de configuração (o objeto que implementa `IVsCfg`, `IVsProjectCfg` e interfaces relacionadas).

  Cada categoria exibida em uma categoria de nível superior representa uma página de propriedades separada. As entradas de categoria e subcategoria disponíveis na caixa de diálogo são determinadas pela implementação de `ISpecifyPropertyPages` e `IVsPropertyPage`.

  `IDispatch` objetos para itens no contêiner de seleção que têm propriedades a serem exibidas em páginas de propriedades implementam `ISpecifyPropertyPages` para enumerar uma lista de IDs de classe. As IDs de classe são passadas como variáveis para `ISpecifyPropertyPages` e são usadas para instanciar as páginas de propriedades. A lista de IDs de classe também é passada para `IVsPropertyPage` para criar a estrutura de árvore à esquerda da caixa de diálogo. As páginas de propriedades passam informações de volta para o objeto `IDispatch` que implementa `ISpecifyPropertyPages` e preenche as informações de cada página.

  As propriedades do objeto de procura são recuperadas usando `IDispatch` para cada objeto no contêiner de seleção.

  A implementação de `Help::DisplayTopicFromF1Keyword` em seu VSPackage fornece a funcionalidade para o botão ajuda.

  Para obter mais informações, consulte `IDispatch` e `ISpecifyPropertyPages`in a biblioteca do MSDN.

  O segundo tipo de páginas de propriedades exibido nos exemplos hospeda uma forma da grade de propriedades, conforme mostrado na captura de tela a seguir.

  ![Páginas de propriedades do vc](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Caixa de diálogo páginas de propriedade com grade de propriedades

  As interfaces `IVSMDPropertyBrowser` e `IVSMDPropertyGrid` (declaradas em vsmanaged. h) são usadas para criar e preencher a grade de propriedades dentro de uma caixa de diálogo ou janela.

  A arquitetura dos projetos mudou consideravelmente das versões anteriores do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Em particular, a noção de qual projeto está ativo foi alterada. No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], não há nenhum conceito de projeto ativo. Em ambientes de desenvolvimento anteriores, o projeto ativo era o projeto que cria e implanta comandos por padrão, independentemente do contexto. Agora, a solução controla e arbitra os comandos de compilação e implantação que se aplicam a quais projetos.

  O que antes era um projeto ativo agora é capturado de uma das três maneiras diferentes:

- O projeto de inicialização

   Você pode especificar um projeto ou projetos da página de propriedades da solução que será iniciada quando o usuário pressionar F5 ou selecionar executar no menu Compilar. Isso funciona de maneira semelhante ao antigo projeto ativo, no sentido de que seu nome é exibido em Gerenciador de Soluções com fonte em negrito.

   Você pode recuperar o projeto de inicialização como uma propriedade no modelo de automação chamando `DTE.Solution.SolutionBuild.StartupProjects`. Em um VSPackage, você chama os métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>. o `IVsSolutionBuildManager` está disponível como um serviço `QueryService` em SID_SVsSolutionBuildManager. Para obter mais informações, consulte configuração do [objeto de configuração do projeto](../../extensibility/internals/project-configuration-object.md) e [solução](../../extensibility/internals/solution-configuration.md).

- Configuração de Build de solução ativa

   o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tem uma configuração de solução ativa, disponível no modelo de automação implementando `DTE.Solution.SolutionBuild.ActiveConfiguration`. Uma configuração de solução é uma coleção que contém uma configuração de projeto para cada projeto na solução (cada projeto pode ter várias configurações, em várias plataformas, com nomes diferentes). Para obter mais informações relacionadas às páginas de propriedades da solução, consulte [configuração da solução](../../extensibility/internals/solution-configuration.md).

- Projeto selecionado no momento

   Implemente o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> para recuperar a hierarquia do projeto e o item do projeto ou itens selecionados. No DTE, você usaria os métodos `SelectedItems.SelectedItem.Project` e `SelectedItems.SelectedItem.ProjectItem`. Há um código de exemplo sob esses cabeçalhos no núcleo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documentos.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md)
- [Objeto de configuração do projeto](../../extensibility/internals/project-configuration-object.md)
- [Configuração da solução](../../extensibility/internals/solution-configuration.md)