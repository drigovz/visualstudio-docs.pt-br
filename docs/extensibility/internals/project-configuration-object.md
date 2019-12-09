---
title: Objeto de configuração do projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725832"
---
# <a name="project-configuration-object"></a>Objeto de configuração de projeto
O objeto de configuração do projeto gerencia a exibição de informações de configuração para a interface do usuário.

 ![Configuração de projeto do Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Páginas de propriedades de configuração do projeto

 O provedor de configuração do projeto gerencia as configurações do projeto. O ambiente e outros pacotes, para obter acesso e recuperar informações sobre as configurações de um projeto, chame as interfaces anexadas ao objeto de provedor de configuração de projeto.

> [!NOTE]
> Você não pode criar ou editar arquivos de configuração de solução programaticamente. Você deve usar `DTE.SolutionBuilder`. Consulte [configuração da solução](../../extensibility/internals/solution-configuration.md) para obter mais informações.

 Para publicar um nome de exibição a ser usado na interface do usuário de configuração, seu projeto deve implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. O ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, que retorna uma lista de ponteiros de `IVsCfg` que você pode usar para obter os nomes de exibição das informações de configuração e plataforma a serem listadas na interface do usuário do ambiente. A configuração e a plataforma ativas são determinadas pela configuração do projeto armazenada na configuração da solução ativa. O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> pode ser usado para recuperar a configuração do projeto ativo.

 O objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> pode, opcionalmente, ser implementado no objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> com o objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> para permitir que você recupere um objeto `IVsProjectCfg2` com base no nome de configuração do projeto canônico.

 Outra maneira de fornecer o ambiente e outros projetos com acesso às configurações do projeto é que os projetos forneçam uma implementação do método `IVsCfgProvider2::GetCfgs` para retornar um ou mais objetos de configuração. Os projetos também podem implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, que herda de `IVsProjectCfg` e, portanto, de `IVsCfg`, para fornecer informações específicas de configuração. o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> dá suporte a plataformas e funcionalidade para adicionar, excluir e renomear configurações de projeto.

> [!NOTE]
> Como o Visual Studio não está mais limitado a dois tipos de configuração, o código que processa as configurações não deve ser escrito com suposições sobre o número de configurações, nem deve ser escrito com a suposição de que um projeto tenha apenas um a configuração é necessariamente depuração ou varejo. Isso faz com que o uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsoleto.

 Chamar `QueryInterface` no objeto retornado de `IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2`. Se `IVsGetCfgProvider` não for encontrado chamando `QueryInterface` no objeto de projeto `IVsProject3`, você poderá acessar o objeto de provedor de configuração chamando `QueryInterface` no objeto de navegador raiz de hierarquia para o objeto retornado para `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` ou por meio de um ponteiro para a configuração provedor retornado para `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.

 o `IVsProjectCfg2` fornece principalmente acesso a objetos de gerenciamento de compilação, depuração e implantação e permite aos projetos a liberdade de agrupar saídas. Os métodos de `IVsProjectCfg` e `IVsProjectCfg2` podem ser usados para implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> para gerenciar o processo de compilação e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> ponteiros para os grupos de saída de uma configuração.

 O projeto deve retornar o mesmo número de grupos para cada configuração que ele suporta, embora o número de saídas contidas em um grupo possa variar de configuração para configuração. Os grupos também devem ter as mesmas informações de identificador (nome canônico, nome de exibição e informações de grupo) da configuração para a configuração em um projeto. Para obter mais informações, consulte [configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md).

 Para habilitar a depuração, suas configurações devem implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` é uma interface opcional implementada por projetos para permitir que o depurador inicie uma configuração e seja implementado no objeto de configuração com `IVsCfg` e `IVsProjectCfg`. O ambiente o chama quando o usuário opta por iniciar o depurador pressionando F5.

 `ISpecifyPropertyPages` e `IDispatch` são usados em conjunto com páginas de propriedades para recuperar e exibir informações dependentes de configuração para o usuário. Para obter mais informações, consulte [páginas de propriedades](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Consulte também
- [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md)
- [Configuração do projeto para compilação](../../extensibility/internals/project-configuration-for-building.md)
- [Configuração do projeto para saída](../../extensibility/internals/project-configuration-for-output.md)
- [Páginas de propriedade](../../extensibility/internals/property-pages.md)
- [Configuração da solução](../../extensibility/internals/solution-configuration.md)