---
title: Interface do usuário da Propriedade do projeto | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a83e5c9fb633322da536e62f1ba03484b965b162
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252351"
---
# <a name="project-property-user-interface"></a>Interface do usuário de propriedades do projeto

Um subtipo de projeto pode usar os itens na caixa de diálogo **páginas de propriedades** do projeto, pois eles são fornecidos pelo projeto base, ocultar ou fazer controles somente leitura e páginas inteiras conforme fornecido ou adicionar páginas específicas de subtipo de projeto à caixa de diálogo **páginas de propriedades** quadro.

## <a name="extending-the-project-property-dialog-box"></a>Estendendo a caixa de diálogo de propriedades do projeto

Um subtipo de projeto implementa extensores de automação e objetos de procura de configuração de projeto. Esses extensores implementam <xref:EnvDTE.IFilterProperties> a interface para tornar as propriedades específicas ocultas ou somente leitura. A caixa de diálogo **páginas de propriedades** do projeto base, implementada pelo projeto base, honra a filtragem executada pelos extensores de automação.

O processo de estender uma caixa de diálogo de **Propriedades do projeto** é descrito abaixo:

- O projeto base recupera os extensores do subtipo projeto implementando a <xref:EnvDTE80.IInternalExtenderProvider> interface. Os objetos procurar, automação do projeto e configuração do projeto procuram o projeto base todos implementam essa interface.

- A implementação de <xref:EnvDTE80.IInternalExtenderProvider> para o objeto procurar no projeto e o objeto de automação do projeto <xref:EnvDTE80.IInternalExtenderProvider> delegam para a implementação do agregador de subtipo do projeto `QueryInterface` ( <xref:EnvDTE80.IInternalExtenderProvider> ou seja <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , para no objeto Project).

- O objeto de busca de configuração de projeto <xref:EnvDTE80.IInternalExtenderProvider> base também implementa para conectar diretamente o extensor de automação do objeto de configuração de subtipo do projeto. Sua implementação delega para a <xref:EnvDTE80.IInternalExtenderProvider> interface implementada pelo agregador de subtipo de projeto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado pelo objeto de procura de configuração do projeto, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> retorna o objeto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, também implementado pelo objeto Browse de configuração do projeto, retorna <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> o objeto.

- Um subtipo de projeto pode determinar os CATIDs apropriados para os vários objetos extensíveis do projeto base em tempo de execução, recuperando os seguintes <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valores:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Para determinar os CATIDs para o escopo do projeto, o subtipo do projeto recupera as propriedades acima para [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) do `VSITEMID typedef`. Um subtipo de projeto também pode querer controlar quais páginas da caixa de diálogo **páginas de propriedades** são exibidas para o projeto, tanto a configuração dependente quanto a configuração independente. Alguns subtipos de projeto talvez precisem remover páginas internas e adicionar páginas específicas de subtipo de projeto. Para habilitar isso, o projeto cliente gerenciado chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> método para as seguintes propriedades:

- `VSHPROPID_PropertyPagesCLSIDList`— uma lista delimitada por ponto-e-vírgula de CLSIDs de páginas de propriedades independentes de configuração.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`uma lista delimitada por ponto-e-vírgula de CLSIDs de páginas de propriedades dependentes de configuração.

Como o subtipo de projeto agrega o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto, ele pode substituir a definição dessas propriedades para controlar quais caixas de diálogo de **páginas de propriedades** são exibidas. O subtipo do projeto pode recuperar essas propriedades do projeto base interno e, em seguida, adicionar ou remover CLSIDs conforme necessário.

Novas páginas de propriedades adicionadas por um subtipo de projeto são enviadas por um objeto de navegação de configuração de projeto da implementação do projeto base. Este objeto de procura de configuração de projeto dá suporte a extensores de automação. Para obter mais informações sobre o AutomationExtenders, consulte [implementando e usando extensores de automação](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). As páginas de propriedades implementadas pela chamada <xref:EnvDTE.Project.Extender%2A> de subtipo de projeto para recuperar seu próprio projeto de pesquisa de configuração de subtipo, que estende o objeto de procura de configuração do projeto base.

## <a name="see-also"></a>Consulte também

- <xref:EnvDTE.IFilterProperties>
- [Caixa de diálogo páginas de propriedades](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
