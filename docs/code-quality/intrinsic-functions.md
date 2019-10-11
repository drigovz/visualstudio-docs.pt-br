---
title: Funções intrínsecas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: e5b754f32edb86d10b4dd722ea7c6486f8179af6
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018739"
---
# <a name="intrinsic-functions"></a>Funções intrínsecas
Uma expressão em SAL pode ser uma expressão CC++ /, desde que ela seja uma expressão que não tenha efeitos colaterais, por exemplo, + +,--, e chamadas de função tenham efeitos colaterais nesse contexto.  No entanto, o SAL fornece alguns objetos do tipo função e alguns símbolos reservados que podem ser usados em expressões SAL. Eles são chamados de *funções intrínsecas*.

## <a name="general-purpose"></a>Uso Geral
As anotações de função instrinsic a seguir fornecem um utilitário geral para SAL.

|Anotação|Descrição|
|----------------|-----------------|
|`_Curr_`|Um sinônimo para o objeto que está sendo anotado no momento.  Quando a anotação `_At_` estiver em uso, `_Curr_` será o mesmo que o primeiro parâmetro para `_At_`.  Caso contrário, é o parâmetro ou o valor de função/retorno inteiro com o qual a anotação está associada lexicalmente.|
|`_Inexpressible_(expr)`|Expressa uma situação em que o tamanho de um buffer é muito complexo para representar usando uma expressão de anotação — por exemplo, quando é computado examinando um conjunto de dados de entrada e, em seguida, contando os membros selecionados.|
|`_Nullterm_length_(param)`|`param` é o número de elementos no buffer, mas não incluindo um terminador nulo. Ele pode ser aplicado a qualquer buffer de tipo não agregado e não nulo.|
|`_Old_(expr)`|Quando é avaliado em pré-condição, `_Old_` retorna o valor de entrada `expr`.  Quando é avaliado em post-Condition, ele retorna o valor `expr`, pois ele teria sido avaliado na pré-condição.|
|`_Param_(n)`|O parâmetro `n`º para uma função, contando de 1 a `n` e `n` é uma constante integral literal. Se o parâmetro for nomeado, essa anotação será idêntica ao acesso ao parâmetro por nome. **Observação:**  `n` pode se referir aos parâmetros posicionais que são definidos por uma elipse ou podem ser usados em protótipos de função onde os nomes não são usados.|
|`return`|A palavra-C++ chave C/reservada `return` pode ser usada em uma expressão sal para indicar o valor de retorno de uma função.  O valor só está disponível no estado de post; é um erro de sintaxe para usá-lo em pré-estado.|

## <a name="string-specific"></a>Cadeia de caracteres específica
As seguintes anotações de função intrínsecas habilitam a manipulação de cadeias de caracteres. Todas as quatro funções têm a mesma finalidade: para retornar o número de elementos do tipo que é encontrado antes de um terminador nulo. As diferenças são os tipos de dados nos elementos que são referenciados. Observe que, se você quiser especificar o comprimento de um buffer com terminação nula que não é composto por caracteres, use a anotação `_Nullterm_length_(param)` da seção anterior.

|Anotação|Descrição|
|----------------|-----------------|
|`_String_length_(param)`|`param` é o número de elementos na cadeia de caracteres até, mas não incluindo um terminador nulo. Esta anotação é reservada para tipos de cadeia de caracteres.|
|`strlen(param)`|`param` é o número de elementos na cadeia de caracteres até, mas não incluindo um terminador nulo. Essa anotação é reservada para uso em matrizes de caracteres e é semelhante à função de tempo de execução C [strlen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param` é o número de elementos na cadeia de caracteres até (mas não incluindo) um terminador nulo. Essa anotação é reservada para uso em matrizes de caracteres largos e é semelhante à função de tempo de execução C [wcslen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Consulte também

- [Usando anotações de SAL para reduzir defeitos de código do C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Noções básicas de SAL](../code-quality/understanding-sal.md)
- [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotando o comportamento da função](../code-quality/annotating-function-behavior.md)
- [Anotando estruturas e classes](../code-quality/annotating-structs-and-classes.md)
- [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)
- [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)