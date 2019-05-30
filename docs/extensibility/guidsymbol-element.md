---
title: Elemento GuidSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bebcec561f915bd8223d0adc183293a1760c261d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342206"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
O `GuidSymbol` elemento contém o GUID do par GUID:ID que representa um menu, um grupo ou um comando. A ID vem de uma `IDSymbol` elemento no `GuidSymbol` elemento. O `GuidSymbol` elemento tem um `name` que fornece um nome amigável para o GUID, que está contido no atributo o `value` atributo.

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
|name|Necessário. Nome do símbolo GUID.|
|Valor |Necessário. GUID do símbolo GUID.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contém a ID do par GUID:ID que representa um menu, um grupo ou um comando.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento Symbols](../extensibility/symbols-element.md)|Grupos `GuidSymbol` elementos em um *VSCT* arquivo.|

## <a name="remarks"></a>Comentários
 Normalmente, uma *VSCT* arquivo contém três `GuidSymbol` elementos no seu `Symbols` seção, um para o pacote propriamente dito, um para o conjunto de comandos (a coleção de menus, grupos e comandos que disponibiliza o pacote), e uma para os bitmaps que fornecer ícones de botões e outros componentes do visual. Cada `IDSymbol` elemento em um determinado `GuidSymbol` elemento deve ter um único `value`. No entanto, `IDSymbol` elementos que têm valores idênticos podem existir em um pacote, desde que eles tenham pais diferentes.

## <a name="see-also"></a>Consulte também
- [Arquivos de tabela (. VSCT) de comando do Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)