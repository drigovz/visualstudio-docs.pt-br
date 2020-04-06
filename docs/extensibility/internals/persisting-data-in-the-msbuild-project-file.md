---
title: Dados persistentes no arquivo do projeto MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706691"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Mantendo os dados no arquivo de projeto do MSBuild
Um subtipo de projeto pode precisar persistir dados específicos do subtipo no arquivo do projeto para uso posterior. Um subtipo de projeto usa a persistência do arquivo de projeto para atender aos seguintes requisitos:

1. Persistir dados usados como parte da construção do projeto. (Para obter mais informações sobre o Microsoft Build Engine, consulte [MSBuild](../../msbuild/msbuild.md).) As informações relacionadas à compilação podem:

    1. Dados independentes de configuração. Ou seja, dados armazenados em elementos mSBuild com condições em branco ou ausentes.

    2. Dados dependentes da configuração. Ou seja, dados armazenados em elementos do MSBuild que estão condicionados para uma configuração específica do projeto. Por exemplo:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Persista dados que não são relevantes para serem construídos. Esses dados podem ser expressos em XML de forma livre que não é validado contra um esquema XML.

    1. Dados independentes de configuração.

    2. Dados dependentes da configuração.

## <a name="persisting-build-related-information"></a>Informações persistentes relacionadas à compilação
 A persistência de dados úteis para a construção de um projeto é tratada através do MSBuild. O sistema MSBuild mantém uma tabela mestre de informações relacionadas à compilação. Os subtipos do projeto são responsáveis por acessar esses dados para obter e definir valores de propriedade. Os subtipos do projeto também podem aumentar a tabela de dados relacionada à compilação adicionando propriedades adicionais a serem persistidas e removendo propriedades para que elas não sejam persistidas.

 Para modificar os dados do MSBuild, um subtipo de projeto é responsável por <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>recuperar o objeto de propriedade MSBuild do sistema de projeto base através de . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>é uma interface implementada no sistema de projeto principal e nas consultas `QueryInterface`de subtipo de projeto agregador para ele executando .

 O procedimento a seguir descreve as etapas para a remoção de um imóvel usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Para remover uma propriedade de um arquivo de projeto MSBuild

1. Chamada `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> do subtipo do projeto.

2. Ligue <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` com set para a propriedade que deseja remover.

### <a name="persisting-non-build-related-information"></a>Informações não relacionadas à não-compilação persistentes
 A persistência de dados em arquivos de projeto que <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>não importam para construir é tratada através de .

 Você pode <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementar `project subtype aggregator` no objeto `project subtype project configuration` principal, no objeto ou ambos.

 Os pontos a seguir descrevem os principais conceitos em relação à persistência de informações não-construídas.

- O projeto base solicita o subtipo principal do projeto (ou seja, o subtipo de projeto mais externo) para carregar e salvar dados independentes de configuração, e ele solicita que os objetos de configuração do projeto do subtipo do projeto carreguem ou salvem dados dependentes da configuração.

- O projeto base chama <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> os métodos de várias vezes para cada nível de agregação de subtipo de projeto e passa o GUID para cada nível.

- O projeto base passa ou recebe um fragmento XML que é dedicado a um subtipo de projeto específico e usa esse mecanismo como uma forma de estado de persistência entre os níveis de agregação.

- O projeto base chama a implementação <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>do subtipo de projeto externo passando em um GUID. Se o GUID pertence ao subtipo de projeto externo, ele lida com a chamada em si; caso contrário, ele delega a chamada para um subtipo de projeto interno, e assim por diante, até que o subtipo do projeto que o GUID corresponda seja encontrado.

- Um subtipo de projeto também pode modificar o fragmento XML antes ou depois de delegar a chamada para um subtipo de projeto interno. O exemplo a seguir mostra um trecho de um arquivo de projeto, onde um nome de um arquivo que contém propriedades específicas de um subtipo de projeto, é passado para esse subtipo de projeto.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Confira também
- [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)
