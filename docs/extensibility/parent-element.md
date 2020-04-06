---
title: Elemento pai | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702224"
---
# <a name="parent-element"></a>Elemento pai
O pai de um botão ou caixa de combinação pode ser apenas um grupo. O pai de um menu ou grupo pode ser qualquer outro menu ou grupo. Em um [elemento CommandPlacement](../extensibility/commandplacement-element.md), este elemento é necessário; em todas as outras instâncias é opcional. Se esse elemento for omitido, o pai será `Group_Undefined:0` implícito.

## <a name="syntax"></a>Sintaxe

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatórios. GUIA do identificador de comando GUID/ID.|
|id|Obrigatórios. ID do identificador de comando GUID/ID.|

### <a name="child-elements"></a>Elementos filho
 Nenhum

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos que um VSPackage fornece ao ambiente de desenvolvimento integrado (IDE). Por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação.|
|[Elemento botões](../extensibility/buttons-element.md)|Elementos [do botão](../extensibility/button-element.md) de grupos.|
|[Elemento menus](../extensibility/menus-element.md)|Define todos os menus que um VSPackage implementa.|
|[Elemento de grupos](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comando de um VSPackage.|

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
