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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2761e012d32516265e61c8001491e3c605372ff5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699018"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>A estrutura do arquivo [Content_types].xml
Contém informações sobre os tipos de conteúdo em um pacote VSIX. O Visual Studio usa o arquivo [Content_Types]. xml para instalar o pacote, mas ele não instala o próprio arquivo.

> [!NOTE]
> Embora este tópico se aplique somente a arquivos [Content_Type]. XML que são usados em pacotes VSIX, o tipo de arquivo [Content_Types]. xml faz parte do padrão *OPC (Open Packaging Conventions)* . Para obter mais informações, consulte [OPC: um novo padrão para empacotar seus dados](https://msdn.microsoft.com/magazine/cc163372.aspx) no site do MSDN.

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem o elemento raiz e seus atributos e elementos filho.

### <a name="root-element"></a>Elemento Root

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
| `http://schemas.openformats.org/package/2006/content-types` | O local do esquema de tipos de conteúdo. |

### <a name="child-elements"></a>Elementos filho
 O elemento `Types` pode conter qualquer número de elementos `Default`.

|Elemento|Descrição|
|-------------|-----------------|
|`Default`|Descreve um tipo de conteúdo no pacote VSIX. Cada tipo de arquivo no pacote deve ter seu próprio `Default` elemento.|

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Extension`|A extensão de nome de arquivo de um arquivo no pacote VSIX.|
|`ContentType`|Descreve o tipo de conteúdo associado à extensão de nome de arquivo.|

### <a name="attribute-name-attribute"></a>{Nome do atributo} Attribute
 O Visual Studio reconhece os seguintes `ContentType` valores para os `Extension` tipos associados.

|Extensão|ContentType|
|---------------|-----------------|
|txt|texto/sem formatação|
|pkgdef|texto/sem formatação|
|Xml|texto/XML|
|vsixmanifest|texto/XML|
|htm ou HTML|texto/html|
|RTF|aplicativo/RTF|
|pdf|aplicativo/PDF|
|GIF|image/gif|
|jpg ou JPEG|imagem/jpg|
|tiff|imagem/tiff|
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

## <a name="see-also"></a>Confira também
- [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Referência do esquema de extensão do VSIX 1,0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: um novo padrão para empacotar seus dados](https://msdn.microsoft.com/magazine/cc163372.aspx)
