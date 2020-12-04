---
title: Operador de contexto no depurador (C++) | Microsoft Docs
description: Talvez seja necessário fornecer contexto para um nome C++ que esteja em um escopo externo e que esteja oculto por um nome local. Saiba como usar o operador de contexto para fazer isso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 1bc238cc56e1b815e79ba381a7cd4866085d3bef
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559752"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Operador de contexto no depurador do Visual Studio (C++)
Você pode usar o operador de contexto em C++ para qualificar um local de ponto de interrupção, um nome de variável ou uma expressão. O operador de contexto é útil para especificar um nome de um escopo externo que, de outra forma, é oculto por um nome local.

## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Sintaxe
 Há duas maneiras de especificar o contexto:

1. {,,[*module*] } *expression*

     As chaves devem conter duas vírgulas e o nome do módulo (executável ou DLL) ou o caminho completo.

     Por exemplo, para definir um ponto de interrupção na função `SomeFunction` de EXAMPLE.dll:

    ```C++
    {,,EXAMPLE.dll}SomeFunction
    ```

2. *módulo*! *expressão* de

    ```C++
    EXAMPLE.dll!SomeFunction
    ```

- *Module* é o nome de um módulo. Você pode usar um caminho completo para resolver a ambiguidade entre módulos com o mesmo nome.

   Se o caminho do *módulo* incluir uma vírgula, um espaço inserido ou uma chave, você deverá usar aspas em volta do caminho para que o analisador de contexto possa reconhecer corretamente a cadeia de caracteres. As aspas simples são consideradas parte de um nome de arquivo do Windows, portanto, você deve usar aspas duplas. Por exemplo,

  ```C++
  {,,"a long, long, library name.dll"} g_Var
  ```

- *expression* é qualquer expressão de C++ válida que seja resolvida para um destino válido, como um nome de função, um nome de variável ou um endereço de ponteiro no *módulo*.

  Quando o avaliador de expressão localiza um símbolo em uma expressão, procura pelo símbolo na seguinte ordem:

1. Escopo léxico externo, começando com o bloco atual, série de instruções incluídas entre chaves e a continuação externa com o bloco delimitador. O bloco atual é o código que contém o local atual, endereço do ponteiro de instrução.

2. Escopo da função. A função atual.

3. Escopo da classe, se o local atual estiver dentro de uma função de membro C ++. O escopo da classe inclui todas as classes base. O avaliador de expressão usa regras de dominância normais.

4. Símbolos globais no módulo atual.

5. Símbolos públicos no programa atual.