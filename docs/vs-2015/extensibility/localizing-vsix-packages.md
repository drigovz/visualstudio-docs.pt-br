---
title: Localizando pacotes VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838385"
---
# <a name="localizing-vsix-packages"></a>Localizando pacotes do VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode localizar um pacote VSIX criando um arquivo extension. vsixlangpack para cada idioma de destino e, em seguida, colocando-os na pasta correta. Quando um pacote localizado é instalado, o nome localizado da extensão é exibido junto com uma descrição localizada. Se você fornecer um arquivo de licença localizado ou uma URL que aponte para informações localizadas, eles também serão exibidos.  
  
 Se o conteúdo do seu pacote VSIX incluir um VSPackage que adiciona comandos de menu ou outra interface do usuário, consulte [localizando comandos de menu](../extensibility/localizing-menu-commands.md) para obter informações sobre como localizar os novos elementos da interface do usuário.  
  
## <a name="directory-structure"></a>Estrutura de diretórios  
 Quando um usuário instala uma extensão, **extensões e atualizações** verifica o nível superior do pacote do VSIX para uma pasta cujo nome corresponde à localidade do Visual Studio do computador de destino. Se **as extensões e atualizações** localizarem um arquivo. vsixlangpack na pasta, ele substituirá os valores localizados nesse arquivo pelos valores correspondentes no arquivo. vsixmanifest. Esses valores são exibidos quando a extensão está sendo instalada. O exemplo a seguir mostra a estrutura de diretório para um pacote VSIX localizado em espanhol (es-ES) e francês (fr-FR).  
  
 MyExtension.dll  
  
 Extensão. vsixmanifest  
  
 [Content_Types]. xml  
  
 es-ES  
  
 Extensão. vsixlangpack  
  
 fr-FR  
  
 Extensão. vsixlangpack  
  
> [!NOTE]
> Os modelos de projeto com suporte ao VSIX em [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] gerar um manifesto do VSIX e nomeá-lo como origem. extensão. vsixmanifest. Quando o Visual Studio cria o projeto, ele copia o conteúdo desse arquivo em Extension. VsixManifest no pacote VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>O arquivo extension. vsixlangpack  
 O arquivo extension. vsixlangpack segue o [esquema do pacote de idiomas do VSIX](../extensibility/vsx-language-pack-schema-reference.md). Este esquema tem um elemento raiz [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) e estes quatro elementos [filho:](../extensibility/localizedname-element-vsix-language-pack-schema.md)localizáname, [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)e [License](../extensibility/license-element-vsix-language-pack-schema.md). Esses elementos filho correspondem aos `Name` `Description` elementos filho,, e, `MoreInfoURL` `License` do `Identifier` elemento do arquivo extension. vsixmanifest.  
  
 Ao criar um arquivo vsixlangpack, você deve definir a `Include in Vsix` propriedade como `true` . Caso contrário, o texto de instalação localizado será ignorado.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Para definir a propriedade include in VSIX  
  
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo extension. vsixlangpack e clique em **Propriedades**.  
  
2. Na grade de propriedades, clique em **incluir no VSIX**e defina seu valor como `true` .  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra partes relevantes de um arquivo extension. vsixmanifest, junto com o arquivo extension. vsixlangpack correspondente para espanhol. Os valores do pacote de idiomas substituem os valores do manifesto se a localidade do Visual Studio do computador de destino estiver definida como espanhol.  
  
### <a name="code"></a>Código  
 [Extensão. vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extensão. vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Elemento LanguagePack do VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Modelo de projeto VSIX](../extensibility/vsix-project-template.md)
