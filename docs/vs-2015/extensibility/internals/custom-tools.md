---
title: Ferramentas personalizadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 594d564cf4a18eb0b673abd9b45b7d70e20381b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196914"
---
# <a name="custom-tools"></a>Ferramentas personalizadas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

As *ferramentas personalizadas* permitem associar uma ferramenta a um item em um projeto e executar essa ferramenta sempre que o arquivo é salvo. Algumas ferramentas personalizadas, às vezes chamadas de *geradores de arquivo único*, são usadas frequentemente para implementar tradutores que geram código a partir de dados e vice-versa. Por exemplo, geradores de arquivo único criam [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] código-fonte fora dos arquivos. Settings e. resx. O código-fonte gerado fornece acesso fortemente tipado aos dados nos arquivos. Settings e. resx. Os [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] tipos de projeto e oferecem suporte a ferramentas personalizadas; os [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] tipos de projeto não. Seus próprios tipos de projeto também podem oferecer suporte a ferramentas personalizadas.  
  
 As ferramentas personalizadas são componentes registrados que implementam a `IVsSingleFileGenerator` interface.  
  
 As ferramentas personalizadas são associadas a um `ProjectItem` objeto de interface e são como designers e editores. Uma ferramenta personalizada usa o arquivo representado por um `ProjectItem` como entrada e grava um novo arquivo cujo nome de arquivo é fornecido pelo `DefaultExtension` método.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementando geradores de arquivo único](../../extensibility/internals/implementing-single-file-generators.md)  
 Descreve como usar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface para implementar uma ferramenta personalizada.  
  
 [Determinando o namespace padrão de um projeto](../../misc/determining-the-default-namespace-of-a-project.md)  
 Descreve como determinar o namespace correto com base no idioma que está sendo usado.  
  
 [Registrando geradores de arquivo único](../../extensibility/internals/registering-single-file-generators.md)  
 Fornece descrições para todas as entradas de registro para uma ferramenta personalizada.  
  
 [Expondo tipos para designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explica como os sistemas de projeto oferecem suporte a designers visuais para acessar classes e tipos gerados por meio de arquivos executáveis temporários (PE).  
  
 [Manter a propriedade de um item de projeto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Mostra como manter uma propriedade de item de projeto, como o autor de um arquivo de origem, no arquivo de projeto.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Fornece detalhes sobre o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , que transforma um único arquivo de entrada em um único arquivo de saída que pode ser compilado ou adicionado a um projeto.  
  
 <xref:EnvDTE.ProjectItem>  
 Explica a `ProjectItem` interface, que representa um item em um projeto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Fornece detalhes sobre o `DefaultExtension` método, que recupera a extensão de nome de arquivo que é fornecida ao nome do arquivo de saída.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Estender projetos](../../extensibility/extending-projects.md)  
 Descreve como usar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projetos e soluções para organizar arquivos de código e arquivos de recursos e como implementar o controle do código-fonte.
