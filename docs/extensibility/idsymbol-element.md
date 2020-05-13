---
title: Elemento IDSymbol | Microsoft Docs
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
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710369"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
O `IDSymbol` elemento contém o ID do par GUID:ID que representa um menu, grupo ou comando. O GUID vem `GuidSymbol` do elemento pai. O `IDSymbol` elemento `name` tem um atributo que fornece um nome amigável `value` para o ID, que está contido no atributo.

## <a name="syntax"></a>Sintaxe

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|name|Obrigatórios. Nome do símbolo de id.|
|value|Obrigatórios. Valor numérico de id do símbolo id.|

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contém o GUID do par GUID:ID que representa um menu, grupo ou comando. Agrupa elementos `IDSymbol`.|

## <a name="remarks"></a>Comentários
 Cada `IDSymbol` elemento em `GuidSymbol` um determinado `value`elemento deve ter um único . No `IDSymbol` entanto, elementos que têm valores idênticos podem existir em um pacote, desde que tenham pais diferentes.

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
