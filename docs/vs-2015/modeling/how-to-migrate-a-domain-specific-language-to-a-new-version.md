---
title: Como migrar uma linguagem específica de domínio para uma nova versão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45f7b38f7dbb6ea470b2d9e186dc8e6bf4b33b1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657335"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Como migrar uma linguagem específica do domínio para uma nova versão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode migrar projetos que definem e usam a linguagem específica de domínio para a [!INCLUDE[vs2010](../includes/vs2010-md.md)] partir da versão do [!INCLUDE[dsl](../includes/dsl-md.md)] que foi distribuída com o [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] .

 Uma ferramenta de migração é fornecida como parte do [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)] . A ferramenta converte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projetos e soluções que usam ou definem ferramentas DSL.

 Você deve executar a ferramenta de migração explicitamente: ela não é iniciada automaticamente quando você abre uma solução no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . A ferramenta e o documento de orientação detalhada podem ser encontrados neste caminho:

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Antes de migrar seus projetos de DSL
 A ferramenta de migração modifica [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] arquivos de projeto (**. csproj**) e arquivos de solução (**. sln**).

#### <a name="to-prepare-projects-for-migration"></a>Para preparar projetos para migração.

- Verifique se os arquivos **. csproj** e **. sln** podem ser gravados. Se eles estiverem sob controle do código-fonte, verifique se eles estão com check-out.

- Faça uma cópia das pastas que você pretende migrar.

## <a name="migrating-a-collection-of-projects"></a>Migrando uma coleção de projetos

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Para migrar projetos e soluções de DSL para o Visual Studio 2010

1. Inicie a ferramenta de migração de DSL.

   - Você pode clicar duas vezes na ferramenta no Windows Explorer (ou explorador de arquivos) ou iniciar a ferramenta em um prompt de comando. A ferramenta está neste local:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Escolha uma pasta que contenha soluções e projetos que você deseja converter.

   - Insira o caminho na caixa na parte superior da ferramenta ou clique em **procurar**.

     A ferramenta de migração exibe uma árvore de projetos que definem ou usam DSLs. A árvore inclui todos os projetos que usam os assemblies **Microsoft. VisualStudio. Modeling. SDK** ou **TextTemplating** .

3. Examine a árvore de projetos e desmarque os projetos que você não deseja converter.

   - Selecione um projeto ou solução para ver uma lista de alterações que a ferramenta fará.

       > [!NOTE]
       > As caixas de seleção que aparecem ao lado de nomes de pasta não têm nenhum efeito. Você deve expandir as pastas para inspecionar os projetos e as soluções.

4. Converta os projetos.

   1. Clique em **converter**.

        Antes de cada arquivo de projeto ser convertido, uma cópia de _Project_**. csproj** é salva como _Project_**. VS2008. csproj**

        Uma cópia de cada _solução_**. sln** é salva como _Solution_**. VS2008. sln**

   2. Investigue todas as conversões com falha que são relatadas.

        As falhas são relatadas na janela de texto. Além disso, o modo de exibição de árvore mostra um sinalizador vermelho em cada nó que falhou ao converter. Você pode clicar no nó para obter mais informações sobre essa falha.

5. **Transforme todos os modelos** em soluções que contenham projetos convertidos com êxito.

   1. Abra a solução.

   2. Clique no botão **transformar todos os modelos** no cabeçalho de Gerenciador de soluções.

       > [!NOTE]
       > Você pode tornar essa etapa desnecessária. Para obter mais informações, consulte [como automatizar a transformação de todos os modelos](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6. Atualize seu código personalizado nos projetos convertidos.

   - Tente compilar os projetos e investigue as falhas.

   - Teste seu designer.

## <a name="see-also"></a>Consulte Também
 [Novidades no SDK de Visualização e Modelagem](../misc/what-s-new-in-visualization-and-modeling-sdk.md)
