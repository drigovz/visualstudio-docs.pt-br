---
title: Operador de contexto (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6351dd9db7e6f8f29bdd15f376f84511c64bfe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161531"
---
# <a name="context-operator-c"></a>Operador de contexto (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar o operador de contexto em C++ para qualificar um local de ponto de interrupção, um nome de variável ou uma expressão. O operador de contexto é útil para especificar um nome de um escopo externo que, de outra forma, é oculto por um nome local.  
  
## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Sintaxe  
 Há duas maneiras de especificar o contexto:  
  
1. {,,[*module*] } *expression*  
  
     As chaves devem conter duas vírgulas e o nome do módulo (executável ou DLL) ou o caminho completo.  
  
     Por exemplo, para definir um ponto de interrupção na função `SomeFunction` de EXAMPLE.dll:  
  
    ```cpp  
    {,,EXAMPLE.dll}SomeFunction  
    ```  
  
2. *módulo*! *expressão* de  
  
    ```cpp  
    EXAMPLE.dll!SomeFunction  
    ```  
  
- *Module* é o nome de um módulo. Você pode usar um caminho completo para resolver a ambiguidade entre módulos com o mesmo nome.  
  
   Se o caminho do *módulo* incluir uma vírgula, um espaço inserido ou uma chave, você deverá usar aspas em volta do caminho para que o analisador de contexto possa reconhecer corretamente a cadeia de caracteres. As aspas simples são consideradas parte de um nome de arquivo do Windows, portanto, você deve usar aspas duplas. Por exemplo,  
  
  ```cpp  
  {,,"a long, long, library name.dll"} g_Var  
  ```  
  
- *expression* é qualquer expressão de C++ válida que seja resolvida para um destino válido, como um nome de função, um nome de variável ou um endereço de ponteiro no *módulo*.  
  
  Quando o avaliador de expressão localiza um símbolo em uma expressão, procura pelo símbolo na seguinte ordem:  
  
1. Escopo léxico externo, começando com o bloco atual, série de instruções incluídas entre chaves e a continuação externa com o bloco delimitador. O bloco atual é o código que contém o local atual, endereço do ponteiro de instrução.  
  
2. Escopo da função. A função atual.  
  
3. Escopo da classe, se o local atual estiver dentro de uma função de membro C ++. O escopo da classe inclui todas as classes base. O avaliador de expressão usa regras de dominância normais.  
  
4. Símbolos globais no módulo atual.  
  
5. Símbolos públicos no programa atual.
