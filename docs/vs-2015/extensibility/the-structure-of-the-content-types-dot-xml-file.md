---
title: A estrutura do arquivo Content_types].xml | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d6eca44c08cf35e7b2075965c1b6139e7fb95bc
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395365"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>A estrutura do arquivo Content_types].xml
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contém informações sobre os tipos de conteúdo em um pacote VSIX. O Visual Studio usa o arquivo [Content_Types].xml para instalar o pacote, mas ele não instala o arquivo em si.  
  
> [!NOTE]
> Embora este tópico se aplique apenas a arquivos [Content_Type].xml que são usados em pacotes VSIX, o tipo de arquivo [Content_Types].xml faz parte do padrão *Open Packaging Conventions (OPC).* Para obter mais informações, consulte [OPC: Um novo padrão para empacotar seus dados](https://msdn.microsoft.com/magazine/cc163372.aspx) no site da MSDN.  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem o elemento raiz e seus atributos e elementos infantis.  
  
### <a name="root-element"></a>Elemento Root  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`Types`|Contém elementos infantis que enumeram os tipos de arquivo no pacote VSIX.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Xmlns`|(Obrigatório.) A localização do esquema usado para este arquivo [Content_Types].xml.|  
  
### <a name="attribute-name-attribute"></a>{Nome do atributo} Atributo  
  
|                           Valor                           |                Descrição                |
|-----------------------------------------------------------|-------------------------------------------|
| `http://schemas.openformats.org/package/2006/content-types` | A localização do esquema dos tipos de conteúdo. |
  
### <a name="child-elements"></a>Elementos filho  
 O elemento `Types` pode conter qualquer número de elementos `Default`.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`Default`|Descreve um tipo de conteúdo no pacote VSIX. Cada tipo de arquivo no `Default` pacote deve ter seu próprio elemento.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Extension`|A extensão do nome do arquivo de um arquivo no pacote VSIX.|  
|`ContentType`|Descreve o tipo de conteúdo associado à extensão do nome do arquivo.|  
  
### <a name="attribute-name-attribute"></a>{Nome do atributo} Atributo  
 O Visual Studio `ContentType` reconhece os `Extension` seguintes valores para os tipos associados.  
  
|Extensão|ContentType|  
|---------------|-----------------|  
|txt|texto/sem formatação|  
|Pkgdef|texto/sem formatação|  
|Xml|texto/xml|  
|Vsixmanifest|texto/xml|  
|htm ou html|texto/html|  
|Rtf|aplicação/rtf|  
|pdf|aplicação/pdf|  
|GIF|image/gif|  
|jpg ou jpeg|imagem/jpg|  
|tiff|imagem/tiff|  
|vsix|aplicação/zip|  
|zip|aplicação/zip|  
|dll|application/octet-stream|  
|todos os outros tipos de arquivos|application/octet-stream|  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O seguinte arquivo [Content_Types].xml descreve um pacote VSIX típico.  
  
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
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Referência do Esquema de Extensão VSIX 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: um novo padrão para empacotar seus dados](https://msdn.microsoft.com/magazine/cc163372.aspx)
