---
title: Elemento Group | Microsoft Docs
description: O elemento Group define um grupo de comandos VSPackage. Este artigo descreve atributos, elementos filho e elementos pai.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a5520a8a47b4b356a79832b619395f86e8231d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945780"
---
# <a name="group-element"></a>Elemento Group
Define um grupo de comandos VSPackage.

## <a name="syntax"></a>Sintaxe

```xml
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">
  <Parent>... </Parent>
</Group>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatório. GUID do identificador de comando GUID/ID.|
|id|Obrigatório. ID do identificador de comando de GUID/ID.|
|priority|Opcional. Um valor numérico que especifica a prioridade.|
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Pai|Opcional. O elemento pai do botão.|
|Annotation|Comentário opcional.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento groups](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comandos de um VSPackage.|

## <a name="example"></a>Exemplo

```xml
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
</Group>
```

## <a name="see-also"></a>Confira também
- [Arquivos de tabela de comando do Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
