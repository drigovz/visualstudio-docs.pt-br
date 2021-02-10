---
title: Elemento pai | Microsoft Docs
description: O elemento pai especifica que um elemento é um pai de um botão, caixa de combinação, menu ou grupo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e34b857d26be49bb98096c6b0ba85ff8049290b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968977"
---
# <a name="parent-element"></a>Elemento pai
O pai de um botão ou caixa de combinação pode ser apenas um grupo. O pai de um menu ou grupo pode ser qualquer outro menu ou grupo. Em um [elemento CommandPlacement](../extensibility/commandplacement-element.md), esse elemento é necessário; em todas as outras instâncias, é opcional. Se esse elemento for omitido, o pai de `Group_Undefined:0` será implícito.

## <a name="syntax"></a>Sintaxe

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|guid|Obrigatório. GUID do identificador de comando de GUID/ID.|
|id|Obrigatório. ID do identificador de comando de GUID/ID.|

### <a name="child-elements"></a>Elementos filho
 Nenhum

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento commandtable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos que um VSPackage fornece ao IDE (ambiente de desenvolvimento integrado). Por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação.|
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos do [elemento Button](../extensibility/button-element.md) de groups.|
|[Elemento menus](../extensibility/menus-element.md)|Define todos os menus que um VSPackage implementa.|
|[Elemento groups](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comandos de um VSPackage.|

## <a name="see-also"></a>Consulte também
- [Arquivos de tabela de comando do Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
