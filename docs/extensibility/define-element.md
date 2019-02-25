---
title: Definir o elemento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ccb14705b4d799e1f7fa6de4728ee8f7fc7b3fb4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706633"
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