---
title: Referência de esquema de item de projeto do SharePoint | Microsoft Docs
description: Consulte uma visão geral da referência de esquema XML do item de projeto do SharePoint (ProjectItemModelSchema. xsd), que é usada para validar o conteúdo de arquivos. transdata.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd425111e7e3d69e381e69e60daf914f74cd2d11
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442541"
---
# <a name="sharepoint-project-item-schema-reference"></a>Referência de esquema de item de projeto do SharePoint
  O Visual Studio usa o esquema de item de projeto do SharePoint para validar o conteúdo de arquivos *. transdata* . Um arquivo *. COMDATA* especifica o conteúdo e o comportamento de um item de projeto do SharePoint. Para obter mais informações sobre o conteúdo de itens de projeto do SharePoint, consulte [criar modelos de item e modelos de projeto para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 O esquema do item de projeto do SharePoint é denominado ProjectItemModelSchema. xsd e é instalado por padrão em% arquivos de programas (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas.

 O elemento raiz é o elemento [ProjectItem](../sharepoint/projectitem-element.md) . A tabela a seguir descreve todos os elementos definidos pelo esquema.

|Elemento|Descrição|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Representa uma coleção de itens de dados personalizados que estão associados ao item de projeto do SharePoint.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Representa um item de dados personalizado que está associado ao item de projeto do SharePoint, no formato de chave/valor. Tanto a chave quanto o valor devem ser cadeias de caracteres.|
|[Recursoproperties](../sharepoint/featureproperties-element.md)|Representa uma coleção de valores de propriedade que são incluídos com um recurso quando ele é implantado no SharePoint. Depois que um recurso é implantado, você pode acessar os valores de propriedade em seu código.|
|[Recursoproperty](../sharepoint/featureproperty-element.md)|Representa uma propriedade personalizada que é incluída com um recurso quando é implantada no SharePoint. Depois que um recurso é implantado, você pode acessar a propriedade em seu código.|
|[Arquivos](../sharepoint/files-element.md)|Especifica os arquivos a serem implantados com o item de projeto do SharePoint, como um arquivo de elemento de recurso ou a saída de um projeto.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa um item de projeto do SharePoint.|
|[ProjectItemfile](../sharepoint/projectitemfile-element.md)|Representa um arquivo do SharePoint, como um arquivo de elemento de recurso, a ser incluído com o item de projeto quando ele é implantado no SharePoint.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Representa uma pasta mapeada.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Representa a saída de um projeto a ser incluído com o item de projeto quando ele é implantado no SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Representa um controle ASPX ou Web Part designado como seguro para qualquer usuário acessar em qualquer página ASPX no site do SharePoint.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Representa uma coleção de controles ASPX e Web Parts que são designados como seguros para qualquer usuário acessar em qualquer página ASPX no site do SharePoint.|

## <a name="see-also"></a>Confira também
- [Criar modelos de item e modelos de projeto para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
