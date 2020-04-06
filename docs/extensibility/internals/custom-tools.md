---
title: Ferramentas personalizadas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708954"
---
# <a name="custom-tools"></a>Ferramentas personalizadas
*Ferramentas personalizadas* permitem associar uma ferramenta a um item em um projeto e executar essa ferramenta sempre que o arquivo for salvo. Certas ferramentas personalizadas, às vezes referidas como *geradores de arquivos únicos,* são frequentemente usadas para implementar tradutores que geram código a partir de dados e vice-versa. Por exemplo, geradores de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] arquivos únicos criam código-fonte a partir das *configurações .e* *arquivos .resx.* O código-fonte gerado fornece acesso fortemente digitado aos dados nos arquivos *.settings* e *.resx.* Os [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipos de projetos e os tipos de projeto suportam ferramentas personalizadas; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tipos de projeto não. Seus próprios tipos de projeto também podem suportar ferramentas personalizadas.

 Ferramentas personalizadas são componentes `IVsSingleFileGenerator` registrados que implementam a interface.

 Ferramentas personalizadas estão `ProjectItem` associadas a um objeto de interface e são como designers e editores. Uma ferramenta personalizada pega o `ProjectItem` arquivo representado por uma entrada e grava `DefaultExtension` um novo arquivo cujo nome de arquivo é fornecido pelo método.

## <a name="in-this-section"></a>Nesta seção
- [Implementar geradores de arquivos únicos](../../extensibility/internals/implementing-single-file-generators.md)

 Descreve como usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> a interface para implementar uma ferramenta personalizada.

- [Registre geradores de arquivos únicos](../../extensibility/internals/registering-single-file-generators.md)

 Fornece descrições para todas as entradas de registro para uma ferramenta personalizada.

- [Expor tipos a designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Explica como os sistemas de projeto fornecem suporte para os designers visuais acessarem classes e tipos gerados por meio de arquivos temporários portáteis executáveis (PE).

- [Persistir a propriedade de um item de projeto](../../extensibility/persisting-the-property-of-a-project-item.md)

 Mostra como persistir uma propriedade de item de projeto, como o autor de um arquivo de origem, no arquivo do projeto.

## <a name="reference"></a>Referência
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Fornece detalhes <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>sobre o , que transforma um único arquivo de entrada em um único arquivo de saída que pode ser compilado ou adicionado a um projeto.

 <xref:EnvDTE.ProjectItem>Explica `ProjectItem` a interface, que representa um item em um projeto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Fornece detalhes `DefaultExtension` sobre o método, que recupera a extensão do nome do arquivo que é dada ao nome do arquivo de saída.

## <a name="related-sections"></a>Seções relacionadas
- [Ampliar projetos](../../extensibility/extending-projects.md)

 Descreve como usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos e soluções para organizar arquivos de código e arquivos de recursos e como implementar o controle de origem.
