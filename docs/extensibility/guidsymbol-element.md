---
title: Elemento GuidSymbol | Microsoft Docs
description: 'O elemento GuidSymbol contém o GUID do par GUID: ID que representa um menu, grupo ou comando.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8f739135a9a4bed969163ce26911e5304a66822b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943388"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
O `GuidSymbol` elemento contém o GUID do par GUID: ID que representa um menu, grupo ou comando. A ID vem de um `IDSymbol` elemento no `GuidSymbol` elemento. O `GuidSymbol` elemento tem um `name` atributo que fornece um nome amigável para o GUID, que está contido no `value` atributo.

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
|name|Obrigatório. Nome do símbolo de GUID.|
|value|Obrigatório. GUID do símbolo GUID.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contém a ID do par GUID: ID que representa um menu, grupo ou comando.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento Symbols](../extensibility/symbols-element.md)|Agrupa `GuidSymbol` elementos em um arquivo *. vsct* .|

## <a name="remarks"></a>Comentários
 Normalmente, um arquivo *. vsct* contém três `GuidSymbol` elementos em sua `Symbols` seção, um para o pacote em si, um para o conjunto de comandos (a coleção de menus, grupos e comandos disponibilizados pelo pacote) e outro para os bitmaps que fornecem ícones para botões e outros componentes visuais. Cada `IDSymbol` elemento em um determinado `GuidSymbol` elemento deve ter um exclusivo `value` . No entanto, os `IDSymbol` elementos que têm valores idênticos podem existir em um pacote, desde que tenham diferentes pais.

## <a name="see-also"></a>Confira também
- [Arquivos de tabela de comando do Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
