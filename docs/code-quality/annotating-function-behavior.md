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
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: c7ff2551f3a99bf13909f9db3b1659482246e957
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919625"
---
# <a name="annotating-function-behavior"></a>Anotando o comportamento da função
Além de anotar os [parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md), você pode anotar as propriedades da função inteira.

## <a name="function-annotations"></a>Anotações de função
As anotações a seguir se aplicam à função como um todo e descrevem como ela se comporta ou o que espera ser verdadeiro.

|Anotação|Descrição|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Não se destina a ser autônomo; em vez disso, é um predicado a ser `_When_` usado com a anotação. Para obter mais informações, consulte [especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> O `name` parâmetro é uma cadeia de caracteres arbitrária que também aparece `_Function_class_` em uma anotação na declaração de algumas funções.  `_Called_from_function_class_`retorna zero se a função que está sendo analisada no momento é anotada `_Function_class_` usando que tem o mesmo valor `name`de; caso contrário, retorna zero.|
|`_Check_return_`|Anota um valor de retorno e declara que o chamador deve inspecioná-lo. O verificador relatará um erro se a função for chamada em um contexto void.|
|`_Function_class_(name)`|O `name` parâmetro é uma cadeia de caracteres arbitrária que é designada pelo usuário.  Ele existe em um namespace que é diferente de outros namespaces. Uma função, um ponteiro de função ou, mais útil — um tipo de ponteiro de função pode ser designado como pertencente a uma ou mais classes de função.|
|`_Raises_SEH_exception_`|Anota uma função que sempre gera uma exceção SEH (manipulador de exceção estruturada), sujeita `_When_` a `_On_failure_` e condições. Para obter mais informações, consulte [especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|Anota uma função que pode, opcionalmente, gerar uma exceção SEH, sujeita `_When_` a `_On_failure_` e condições.|
|`_Must_inspect_result_`|Anota qualquer valor de saída, incluindo o valor de retorno, os parâmetros e os globais.  O analisador relatará um erro se o valor no objeto anotado não for inspecionado posteriormente. "Inspeção" inclui se ele é usado em uma expressão condicional, é atribuído a um parâmetro de saída ou global, ou é passado como um parâmetro.  Para valores de retorno `_Must_inspect_result_` , `_Check_return_`implica.|
|`_Use_decl_annotations_`|Pode ser usado em uma definição de função (também conhecida como um corpo de função) no lugar da lista de anotações no cabeçalho.  Quando `_Use_decl_annotations_` é usado, as anotações que aparecem em um cabeçalho dentro do escopo para a mesma função são usadas como se elas também estiverem presentes na definição que tem a `_Use_decl_annotations_` anotação.|

## <a name="successfailure-annotations"></a>Anotações de êxito/falha
Uma função pode falhar e, quando isso acontecer, seus resultados poderão estar incompletos ou diferentes dos resultados quando a função for bem-sucedida.  As anotações na lista a seguir fornecem maneiras de expressar o comportamento de falha.  Para usar essas anotações, você deve habilitá-las para determinar o sucesso; Portanto, uma `_Success_` anotação é necessária.  Observe que `NTSTATUS` e `HRESULT` já tem uma `_Success_` anotação interna. no entanto, se você especificar sua própria `_Success_` anotação em `NTSTATUS` ou `HRESULT`, ela substituirá a anotação interna.

|Anotação|Descrição|
|----------------|-----------------|
|`_Always_(anno_list)`|Equivalente a `anno_list _On_failure_(anno_list)`; ou seja, as anotações em `anno_list` aplicaram se a função foi ou não concluída com sucesso.|
|`_On_failure_(anno_list)`|Para ser usado somente quando `_Success_` o também é usado para anotar a função, seja explicitamente ou implicitamente por `_Return_type_success_` meio de um typedef. Quando a `_On_failure_` anotação está presente em um parâmetro de função ou valor de retorno, cada `anno_list` anotação em (Anno) se comporta como se fosse codificada como `_When_(!expr, anno)`, em `expr` que é o parâmetro para a `_Success_` anotação necessária. Isso significa que o aplicativo implícito do `_Success_` para todas as pós-condições não `_On_failure_`se aplica ao.|
|`_Return_type_success_(expr)`|Pode ser aplicado a um typedef. Indica que todas as funções que retornam esse tipo e que não `_Success_` possuem explicitamente são anotadas como se `_Success_(expr)`tivessem. `_Return_type_success_`Não pode ser usado em uma função ou um typedef de ponteiro de função.|
|`_Success_(expr)`|`expr`é uma expressão que produz um Rvalue. Quando a `_Success_` anotação está presente em uma declaração ou definição de função, cada anotação`anno`() na função e em pós-condição se comporta como se fosse codificada como `_When_(expr, anno)`. A `_Success_` anotação pode ser usada somente em uma função, não em seus parâmetros ou tipo de retorno. Pode haver no máximo `_Success_` uma anotação em uma função e não pode estar em nenhuma `_When_`, `_At_`ou `_Group_`. Para obter mais informações, consulte [especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Consulte também

- [Usando anotações de SAL para reduzir defeitos de código do C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Noções básicas de SAL](../code-quality/understanding-sal.md)
- [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotando estruturas e classes](../code-quality/annotating-structs-and-classes.md)
- [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)
- [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funções intrínsecas](../code-quality/intrinsic-functions.md)
- [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)