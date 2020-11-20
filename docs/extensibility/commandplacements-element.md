---
title: Elemento CommandPlacements | Microsoft Docs
description: O elemento CommandPlacements agrupa elementos CommandPlacement e outros agrupamentos do CommandPlacements. O elemento CommandPlacements é opcional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 301fe17f3ad12bfd1e150d9bf48180be6cb62adc
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974012"
---
# <a name="commandplacements-element"></a>Elemento CommandPlacements
O elemento CommandPlacements agrupa elementos CommandPlacement e outros agrupamentos do CommandPlacements.

 O elemento CommandPlacements é opcional. Se nenhum comando, grupo ou menu precisar ser incluído em um local secundário, você não precisará incluir esta seção no arquivo *. vsct* .

## <a name="syntax"></a>Sintaxe

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|CommandPlacements|Agrupa elementos CommandPlacement e outros agrupamentos do CommandPlacements.|
|[Elemento CommandPlacement](../extensibility/commandplacement-element.md)|Permite que os botões, grupos e menus sejam incluídos em mais de um grupo ou menu.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento commandtable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos.|

## <a name="example"></a>Exemplo

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Confira também
- [Elemento CommandPlacement](../extensibility/commandplacement-element.md)
- [Arquivos de tabela de comando do Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
