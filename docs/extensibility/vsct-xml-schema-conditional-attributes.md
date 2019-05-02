---
title: Atributos condicionais do esquema XML do VSCT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73e48cfb0a30ca71592879c8276ef1be76cb973f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953135"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atributos condicionais do esquema XML do VSCT
Você pode aplicar atributos condicionais para todas as listas e itens. Operadores lógicos e expressões de expansão de símbolo avaliadas como true ou false. Se for true, a lista associada ou o item será incluído na saída resultante.

 Você pode testar as expansões de token em relação a outras expansões de token ou constantes. A função `Defined()` testa se um determinado nome tiver sido definido, mesmo se ele não tem nenhum valor.

 Quando um atributo Condition é aplicado a uma lista, a condição é aplicada a todos os elementos filho na lista. Se um elemento filho em si contém um atributo Condition, sua condição é combinada com a expressão pai por uma operação AND.

 Os valores 1, '1' e 'true' são avaliados como true e 0, '0' e 'false' são avaliadas como false.

## <a name="operators"></a>Operadores
 Use os operadores a seguir para avaliar expressões condicionais.

|Operador|Definição|
|--------------|----------------|
|(,)|Agrupamento|
|!|Não lógico|
|\<, >, \<=, >=, ==, !=|Relacional e igualdade|
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

## <a name="see-also"></a>Consulte também
- [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)