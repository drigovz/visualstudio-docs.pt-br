---
title: A estrutura do arquivo [Content_types]. xml | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5cc42a5346498c04f759956b2ca00094ac1df119
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718722"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>A estrutura do arquivo [Content_types].xml
Contém informações sobre os tipos de conteúdo em um pacote VSIX. O Visual Studio usa o arquivo [Content_Types]. xml para instalar o pacote, mas ele não instala o próprio arquivo.

> [!NOTE]
> Embora este tópico se aplique somente a arquivos [Content_Type]. XML que são usados em pacotes VSIX, o tipo de arquivo [Content_Types]. xml faz parte do padrão *OPC (Open Packaging Conventions)* . Para obter mais informações, consulte [OPC: um novo padrão para empacotar seus dados](http://go.microsoft.com/fwlink/?LinkID=148207) no site do MSDN.

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem o elemento raiz e seus atributos e elementos filho.

### <a name="root-element"></a>Elemento raiz

|Elemento|Descrição|
|-------------|-----------------|
|`Types`|Contém elementos filho que enumeram os tipos de arquivo no pacote VSIX.|

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Xmlns`|(Obrigatório). O local do esquema usado para este arquivo [Content_Types]. xml.|

### <a name="attribute-name-attribute"></a>{Nome do atributo} Attribute

| Valor | Descrição |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | O local do esquema de tipos de conteúdo. |

### <a name="child-elements"></a>Elementos filho
 O elemento `Types` pode conter qualquer número de elementos `Default`.

|Elemento|Descrição|
|-------------|-----------------|
|`Default`|Descreve um tipo de conteúdo no pacote VSIX. Cada tipo de arquivo no pacote deve ter seu próprio elemento `Default`.|

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Extension`|A extensão de nome de arquivo de um arquivo no pacote VSIX.|
|`ContentType`|Descreve o tipo de conteúdo associado à extensão de nome de arquivo.|

### <a name="attribute-name-attribute"></a>{Nome do atributo} Attribute
 O Visual Studio reconhece os seguintes valores de `ContentType` para os tipos de `Extension` associados.

|Extensão|contentType|
|---------------|-----------------|
|localizado|texto/sem formatação|
|pkgdef|texto/sem formatação|
|xml|texto/XML|
|vsixmanifest|texto/XML|
|htm ou HTML|texto/HTML|
|RTF|aplicativo/RTF|
|formato|aplicativo/PDF|
|Gifs|imagem/GIF|
|jpg ou JPEG|imagem/jpg|
|formato|imagem/TIFF|
|vsix|aplicativo/zip|
|zip|aplicativo/zip|
|dll|application/octet-stream|
|todos os outros tipos de arquivo|application/octet-stream|

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição
 O arquivo [Content_Types]. XML a seguir descreve um pacote VSIX típico.

### <a name="code"></a>Código

```
<?xml version="1.0" encoding="utf-8" ?>
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
    <Default Extension="vsixmanifest" ContentType="text/xml" />
    <Default Extension="dll" ContentType="application/octet-stream" />
    <Default Extension="png" ContentType="application/octet-stream" />
    <Default Extension="txt" ContentType="text/plain" />
    <Default Extension="pkgdef" ContentType="text/plain" />
</Types>
```

## <a name="see-also"></a>Consulte também
- [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Referência do esquema de extensão do VSIX 1,0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: um novo padrão para empacotar seus dados](http://go.microsoft.com/fwlink/?LinkID=148207)