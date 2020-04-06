---
title: Localização de pacotes VSIX | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702894"
---
# <a name="localizing-vsix-packages"></a>Localizando pacotes do VSIX

Você pode localizar um pacote VSIX criando um arquivo *Extension.vsixlangpack* para cada idioma de destino e, em seguida, colocá-los na pasta correta. Quando um pacote localizado é instalado, o nome localizado da extensão é exibido juntamente com uma descrição localizada. Se você fornecer um arquivo de licença localizado ou uma URL que aponte para informações localizadas, elas também serão exibidas.

Se o conteúdo do seu pacote VSIX incluir um VSPackage que adiciona comandos de menu ou outras uI, consulte [os comandos do menu Localize](../extensibility/localizing-menu-commands.md) para obter informações sobre a localização dos novos elementos de ida e volta.

## <a name="directory-structure"></a>Estrutura do diretório

 Quando um usuário instala uma extensão, **extensões e atualizações** verifica o nível superior do pacote VSIX para uma pasta cujo nome corresponde ao local do Visual Studio do computador de destino. Se **Extensões e Atualizações** encontrar um arquivo *.vsixlangpack* na pasta, ele substituirá os valores localizados nesse arquivo pelos valores correspondentes no arquivo *.vsixmanifest.* Esses valores são exibidos quando a extensão está sendo instalada. O exemplo a seguir mostra a estrutura do diretório de um pacote VSIX localizado em espanhol (es-ES) e francês (fr-FR).

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Os modelos de projeto suportados [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] pelo VSIX no gerar um manifesto VSIX e nomeá-lo *fonte.extension.vsixmanifest*. Quando o Visual Studio constrói o projeto, ele copia o conteúdo desse arquivo em Extension.VsixManifest no pacote VSIX.

## <a name="the-extensionvsixlangpack-file"></a>O arquivo Extension.vsixlangpack

O arquivo *Extension.vsixlangpack* segue o [esquema do Pacote de Idiomas VSIX 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Este esquema tem `PackageLanguagePackManifest`um , que é `Metadata` imediatamente seguido por um elemento infantil. O elemento Metadados pode conter até `DisplayName` `Description`6 `MoreInfo` `License`elementos infantis, e `ReleaseNotes` `Icon`. Esses elementos infantis `DisplayName` `Description`correspondem `License` `ReleaseNotes`aos `Icon` elementos, `Metadata` `MoreInfo`e filhos do elemento do arquivo *Extension.vsixmanifest.*

Quando você cria um arquivo vsixlangpack, você deve definir a `Include in Vsix` propriedade para `true`. Caso contrário, o texto de instalação localizado será ignorado.

### <a name="to-set-the-include-in-vsix-property"></a>Para definir a propriedade Incluir em Vsix

1. No **Solution Explorer,** clique com o botão direito do mouse no arquivo Extension.vsixlangpack e, em seguida, clique **em Propriedades**.

2. Na **grade de propriedades,** clique em Incluir em `true` **Vsix**e defina seu valor como .

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

O exemplo a seguir mostra partes relevantes de um arquivo *Extension.vsixmanifest.* O arquivo também inclui o arquivo *Extension.vsixlangpack* correspondente para espanhol. Os valores do pacote de idiomas substituem os valores do manifesto se a localização do Visual Studio do computador de destino estiver definida como espanhol.

### <a name="code"></a>Código

- [*Extensão.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extension.vsixlangpack*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Confira também

|Title|Descrição|
|-----------|-----------------|
|[Referência do esquema 2.0 do VSIX Language Pack](vsix-language-pack-schema-2-0-reference.md)|Um pacote de idiomas VSIX descreve as informações de localização de um arquivo de implantação .vsix.|
|[Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descreve a estrutura e o conteúdo de um pacote vsix.|
|[Menu localize comandos](../extensibility/localizing-menu-commands.md)|Mostra como localizar outros recursos de texto em uma extensão.|
