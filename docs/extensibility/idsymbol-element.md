---
title: Elemento IDSymbol | Microsoft Docs
description: 'O elemento IDSymbol contém a ID do par GUID: ID que representa um menu, grupo ou comando.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4feb477f8507bc3fe57e6db355538ab98ceeeaa
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995532"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
O `IDSymbol` elemento contém a ID do par GUID: ID que representa um menu, grupo ou comando. O GUID vem do elemento pai `GuidSymbol` . O `IDSymbol` elemento tem um `name` atributo que fornece um nome amigável para a ID, que está contido no `value` atributo.

## <a name="syntax"></a>Syntax

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|name|Obrigatórios. Nome do símbolo de ID.|
|value|Obrigatórios. Valor de ID numérico do símbolo de ID.|

### <a name="child-elements"></a>Elementos filho
 nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contém o GUID do par GUID: ID que representa um menu, grupo ou comando. Agrupa elementos `IDSymbol`.|

## <a name="remarks"></a>Comentários
 Cada `IDSymbol` elemento em um determinado `GuidSymbol` elemento deve ter um exclusivo `value` . No entanto, os `IDSymbol` elementos que têm valores idênticos podem existir em um pacote, desde que tenham diferentes pais.

## <a name="see-also"></a>Confira também
- [Arquivos de tabela de comando do Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
