---
title: Propriedades do MSBuild com suporte do SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5470160c6b0af1af39238a14319ad497e1541a43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985173"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Propriedades do MsBuild com suporte no SharePoint
  Qualquer [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriedade definida no arquivo Microsoft. VisualStudio. SharePoint. targets, arquivo de projeto ou arquivo de usuário do projeto pode ser usada em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos do SharePoint. Além das [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Propriedades comuns fornecidas pelo projeto, o SharePoint define propriedades adicionais que são específicas para projetos do SharePoint.

 Para obter uma lista de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Propriedades comuns, consulte [Propriedades comuns do projeto MSBuild](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Para obter uma lista completa das propriedades com suporte pela linguagem de programação, examine o arquivo *. targets* , o arquivo de projeto (*. csproj* ou *. vbproj*) ou o arquivo de usuário do projeto (*csproj. User* ou *. vbproj. User*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>Propriedades do MsBuild específicas para o SharePoint
 A tabela a seguir lista [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] as propriedades que se aplicam especificamente aos projetos do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Existem outras propriedades, mas elas são para uso interno.

|Nome da propriedade|Descrição|
|-------------------|-----------------|
|SharePointSiteUrl|Uma cadeia de caracteres que representa o [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para o site do SharePoint.|
|SandboxedSolution|Um valor booliano que indica se a solução é uma solução em área restrita.|
|ActiveDeploymentConfiguration|A configuração de implantação ativa.|
|IncludeAssemblyInPackage|Um valor booliano que indica se o assembly está incluído no arquivo de pacote.|
|PreDeploymentCommand|Um valor de cadeia de caracteres que representa o comando a ser executado na etapa de comando pré-implantação.|
|PostDeploymentCommand|Um valor de cadeia de caracteres que representa o comando a ser executado na etapa de comando pós-implantação.|
|CustomBeforeSharePointTargets|Uma cadeia de caracteres que representa o caminho de um [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] arquivo de destino. Se o arquivo de destinos existir e estiver definido, ele será importado antes de qualquer dado de destino do SharePoint. Essa propriedade permite que você personalize o processo de pacote predefinindo propriedades relacionadas ao empacotamento sem modificar o arquivo de destinos do SharePoint enviado, mas o arquivo de destinos ainda se aplica a todos os projetos do SharePoint.|
|CustomAfterSharePointTargets|Uma cadeia de caracteres que representa o caminho de um [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] arquivo de destino. Se o arquivo de destinos existir e estiver definido, ele será importado após todos os dados de destino do SharePoint. Essa propriedade permite que você personalize o processo de pacote substituindo as propriedades e os destinos relacionados ao empacotamento sem precisar modificar o arquivo de destinos do SharePoint enviado, mas o arquivo de destinos ainda se aplica a todos os projetos do SharePoint.|
|LayoutPath|Uma cadeia de caracteres que representa o diretório raiz onde cada um dos arquivos a serem empacotados é temporariamente colocado antes de serem adicionados ao arquivo *. wsp* . Esse caminho pode ser útil para saber quando você substitui os destinos BeforeLayout e AfterLayout para adicionar, remover ou modificar arquivos a serem empacotados, pois você pode usá-lo para alterar o conteúdo do arquivo *. wsp* .|
|BasePackagePath|Uma cadeia de caracteres que representa a pasta na qual o pacote é colocado. Esse valor usa o diretório de saída do projeto, como Bin\Debug.|
|PackageExtension|Uma cadeia de caracteres que representa a extensão de nome de arquivo a ser acrescentada ao pacote. O valor padrão é WSP.|
|AssemblyDeploymentTarget|Uma cadeia de caracteres que representa o local em que o assembly do projeto é implantado no servidor do SharePoint. Seu valor é GlobalAssemblyCache (o padrão) ou WebApplication. Essa propriedade também pode ser definida no janela Propriedades.|
|PackageWithValidation|Um valor booliano que especifica se a validação é executada antes do empacotamento. Essa propriedade permite ignorar erros de validação durante a criação de pacotes.|
|ValidatePackageDependsOn|Uma cadeia de caracteres que define destinos adicionais a serem executados antes do destino ValidatePackage.|
|TokenReplacementFileExensions|Uma cadeia de caracteres que define os arquivos que têm seus tokens substituídos durante o empacotamento.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Usar propriedades do MsBuild na página Propriedades
 Para obter flexibilidade, em vez de usar cadeias de caracteres embutidas em código na **linha de comando de pré-implantação** e nas caixas de linha de comando de **pós-implantação** na página de propriedades do SharePoint, você pode usar as propriedades do SharePoint como argumentos. Por exemplo, em vez de especificar uma [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] cadeia de caracteres específica para o site do SharePoint, você pode usar `$(SharePointSiteUrl)` .

> [!NOTE]
> Você pode usar a [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] sintaxe de variável `$(` *PropertyName* `)` ou a sintaxe de variável de ambiente `%` *PropertyName* `%` para especificar uma propriedade.

## <a name="see-also"></a>Confira também

- [Referência do MSBuild](../msbuild/msbuild-reference.md)