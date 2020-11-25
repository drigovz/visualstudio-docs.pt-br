---
title: Parâmetros substituíveis | Microsoft Docs
description: Examine os parâmetros substituíveis (tokens), que especificam valores dentro de arquivos de projeto para itens de solução do SharePoint cujos valores reais não são conhecidos em tempo de design.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload: office
ms.openlocfilehash: 1cd44b3edfaeae376e5a4a9698d138bd75c03bf8
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970259"
---
# <a name="replaceable-parameters"></a>Parâmetros substituíveis
  Parâmetros substituíveis, ou *tokens*, podem ser usados dentro de arquivos de projeto para fornecer valores para itens de solução do SharePoint cujos valores reais não são conhecidos em tempo de design. Eles são semelhantes em função aos [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokens de modelo padrão. Para obter mais informações, consulte [parâmetros de modelo](../ide/template-parameters.md).

## <a name="token-format"></a>Formato do token
 Os tokens começam e terminam com um caractere de cifrão ($). Na implantação, todos os tokens usados são substituídos por valores reais quando um projeto é empacotado em um pacote de solução do SharePoint (arquivo *. wsp* ). Por exemplo, o token **$SharePoint. Package.Name $** pode ser resolvido para a cadeia de caracteres "testar pacote do SharePoint".

## <a name="token-rules"></a>Regras de token
 As regras a seguir se aplicam a tokens:

- Os tokens podem ser especificados em qualquer lugar em uma linha.

- Tokens não podem abranger várias linhas.

- O mesmo token pode ser especificado mais de uma vez na mesma linha e no mesmo arquivo.

- Tokens diferentes podem ser especificados na mesma linha.

  Os tokens que não seguem essas regras são ignorados e não resultam em um aviso ou erro.

  A substituição de tokens por valores de cadeia de caracteres é feita imediatamente após a transformação do manifesto. Essa substituição permite que o usuário edite os modelos de manifesto com tokens.

### <a name="token-name-resolution"></a>Resolução de nomes de token
 Na maioria dos casos, um token é resolvido para um valor específico, independentemente de onde ele está contido. No entanto, se o token estiver relacionado a um pacote ou recurso, o valor do token dependerá de onde ele está contido. Por exemplo, se um recurso estiver no pacote A, o token será `$SharePoint.Package.Name$` resolvido para o valor "pacote a". Se o mesmo recurso estiver no pacote B, o será `$SharePoint.Package.Name$` resolvido para "pacote B".

## <a name="tokens-list"></a>Lista de tokens
 A tabela a seguir lista os tokens disponíveis.

|Name|Descrição|
|----------|-----------------|
|$SharePoint. Project. FileName $|O nome do arquivo de projeto que o contém, como, *NewProj. csproj*.|
|$SharePoint. Project. FileNameWithoutExtension $|O nome do arquivo de projeto que o contém sem a extensão de nome de arquivo. Por exemplo, "NewProj".|
|$SharePoint. Project. AssemblyFullName $|O nome de exibição (nome forte) do assembly de saída do projeto recipiente.|
|$SharePoint. Project. AssemblyFileName $|O nome do assembly de saída do projeto recipiente.|
|$SharePoint. Project. AssemblyFileNameWithoutExtension $|O nome do assembly de saída do projeto recipiente, sem a extensão de nome de arquivo.|
|$SharePoint. Project. AssemblyPublicKeyToken $|O token de chave pública do assembly de saída do projeto recipiente, convertido em uma cadeia de caracteres. (16 caracteres no formato hexadecimal "X2").|
|$SharePoint. Package.Name $|O nome do pacote de contenção.|
|$SharePoint. Package. FileName $|O nome do arquivo de definição do pacote que o contém.|
|$SharePoint. Package. FileNameWithoutExtension $|O nome (sem extensão) do arquivo de definição do pacote que o contém.|
|$SharePoint. Package.Id $|A ID do SharePoint para o pacote de contenção. Se um recurso for usado em mais de um pacote, esse valor será alterado.|
|$SharePoint. Feature. FileName $|O nome do arquivo de definição do recurso que contém, como *Feature1. Feature*.|
|$SharePoint. Feature. FileNameWithoutExtension $|O nome do arquivo de definição de recurso, sem a extensão de nome de arquivo.|
|$SharePoint. Feature. DeploymentPath $|O nome da pasta que contém o recurso no pacote. Esse token é igual à propriedade "caminho de implantação" no designer de recursos. Um valor de exemplo é, "Project1_Feature1".|
|$SharePoint. Feature.Id $|A ID do SharePoint do recurso que o contém. Esse token, assim como acontece com todos os tokens de nível de recurso, pode ser usado somente por arquivos incluídos em um pacote por meio de um recurso, não adicionado diretamente a um pacote fora de um recurso.|
|$SharePoint. ProjectItem.Name $|O nome do item de projeto (não seu nome de arquivo), conforme Obtido em **ISharePointProjectItem.Name**.|
|$SharePoint. Type. \<GUID> . AssemblyQualifiedName $|O nome qualificado do assembly do tipo correspondente ao [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] do token. O formato de [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] é minúscula e corresponde ao formato Guid. ToString ("D") (ou seja, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|
|$SharePoint. Type. \<GUID> . FullName $|O nome completo do tipo que corresponde ao GUID no token. O formato do GUID é minúscula e corresponde ao formato Guid. ToString ("D") (ou seja, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Adicionar extensões à lista de extensões de arquivo de substituição de token
 Embora os tokens possam ser teoricamente usados por qualquer arquivo que pertença a um item de projeto do SharePoint incluído no pacote, por padrão, o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procura tokens somente em arquivos de pacote, arquivos de manifesto e arquivos que têm as seguintes extensões:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- WebPart

- DWP

  Essas extensões são definidas pelo `<TokenReplacementFileExtensions>` elemento no arquivo Microsoft. VisualStudio. SharePoint. targets, localizado na pasta... \\<arquivos de programas \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools

  No entanto, você pode adicionar extensões de arquivo adicionais à lista. Adicione um `<TokenReplacementFileExtensions>` elemento a qualquer PropertyGroup no arquivo de projeto do SharePoint que é definido antes do \<Import> arquivo de destinos do SharePoint.

> [!NOTE]
> Como a substituição do token ocorre depois que um projeto é compilado, você não deve adicionar extensões de arquivo para tipos de arquivo que são compilados, como *. cs*, *. vb* ou *. resx*. Os tokens são substituídos somente em arquivos que não são compilados.

 Por exemplo, para adicionar as extensões de nome de arquivo (*. MyExtension* e *. yourextension*) à lista de extensões de nome de arquivo de substituição de token, você adicionaria o seguinte a um arquivo de projeto (*. csproj*):

```xml
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
.
.
.
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>
</PropertyGroup>
```

 Você pode adicionar a extensão diretamente ao arquivo de destinos (*. targets*). No entanto, adicionar a extensão altera a lista de extensões para todos os projetos do SharePoint empacotados no sistema local, não apenas os seus próprios. Essa extensão pode ser conveniente quando você é o único desenvolvedor no sistema ou se a maioria de seus projetos exigir. No entanto, como ele é específico do sistema, essa abordagem não é portátil e, portanto, é recomendável que você adicione todas as extensões ao arquivo de projeto em vez disso.

## <a name="see-also"></a>Veja também
- [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
