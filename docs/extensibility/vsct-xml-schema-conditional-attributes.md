---
title: VsCT XML Schema Atributos Condicionais | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697941"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VsCT XML atributos condicionais do esquema
Você pode aplicar atributos condicionais a todas as listas e itens. Operadores lógicos e expressões de expansão de símbolos avaliam ser verdadeiros ou falsos. Se for verdade, a lista ou item associado será incluído na saída resultante.

 Você pode testar expansões de tokens contra outras expansões ou constantes de tokens. A `Defined()` função testa se um nome específico foi definido, mesmo que não tenha valor.

 Quando um atributo Condição é aplicado a uma lista, a condição é aplicada a todos os elementos da criança da lista. Se um elemento filho em si contém um atributo Condição, então sua condição é combinada com a expressão pai por uma operação AND.

 Os valores 1, '1' e 'verdadeiro' são avaliados como verdadeiros, e 0, '0' e 'falso' são avaliados como falsos.

## <a name="operators"></a>Operadores
 Use os seguintes operadores para avaliar expressões condicionais.

|Operador|Definição|
|--------------|----------------|
|(,)|Agrupamento|
|!|Não lógico|
|\<>, \<=, >=, ==, !=|Igualdade e Igualdade|
|e|Boolean|
|ou|Boolean|

## <a name="examples"></a>Exemplos

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>Confira também
- [Tabela de comando do Visual Studio (. Vsct) arquivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
