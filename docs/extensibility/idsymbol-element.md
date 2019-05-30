---
title: Elemento IDSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4489be4ea24382ddaf0fcbe5e824eac3945c9cec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319529"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
O `IDSymbol` elemento contém a ID do par GUID:ID que representa um menu, um grupo ou um comando. O GUID é proveniente do pai `GuidSymbol` elemento. O `IDSymbol` elemento tem um `name` que fornece um nome amigável para a ID, que está contida no atributo de `value` atributo.

## <a name="syntax"></a>Sintaxe

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|name|Necessário. Nome do símbolo de ID.|
|Valor |Necessário. Valor numérico da ID do símbolo de ID.|

### <a name="child-elements"></a>Elementos filho
 nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contém o GUID do par GUID:ID que representa um menu, um grupo ou um comando. Agrupa elementos `IDSymbol`.|

## <a name="remarks"></a>Comentários
 Cada `IDSymbol` elemento em um determinado `GuidSymbol` elemento deve ter um único `value`. No entanto, `IDSymbol` elementos que têm valores idênticos podem existir em um pacote, desde que eles tenham pais diferentes.

## <a name="see-also"></a>Consulte também
- [Arquivos de tabela (. VSCT) de comando do Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)