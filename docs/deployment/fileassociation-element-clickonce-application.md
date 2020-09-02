---
title: '&lt;&gt;elemento FileAssociation (aplicativo ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d3a43af5b2c7d50034cbed9d7da16e65b402f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928521"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;&gt;elemento FileAssociation (aplicativo ClickOnce)
Identifica uma extensão de arquivo a ser associada ao aplicativo.

## <a name="syntax"></a>Syntax

```xml
<fileAssociation
    xmlns="urn:schemas-microsoft-com:clickonce.v1"
    extension
    description
    progid
    defaultIcon
/>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O elemento `fileAssociation` é opcional. O elemento tem os atributos a seguir.

|Atributo|Descrição|
|---------------|-----------------|
|`extension`|Obrigatórios. A extensão de arquivo a ser associada ao aplicativo.|
|`description`|Obrigatórios. Uma descrição do tipo de arquivo a ser usado pelo shell.|
|`progid`|Obrigatórios. Um nome que identifica exclusivamente o tipo de arquivo.|
|`defaultIcon`|Obrigatórios. Especifica o ícone a ser usado para arquivos com esta extensão. O arquivo de ícone deve ser especificado usando o [ \<file> elemento](../deployment/file-element-clickonce-application.md) dentro do [ \<assembly> elemento](../deployment/assembly-element-clickonce-application.md) que contém esse elemento.|

## <a name="remarks"></a>Comentários
 Esse elemento deve incluir uma referência de namespace XML para "urn: schemas-microsoft-com: ClickOnce. v1". Se o `<fileAssociation>` elemento for usado, ele deverá vir após o `<application>` elemento em seu [ \<assembly> elemento](../deployment/assembly-element-clickonce-application.md)pai.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] não substituirá as associações de arquivo existentes. No entanto, um aplicativo ClickOnce pode substituir a extensão do arquivo somente para o usuário atual. Depois que o aplicativo ClickOnce for desinstalado, o ClickOnce excluirá a associação de arquivo para o usuário e a associação por máquina estará ativa novamente.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra os `fileAssociation` elementos em um manifesto de aplicativo para um aplicativo de editor de texto implantado usando o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Este exemplo de código também inclui o [ \<file> elemento](../deployment/file-element-clickonce-application.md) exigido pelo `defaultIcon` atributo.

```xml
<file name="text.ico" size="4286">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>
  </hash>
</file>
<file name="writing.ico" size="9662">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>
  </hash>
</file>
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />
```

## <a name="see-also"></a>Confira também
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)