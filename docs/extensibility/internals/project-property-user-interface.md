---
title: Interface do Usuário de Propriedade do Projeto | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706392"
---
# <a name="project-property-user-interface"></a>Interface do usuário de propriedades do projeto

Um subtipo de projeto pode usar os itens na caixa de diálogo Páginas de **propriedade** do projeto à medida que são fornecidos pelo projeto base, ocultar ou fazer controles somente leitura e páginas inteiras conforme fornecido, ou adicionar páginas específicas do projeto à caixa de diálogo Páginas de **propriedade.**

## <a name="extending-the-project-property-dialog-box"></a>Ampliação da caixa de diálogo de propriedade do projeto

Um subtipo de projeto implementa extensores de automação e a configuração do projeto navega por objetos. Esses extensores <xref:EnvDTE.IFilterProperties> implementam a interface para tornar propriedades específicas ocultas ou somente leitura. A caixa de diálogo Páginas de **Propriedade** do projeto base, implementada pelo projeto base, honra a filtragem realizada pelos Extensores de Automação.

O processo de extensão de uma caixa de diálogo **Project Property** é descrito abaixo:

- O projeto base recupera os extensores do subtipo do projeto implementando a <xref:EnvDTE80.IInternalExtenderProvider> interface. A navegação, a automação do projeto e a configuração do projeto navegam objetos do projeto base, implementando essa interface.

- A implementação do objeto de <xref:EnvDTE80.IInternalExtenderProvider> navegação do projeto <xref:EnvDTE80.IInternalExtenderProvider> e o delegado de objetode automação do `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> para a implementação do agregador do subtipo do projeto (ou seja, eles para o objeto do projeto).

- O objeto de navegação de <xref:EnvDTE80.IInternalExtenderProvider> navegação de configuração do projeto base também implementa o fio direto no Extender de automação do objeto de configuração do subtipo do projeto. Sua implementação delega à <xref:EnvDTE80.IInternalExtenderProvider> interface implementada pelo agregador do subtipo do projeto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementado pelo objeto de navegação <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de configuração do projeto, retorna o objeto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, também implementado pelo objeto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> navegação de configuração do projeto, retorna o objeto.

- Um subtipo de projeto pode determinar os CATIDs apropriados para os vários objetos extensíveis do projeto base no tempo de execução, recuperando os seguintes <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valores:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Para determinar os CATIDs para o escopo do projeto, o subtipo do projeto recupera as propriedades acima para [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) do `VSITEMID typedef`. Um subtipo de projeto também pode querer controlar quais páginas de caixa de diálogo Páginas de **propriedade** são exibidas para o projeto, tanto dependente de configuração quanto independente de configuração. Alguns subtipos de projeto podem precisar remover páginas incorporadas e adicionar páginas específicas do subtipo do projeto. Para habilitar isso, o projeto cliente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> gerenciado chama o método para as seguintes propriedades:

- `VSHPROPID_PropertyPagesCLSIDList`— uma lista delimitada de ponto e vírgula de CLSIDs de páginas de propriedade independentes de configuração.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`uma lista delimitada de ponto e vírgula de CLSIDs de páginas de propriedade dependentes de configuração.

Como o subtipo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projeto agrega o objeto, ele pode substituir a definição dessas propriedades para controlar quais caixas de diálogo Páginas de **propriedade** são exibidas. O subtipo do projeto pode recuperar essas propriedades do projeto de base interna e, em seguida, adicionar ou remover CLSIDs conforme necessário.

Novas páginas de propriedade adicionadas por um subtipo de projeto recebem um objeto de navegação de configuração de projeto a partir da implementação do projeto base. Esta configuração do projeto navega objeto suporta extensores de automação. Para obter mais informações sobre extensores de automação, consulte [Implementando e usando extensores de automação](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). As páginas de propriedade implementadas <xref:EnvDTE.Project.Extender%2A> pela chamada do subtipo de projeto para recuperar seu próprio objeto de configuração de subtipo de projeto que amplia o objeto de navegação de configuração do projeto base.

## <a name="see-also"></a>Confira também

- <xref:EnvDTE.IFilterProperties>
- [Caixa de diálogo páginas de propriedade](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
