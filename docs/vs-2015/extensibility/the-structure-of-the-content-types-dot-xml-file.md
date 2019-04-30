---
title: A estrutura do Content_types] arquivo. XML | Microsoft Docs
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
ms.openlocfilehash: 4117e028611c2ff64102a97579d17d72f50407e0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430150"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>A estrutura do Content_types] arquivo. XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contém informações sobre os tipos de conteúdo de um pacote VSIX. Visual Studio usa o arquivo [Content_Types]. XML para instalar o pacote, mas não instala o arquivo propriamente dito.  
  
> [!NOTE]
> Embora este tópico se aplica somente a [Content_Type]. XML arquivos que são usados em pacotes VSIX, o tipo de arquivo [Content_Types]. xml faz parte do *Open Packaging Conventions (OPC)* padrão. Para obter mais informações, consulte [OPC: Um novo padrão para empacotamento seus dados](http://go.microsoft.com/fwlink/?LinkID=148207) no site do MSDN.  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem o elemento raiz e seus atributos e elementos filho.  
  
### <a name="root-element"></a>Elemento raiz  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`Types`|Contém elementos filho que enumerar os tipos de arquivos no pacote VSIX.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Xmlns`|(Obrigatório.) O local do esquema usado para esse arquivo. XML de [Content_Types].|  
  
### <a name="attribute-name-attribute"></a>{Nome do atributo} Atributo  
  
|                           Valor                           |                Descrição                |
|-----------------------------------------------------------|-------------------------------------------|
| http://schemas.openformats.org/package/2006/content-types | O local do esquema de tipos de conteúdo. |
  
### <a name="child-elements"></a>Elementos filho  
 O `Types` elemento pode conter qualquer número de `Default` elementos.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`Default`|Descreve um tipo de conteúdo no pacote VSIX. Cada tipo de arquivo do pacote deve ter seu próprio `Default` elemento.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Extension`|A extensão de nome de arquivo de um arquivo no pacote VSIX.|  
|`ContentType`|Descreve o tipo de conteúdo que está associado com a extensão de nome de arquivo.|  
  
### <a name="attribute-name-attribute"></a>{Nome do atributo} Atributo  
 Visual Studio reconhece as seguintes `ContentType` valores associado `Extension` tipos.  
  
|Extensão|ContentType|  
|---------------|-----------------|  
|txt|texto/simples|  
|pkgdef|texto/simples|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm ou html|text/html|  
|rtf|aplicativo/rtf|  
|pdf|aplicativo/pdf|  
|gif|imagem/gif|  
|JPG ou jpeg|image/jpg|  
|TIFF|imagem/tiff|  
|vsix|aplicativo/zip|  
|zip|aplicativo/zip|  
|DLL|application/octet-stream|  
|todos os outros tipos de arquivo|application/octet-stream|  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O seguinte arquivo. XML [Content_Types] descreve um pacote VSIX típico.  
  
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
 [Referência de esquema 1.0 de extensão do VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Um novo padrão para empacotar dados](http://go.microsoft.com/fwlink/?LinkID=148207)
