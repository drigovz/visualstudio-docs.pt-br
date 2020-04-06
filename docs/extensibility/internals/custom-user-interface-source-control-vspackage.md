---
title: Interface de usuário personalizada (Source Control VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708926"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interface de usuário personalizada (controle de origem VSPackage)
Um VSPackage declara seus itens de menu e seus estados padrão através da tabela de comando visual Studio *(.vsct).* O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) exibe os itens do menu em seus estados padrão até que o VSPackage seja carregado. Posteriormente, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> o método é chamado para ativar ou desativar itens do menu.

 Um VSPackage pode definir uma chave de registro para que o VSPackage possa ser carregado automaticamente dependendo de um contexto de interface de usuário de comando (UI), embora normalmente um controle de origem VSPackage deve carregar sob demanda em vez de apenas mudar para um contexto de interface de usuário particular. Para obter mais informações sobre a chave de registro **AutoLoadPackages,** consulte [Gerenciar VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>VSPackage UI
 Um pacote de controle de origem é implementado como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]um VSPackage e não usa nenhuma iu de . Cada controle de origem O VSPackage deve especificar seus próprios elementos de IU, como itens de menu, grupos de menu, janelas de ferramentas, barras de ferramentas e qualquer ui necessária para definir opções específicas para o controle de origem VSPackage. Esses elementos de IU podem ser ativados de forma estática ou dinâmica. Os elementos de IA estático são definidos em um arquivo *.vsct* e são exibidos se o VSPackage está carregado ou não. Elementos de interface do usuário dinâmico podem ser visíveis dependendo de um contexto de interface do usuário de comando específico, como <xref:EnvDTE.Constants.vsContextNoSolution>, ou como resultado de uma chamada para o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. A visibilidade dos elementos de IU dinâmicos está em conformidade com a estratégia de carregamento atrasado de VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>Restrições de IU no controle de origem VSPackages
 Como o controle de origem VSPackage não pode ser removido do IDE depois de carregado, o VSPackage deve ser capaz de entrar em um estado inativo. Quando um VSPackage recebe a notificação de que não está mais ativo, o VSPackage desativa sua interface do iu e ignora qualquer interação externa do IDE. A implementação do método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> do VSPackage deve ocultar comandos quando o VSPackage não estiver ativo.

 Todo controle de origem `IVsSccProvider` VSPackage deve implementar a interface. Dois métodos na <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>e , devem ser implementados pelo VSPackage.

 O controle de origem VSPackage pode ter subscrito vários <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>IDE, que são implementados pelo , e assim por diante. Além disso, o VSPackage pode ter implementado interfaces de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>retorno de chamada habilitadas para registro, como a . Essas interfaces devem ser ignoradas quando inativas.

 A lista a seguir mostra as interfaces afetadas pelo estado ativo de um controle de origem VSPackage:

- Acompanhe os eventos dos documentos do projeto.

- Eventos de solução.

- Interfaces de persistência de soluções. Quando inativo, os pacotes não devem ser regravar para arquivos *.sln* e *.suo.*

- Extensores de propriedades.

  As <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> interfaces necessárias e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, e também quaisquer interfaces opcionais associadas ao controle de origem, não são chamadas quando o controle de origem VSPackage está inativo.

  Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] for iniciado, defina o contexto de interface do dia do comando para o ID do controle de origem padrão atual VSPackage ID. Isso faz com que a ui estática do controle de origem ativa VSPackage apareça no IDE sem realmente carregar o VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pausas para que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> se registre através do antes de fazer quaisquer chamadas para o VSPackage.

  A tabela a seguir descreve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] detalhes específicos sobre como o IDE oculta diferentes itens de IA.

| Item de UI | Descrição |
| - | - |
| Menus e barras de ferramentas | O pacote de controle de origem deve definir os estados iniciais de visibilidade do menu e da barra de ferramentas para o ID do pacote de controle de origem na seção [Restrições](../../extensibility/visibilityconstraints-element.md) de Visibilidade do arquivo *.vsct.* Isso permite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que o IDE defina o estado dos itens do menu adequadamente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> sem carregar o VSPackage e chamar uma implementação do método. |
| Janelas da ferramenta | O controle de origem VSPackage esconde todas as janelas de ferramenta que possui quando é feita inativa. |
| Controle de origem PÁGINAS de opções específicas do VSPacote | A chave de registro **HKLM\SOFTWARE\Microsoft\VisualStudio\X\ToolsOptionsPages\VisibilityCmdUIContexts** permite que um VSPackage defina os contextos nos quais ele requer que suas páginas de opções sejam exibidas. Uma entrada de registro sob esta chave teria que ser criada usando o ID de serviço (SID) do serviço de controle de origem e atribuindo-o um valor DWORD de 1. Sempre que um evento de interface do ui ocorrer em um contexto com o que o controle de origem VSPackage é registrado, o VSPackage será chamado se estiver ativo. |

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Gerenciar VSPackages](../../extensibility/managing-vspackages.md)
