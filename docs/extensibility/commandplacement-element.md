---
title: Elemento de posicionamento de comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739734"
---
# <a name="commandplacement-element"></a>Elemento CommandPlacement
O elemento CommandPlacement permite que botões, grupos e menus sejam incluídos em mais de um grupo ou menu. Usando o elemento CommandPlacement, você não precisa redefinir completamente esses itens para modificar a aparência de uma interface de usuário.

 Para obter mais informações, consulte [Criar grupos reutilizáveis de botões](../extensibility/creating-reusable-groups-of-buttons.md).

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
|guid|Obrigatórios. A orientação do conjunto de comandos, conforme definido no [elemento Símbolos](../extensibility/symbols-element.md).|
|id|Obrigatórios. O id do menu, grupo ou comando a ser `Symbols Element`colocado, conforme definido no .|
|priority|Obrigatórios. Determina a posição visual do item em seu elemento pai.|
|Condição|Opcional. Ver [Atributos Condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Pai|Obrigatórios. O menu ou grupo que hospeda o item a ser colocado.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ComandosDe posicionamento](../extensibility/commandplacements-element.md)|Especifica grupos de comandos e elementos de posicionamento de comando.|

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
- [Elemento ComandosDe posicionamento](../extensibility/commandplacements-element.md)
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
