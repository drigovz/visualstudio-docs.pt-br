---
title: Anotando o comportamento da função
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: b77379d0bb9dbd80f01eadf5209353b3fd12eb1c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446302"
---
# <a name="annotating-function-behavior"></a>Anotando o comportamento da função
Além de anotar os [parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md), você pode anotar as propriedades da função inteira.

## <a name="function-annotations"></a>Anotações de função
As anotações a seguir se aplicam à função como um todo e descrevem como ela se comporta ou o que espera ser verdadeiro.

|Anotação|Descrição|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Não se destina a ser autônomo; em vez disso, é um predicado a ser usado com a anotação `_When_`. Para obter mais informações, consulte [especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> O parâmetro `name` é uma cadeia de caracteres arbitrária que também aparece em uma anotação `_Function_class_` na declaração de algumas funções.  `_Called_from_function_class_` retornará zero, se a função que está sendo analisada no momento for anotada usando `_Function_class_` que tem o mesmo valor de `name`; caso contrário, retornará zero.|
|`_Check_return_`|Anota um valor de retorno e declara que o chamador deve inspecioná-lo. O verificador relatará um erro se a função for chamada em um contexto void.|
|`_Function_class_(name)`|O parâmetro `name` é uma cadeia de caracteres arbitrária que é designada pelo usuário.  Ele existe em um namespace que é diferente de outros namespaces. Uma função, um ponteiro de função ou, mais útil — um tipo de ponteiro de função pode ser designado como pertencente a uma ou mais classes de função.|
|`_Raises_SEH_exception_`|Anota uma função que sempre gera uma exceção SEH (manipulador de exceção estruturada), sujeita às condições `_When_` e `_On_failure_`. Para obter mais informações, consulte [especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|Anota uma função que pode, opcionalmente, gerar uma exceção SEH, sujeita às condições `_When_` e `_On_failure_`.|
|`_Must_inspect_result_`|Anota qualquer valor de saída, incluindo o valor de retorno, os parâmetros e os globais.  O analisador relatará um erro se o valor no objeto anotado não for inspecionado posteriormente. "Inspeção" inclui se ele é usado em uma expressão condicional, é atribuído a um parâmetro de saída ou global, ou é passado como um parâmetro.  Para valores de retorno, `_Must_inspect_result_` implica `_Check_return_`.|
|`_Use_decl_annotations_`|Pode ser usado em uma definição de função (também conhecida como um corpo de função) no lugar da lista de anotações no cabeçalho.  Quando `_Use_decl_annotations_` é usado, as anotações que aparecem em um cabeçalho dentro do escopo para a mesma função são usadas como se elas também estejam presentes na definição que tem a anotação `_Use_decl_annotations_`.|

## <a name="successfailure-annotations"></a>Anotações de êxito/falha
Uma função pode falhar e, quando isso acontecer, seus resultados poderão estar incompletos ou diferentes dos resultados quando a função for bem-sucedida.  As anotações na lista a seguir fornecem maneiras de expressar o comportamento de falha.  Para usar essas anotações, você deve habilitá-las para determinar o sucesso; Portanto, uma anotação `_Success_` é necessária.  Observe que `NTSTATUS` e `HRESULT` já têm uma anotação `_Success_` incorporada a eles; no entanto, se você especificar sua própria anotação `_Success_` em `NTSTATUS` ou `HRESULT`, ela substituirá a anotação interna.

|Anotação|Descrição|
|----------------|-----------------|
|`_Always_(anno_list)`|Equivalente a `anno_list _On_failure_(anno_list)`; ou seja, as anotações em `anno_list` se aplicam se a função foi ou não com sucesso.|
|`_On_failure_(anno_list)`|Para ser usado somente quando `_Success_` também é usado para anotar a função, seja explicitamente ou implicitamente por meio de `_Return_type_success_` em um typedef. Quando a anotação `_On_failure_` está presente em um parâmetro de função ou valor de retorno, cada anotação em `anno_list` (Anno) se comporta como se fosse codificada como `_When_(!expr, anno)`, em que `expr` é o parâmetro para a anotação `_Success_` necessária. Isso significa que o aplicativo implícito de `_Success_` para todas as pós-condições não se aplica ao `_On_failure_`.|
|`_Return_type_success_(expr)`|Pode ser aplicado a um typedef. Indica que todas as funções que retornam esse tipo e não têm explicitamente `_Success_` são anotadas como se tivessem `_Success_(expr)`. Não é possível usar `_Return_type_success_` em uma função ou um typedef de ponteiro de função.|
|`_Success_(expr)`|`expr` é uma expressão que produz um Rvalue. Quando a anotação `_Success_` está presente em uma declaração ou definição de função, cada anotação (`anno`) na função e em pós-condição se comporta como se fosse codificada como `_When_(expr, anno)`. A anotação `_Success_` pode ser usada somente em uma função, não em seus parâmetros ou tipo de retorno. Pode haver no máximo uma anotação `_Success_` em uma função e não pode estar em nenhuma `_When_`, `_At_` ou `_Group_`. Para obter mais informações, consulte [especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Consulte também

- [Usando anotações de SAL para reduzir defeitos de código do C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Noções básicas de SAL](../code-quality/understanding-sal.md)
- [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotando estruturas e classes](../code-quality/annotating-structs-and-classes.md)
- [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)
- [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funções intrínsecas](../code-quality/intrinsic-functions.md)
- [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)
