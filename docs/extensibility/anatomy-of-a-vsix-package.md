---
title: Anatomia de um pacote VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6d3f994c531bd36ab4281c5f0b27e993cd3392
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740086"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia de um pacote VSIX
Um pacote VSIX é um arquivo *.vsix* que contém uma ou mais extensões do Visual Studio, juntamente com os metadados que o Visual Studio usa para classificar e instalar as extensões. Esses metadados estão contidos no manifesto VSIX e no arquivo *[Content_Types].xml.* Um pacote VSIX também pode conter um ou mais arquivos *Extension.vsixlangpack* para fornecer texto de configuração localizado, e pode conter pacotes VSIX adicionais para instalar dependências.

 O formato do pacote VSIX segue o padrão Open Packaging Conventions (OPC). O pacote contém binários e arquivos de suporte, juntamente com um arquivo *[Content_Types].xml* e um arquivo manifesto *.vsix.* Um pacote VSIX pode conter a saída de vários projetos, ou mesmo vários pacotes que tenham seus próprios manifestos.

> [!NOTE]
> Os nomes dos arquivos incluídos nos pacotes VSIX não devem incluir espaços, nem caracteres reservados em Uri (Uniform Resource Identifiers, identificadores de recursos uniformes), conforme definido em [ \[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>O manifesto VSIX
 O manifesto VSIX contém informações sobre a extensão a ser instalada e segue o Esquema VSX. Para obter mais informações, consulte [o esquema de extensão VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Para um exemplo de manifesto VSIX, consulte [o elemento PackageManifest (elemento raiz, esquema VSX)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 O manifesto VSIX `extension.vsixmanifest` deve ser nomeado quando ele está incluído em um arquivo ^.vsix*.

## <a name="the-content"></a>O conteúdo
 Um pacote VSIX pode conter modelos, itens de caixa de ferramentas, VSPackages ou qualquer outro tipo de extensão que seja suportada pelo Visual Studio.

## <a name="language-packs"></a>Pacotes de idiomas
 Um pacote VSIX pode conter uma ou mais arquivos *Extension.vsixlangpack* para fornecer texto localizado durante a instalação. Para obter mais informações, consulte [Localizing VSIX packages](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Dependências e referências
 Um pacote VSIX pode conter outros pacotes VSIX como referências. Cada um desses outros pacotes deve incluir seu próprio manifesto VSIX.

 Se um usuário tentar instalar uma extensão que tenha dependências, o instalador verificará se os conjuntos necessários estão instalados no sistema do usuário. Se os conjuntos necessários não forem encontrados, **extensões e atualizações** serão exibidos uma lista dos conjuntos em falta.

 Se o manifesto de extensão incluir um ou mais elementos [de referência,](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) **extensões e atualizações** compara o manifesto de cada referência às extensões instaladas no sistema, e instala a extensão referenciada se ela ainda não estiver instalada. Se uma versão anterior de uma extensão referenciada for instalada, a versão mais recente a substituirá.

 Se um projeto em uma solução de vários projetos incluir uma referência a outro projeto na mesma solução, o pacote VSIX inclui as dependências desse projeto. Você pode substituir esse comportamento clicando na referência para o projeto interno e, em seguida, na `BuiltProjectOutputGroup`janela **Propriedades,** definindo os grupos de saída incluídos na propriedade **VSIX** para .

 Para incluir DLLs de satélite de conjuntos referenciados no pacote VSIX, adicione `SatelliteDllsProjectOutputGroup` aos grupos de saída incluídos na propriedade **VSIX.**

## <a name="installation-location"></a>Local de instalação
 Durante a instalação, **extensões e atualizações** procura o conteúdo do pacote VSIX em uma pasta em *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensões*.

 Por padrão, a instalação se aplica apenas ao usuário atual, porque *%LocalAppData%* é um diretório específico do usuário. No entanto, se você definir o `True`elemento Todos os [Usuários](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) do manifesto para , a extensão será instalada em <em>.. \\ </em>VisualStudioInstallationFolder<em>\Common7\IDE\Extensões</em> e estará disponível para todos os usuários do computador.

## <a name="content_typesxml"></a>[Content_Types].xml
 O arquivo *[Content_Types].xml* identifica os tipos de arquivo no arquivo *.vsix* expandido. O Visual Studio usa este arquivo durante a instalação do pacote, mas não instala o arquivo em si. Para obter mais informações sobre este arquivo, consulte [A estrutura do arquivo [Content_types].xml](the-structure-of-the-content-types-dot-xml-file.md).

 Um arquivo *[Content_Types].xml* é exigido pelo padrão Open Packaging Conventions (OPC). Para obter mais informações sobre o OPC, consulte [OPC: Um novo padrão para empacotar seus dados](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) no site da MSDN.
