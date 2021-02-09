---
title: Elemento CommandPlacement | Microsoft Docs
description: O elemento CommandPlacement permite que os botões, grupos e menus sejam incluídos em mais de um grupo ou menu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77c7ae72f9c4c776dd8535e54112dc43833705cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876102"
---
# <a name="commandplacement-element"></a>Elemento CommandPlacement
O elemento CommandPlacement permite que os botões, grupos e menus sejam incluídos em mais de um grupo ou menu. Usando o elemento CommandPlacement, você não precisa redefinir completamente esses itens para modificar a aparência de uma interface do usuário.

 Para obter mais informações, consulte [criar grupos de botões reutilizáveis](../extensibility/creating-reusable-groups-of-buttons.md).

## <a name="syntax"></a>Sintaxe

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatório. O GUID do conjunto de comandos, conforme definido no [elemento Symbols](../extensibility/symbols-element.md).|
|id|Obrigatório. A ID do menu, do grupo ou do comando a ser colocado, conforme definido no `Symbols Element` .|
|priority|Obrigatório. Determina a posição visual do item em seu elemento pai.|
|Condição|Opcional. Consulte [Aattributes condicional](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Pai|Obrigatório. O menu ou grupo que hospeda o item a ser colocado.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Especifica grupos de elementos CommandPlacements e CommandPlacement.|

## <a name="example"></a>Exemplo

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Confira também
- [Elemento CommandPlacements](../extensibility/commandplacements-element.md)
- [Arquivos de tabela de comando do Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
