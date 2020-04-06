---
title: Objeto de configuração do projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706652"
---
# <a name="project-configuration-object"></a>Objeto de configuração de projeto
O objeto de configuração do projeto gerencia a exibição de informações de configuração para a ui.

 ![Configuração do projeto visual studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Páginas de propriedade de configuração de projeto

 O Provedor de Configuração de Projeto gerencia as configurações do projeto. O ambiente e outros pacotes, para obter acesso e recuperar informações sobre as configurações de um projeto, ligue para as interfaces anexadas ao objeto Project Configuration Provider.

> [!NOTE]
> Você não pode criar ou editar arquivos de configuração de solução programáticamente. É necessário usar `DTE.SolutionBuilder`. Consulte [Configuração da solução](../../extensibility/internals/solution-configuration.md) para obter mais informações.

 Para publicar um nome de exibição a ser usado <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>na ia de configuração, seu projeto deve implementar . O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>chama , que `IVsCfg` retorna uma lista de ponteiros que você pode usar para obter os nomes de exibição para as informações de configuração e plataforma a serem listados na ui do ambiente. A configuração ativa e a plataforma são determinadas pela configuração do projeto armazenada na configuração da solução ativa. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> método pode ser usado para recuperar a configuração ativa do projeto.

 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> objeto pode ser implementado <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> opcionalmente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> no objeto com `IVsProjectCfg2` o objeto para permitir que você recupere um objeto com base no nome de configuração do projeto canônico.

 Outra forma de fornecer ao ambiente e a outros projetos acesso às `IVsCfgProvider2::GetCfgs` configurações do projeto é que os projetos forneçam uma implementação do método para devolver um ou mais objetos de configuração. Os projetos também <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>podem implementar `IVsProjectCfg` , que `IVsCfg`herda de e, portanto, de - para fornecer informações específicas de configuração. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>suporta plataformas e funcionalidades para adicionar, excluir e renomear configurações de projeto.

> [!NOTE]
> Como o Visual Studio não está mais limitado a dois tipos de configuração, o código que processa configurações não deve ser escrito com suposições sobre o número de configurações, nem deve ser escrito com a suposição de que um projeto que tenha apenas uma configuração é necessariamente Debug ou Retail. Isso torna o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> uso e obsoleto.

 Chamando `QueryInterface` o objeto`IVsGetCfgProvider::GetCfgProvider` devolvido `IVsCfgProvider2`de recuperações . Se `IVsGetCfgProvider` não for `QueryInterface` encontrado `IVsProject3` chamando o objeto do projeto, `QueryInterface` você pode acessar o objeto do provedor `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`de configuração chamando o objeto `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`do navegador raiz hierárquico para o objeto retornado para , ou através de um ponteiro para o provedor de configuração retornado para .

 `IVsProjectCfg2`fornece principalmente acesso a objetos de gerenciamento de compilação, depuração e implantação e permite aos projetos a liberdade de agrupar saídas. Os métodos `IVsProjectCfg` `IVsProjectCfg2` e podem ser <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> usados para implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> para gerenciar o processo de compilação e ponteiros para os grupos de saída de uma configuração.

 O projeto deve retornar o mesmo número de grupos para cada configuração que ele suporta, embora o número de saídas contidas em um grupo possa variar de configuração para configuração. Os grupos também devem ter as mesmas informações de identificador (nome canônico, nome de exibição e informações de grupo) desde a configuração até a configuração dentro de um projeto. Para obter mais informações, consulte [Configuração do projeto para saída](../../extensibility/internals/project-configuration-for-output.md).

 Para habilitar a depuração, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>suas configurações devem implementar . `IVsDebuggableProjectCfg`é uma interface opcional implementada por projetos para permitir que o depurador `IVsCfg` `IVsProjectCfg`inicie uma configuração e é implementada no objeto de configuração com e . O ambiente o chama quando o usuário opta por iniciar o depurador pressionando F5.

 `ISpecifyPropertyPages`e `IDispatch` são usados em conjunto com páginas de propriedade para recuperar e exibir informações dependentes da configuração ao usuário. Para obter mais informações, consulte [Páginas de propriedade](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Confira também
- [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md)
- [Configuração de projeto para compilar](../../extensibility/internals/project-configuration-for-building.md)
- [Configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md)
- [Páginas de propriedades](../../extensibility/internals/property-pages.md)
- [Configuração da solução](../../extensibility/internals/solution-configuration.md)
