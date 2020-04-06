---
title: Elemento grupos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6383c3c7a28f9aa7778fddcbfe36b237d21323f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711181"
---
# <a name="groups-element"></a>Elemento Groups
Contém entradas que definem os grupos de comando de um VSPackage.

## <a name="syntax"></a>Sintaxe

```xml
<Groups>
  <Group>... </Group>
  <Group>... </Group>
</Groups>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento Group](../extensibility/group-element.md)|Representa um único grupo de comando.|
|[Elemento de grupos](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comando de um VSPackage.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento comandos](../extensibility/commands-element.md)|Representa a coleção de comandos na barra de ferramentas VSPackage.|

## <a name="example"></a>Exemplo

```xml
<Groups>
  <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
  </Group>
</Groups>
```

## <a name="see-also"></a>Confira também
- [Como o VSPackages adiciona elementos de interface de usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
