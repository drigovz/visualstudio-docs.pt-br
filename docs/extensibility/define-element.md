---
title: Definir o elemento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d82bd5050955f69e23c71569a13ac1a5d428aef2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348141"
---
# <a name="define-element"></a>Definir o elemento
Define um par de nome e o valor do símbolo. Este símbolo pode ser avaliado por atributos condicionais. Para obter mais informações, consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md). Consulte também o [elemento Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Sintaxe

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|name|Necessário. O nome do símbolo:<br /><br /> name="Mode"|
|Valor |Necessário. O valor do símbolo:<br /><br /> value="Standard"|
|Condição|Opcional. Para obter mais informações, consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos filho
 nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos que fornece um VSPackage para o ambiente de desenvolvimento integrado (IDE). Por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação.|

## <a name="example"></a>Exemplo

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Consulte também
- [Arquivos de tabela (. VSCT) de comando do Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)