---
title: Elemento UsedCommands | Microsoft Docs
description: O elemento UsedCommands agrupa elementos UsedCommand e outros agrupamentos do UsedCommands. O elemento UsedCommands é opcional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89ecd1d0f7697a38ef7318ddf93a91a4397b5d72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934058"
---
# <a name="usedcommands-element"></a>Elemento UsedCommands
O elemento UsedCommands agrupa elementos UsedCommand e outros agrupamentos do UsedCommands.

 O elemento UsedCommands é opcional. Se você não chamar comandos definidos fora do pacote, não precisará incluir esta seção no arquivo. vsct.

## <a name="syntax"></a>Sintaxe

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
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
|[Elemento UsedCommand](../extensibility/usedcommand-element.md)|O comando que é implementado por outro código.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos (por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação) que um VSPackage fornece ao IDE (ambiente de desenvolvimento integrado).|

## <a name="example"></a>Exemplo

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Confira também
- [Elemento UsedCommand](../extensibility/usedcommand-element.md)
- [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
