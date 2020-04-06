---
title: Elemento símbolo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699342"
---
# <a name="symbols-element"></a>Elemento Symbols
Define GUIDs e IDs que são usados por outros elementos VSCT. Para código não gerenciado, essas informações geralmente vêm dos arquivos de cabeçalho especificados pelo [Extern Element](../extensibility/extern-element.md). O código gerenciado usa os elementos filho do elemento Símbolos para definir essas informações.

 Se você criar um arquivo .vsct a partir de um arquivo .cto existente, os símbolos serão gerados como filhos do elemento Símbolos. Para obter mais informações, consulte [Como: Criar um . Arquivo Vsct de um Existente . Arquivo Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 O elemento Símbolos não deve ser confundido com o [Elemento Definir](../extensibility/define-element.md), que define pares de valor de nome para uso pelo pré-processador.

## <a name="syntax"></a>Sintaxe

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|Nenhum||

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|GuidSymbol|Define um símbolo GUID. GuidSymbol tem dois atributos necessários: nome e valor. O nome é o nome do símbolo, e o valor é o valor do GUID como uma string.<br /><br /> Por exemplo:\<GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848} />|
|Símbolo de ID|Define um símbolo. O IDSymbol tem dois atributos necessários: nome e valor. O nome é o nome do símbolo, e o valor é o valor do símbolo como uma string.<br /><br /> Por exemplo:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|O elemento raiz do arquivo .vsct.|

## <a name="example"></a>Exemplo

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>Confira também
- [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
