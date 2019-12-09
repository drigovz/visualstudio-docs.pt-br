---
title: Elemento CommandPlacements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb22359c936caacef81f4c9b81993a46d47ccc0b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341893"
---
# <a name="commandplacements-element"></a>Elemento CommandPlacements
O elemento CommandPlacements agrupa elementos CommandPlacement e outros agrupamentos CommandPlacements.

 O elemento CommandPlacements é opcional. Se não há comandos, grupos ou menus devem ser incluídas em um local secundário, não precisará incluí-la em seu *VSCT* arquivo.

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
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|CommandPlacements|Agrupa elementos de CommandPlacement e outros agrupamentos CommandPlacements.|
|[Elemento CommandPlacement](../extensibility/commandplacement-element.md)|Permite que os botões, grupos e menus a serem incluídos em mais de um grupo ou menu.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos.|

## <a name="example"></a>Exemplo

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Consulte também
- [Elemento CommandPlacement](../extensibility/commandplacement-element.md)
- [Arquivos de tabela (. VSCT) de comando do Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)