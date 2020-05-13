---
title: Elemento GuidSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711122"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
O `GuidSymbol` elemento contém o GUID do par GUID:ID que representa um menu, grupo ou comando. O ID vem `IDSymbol` de `GuidSymbol` um elemento no elemento. O `GuidSymbol` elemento `name` tem um atributo que fornece um nome `value` amigável para o GUID, que está contido no atributo.

## <a name="syntax"></a>Sintaxe

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|name|Obrigatórios. Nome do símbolo GUID.|
|value|Obrigatórios. GUIA do símbolo GUID.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contém o ID do par GUID:ID que representa um menu, grupo ou comando.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento símbolos](../extensibility/symbols-element.md)|Grupos `GuidSymbol` elementos em um arquivo *.vsct.*|

## <a name="remarks"></a>Comentários
 Normalmente, um arquivo *.vsct* contém três `GuidSymbol` elementos em sua `Symbols` seção, um para o próprio pacote, um para o conjunto de comandos (a coleção de menus, grupos e comandos que o pacote disponibiliza) e um para os bitmaps que fornecem ícones para botões e outros componentes visuais. Cada `IDSymbol` elemento em `GuidSymbol` um determinado `value`elemento deve ter um único . No `IDSymbol` entanto, elementos que têm valores idênticos podem existir em um pacote, desde que tenham pais diferentes.

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
