---
title: Ferramentas personalizadas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8b18ee5c1c84b8e6480ffa9f91f739796f0991
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834406"
---
# <a name="custom-tools"></a>Ferramentas personalizadas
*Ferramentas personalizadas* permitem que você associe uma ferramenta de um item em um projeto e executar essa ferramenta, sempre que o arquivo é salvo. Determinadas ferramentas personalizadas, também conhecido como *geradores de arquivo único*, costumam ser usados para implementar os tradutores que geram código de dados e vice-versa. Por exemplo, criar geradores de arquivo único [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] código fora da fonte a *Settings* e *. resx* arquivos. O código-fonte gerado fornece acesso fortemente tipado aos dados na *. Settings* e *resx* arquivos. O [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ferramentas personalizadas; dar suporte a tipos de projeto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tipos de projeto não fizer isso. Seus próprios tipos de projeto também podem dar suporte a ferramentas personalizadas.  
  
 Ferramentas personalizadas são registrados componentes que implementam o `IVsSingleFileGenerator` interface.  
  
 Ferramentas personalizadas são associadas com um `ProjectItem` objeto de interface e são como os designers e editores. Uma ferramenta personalizada utiliza o arquivo representado por um `ProjectItem` como entrada e grava um novo arquivo cujo nome de arquivo é fornecido pelo `DefaultExtension` método.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementar geradores de arquivo único](../../extensibility/internals/implementing-single-file-generators.md)  
 Descreve como usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface para implementar uma ferramenta personalizada.  
  
 [Registrar geradores de arquivo único](../../extensibility/internals/registering-single-file-generators.md)  
 Fornece descrições para todas as entradas do registro para uma ferramenta personalizada.  
  
 [Expor tipos aos designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explica como sistemas de projeto fornecem suporte para designers visuais para classes de acesso gerado e tipos por meio de arquivos temporários PE (executável portátil).  
  
 [Manter a propriedade de um item de projeto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Mostra como manter uma propriedade de item de projeto, como o autor de um arquivo de origem, no arquivo de projeto.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Fornece detalhes sobre o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, que transforma um único arquivo de entrada em um arquivo de saída única que pode ser compilado ou adicionado a um projeto.  
  
 <xref:EnvDTE.ProjectItem>  
 Explica o `ProjectItem` interface, que representa um item em um projeto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Fornece detalhes sobre o `DefaultExtension` método, que recupera a extensão de nome de arquivo que é fornecida para o nome do arquivo de saída.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Estender projetos](../../extensibility/extending-projects.md)  
 Descreve como usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos e soluções para organizar os arquivos de código e arquivos de recurso e como implementar o controle do código-fonte.