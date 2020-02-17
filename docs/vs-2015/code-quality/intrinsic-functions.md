---
title: Funções intrínsecas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: a0a6cd31cbc8cf73cfa2c7e9ee7c096fa56799b9
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277968"
---
# <a name="intrinsic-functions"></a>Funções intrínsecas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma expressão em SAL pode ser uma expressão CC++ /, desde que ela seja uma expressão que não tenha efeitos colaterais, por exemplo, + +,--, e chamadas de função tenham efeitos colaterais nesse contexto.  No entanto, o SAL fornece alguns objetos do tipo função e alguns símbolos reservados que podem ser usados em expressões SAL. Eles são chamados de *funções intrínsecas*.  
  
## <a name="general-purpose"></a>Uso Geral  
 As anotações de função instrinsic a seguir fornecem um utilitário geral para SAL.  
  
|Anotação|DESCRIÇÃO|  
|----------------|-----------------|  
|`_Curr_`|Um sinônimo para o objeto que está sendo anotado no momento.  Quando a anotação de `_At_` estiver em uso, `_Curr_` será o mesmo que o primeiro parâmetro para `_At_`.  Caso contrário, é o parâmetro ou o valor de função/retorno inteiro com o qual a anotação está associada lexicalmente.|  
|`_Inexpressible_(expr)`|Expressa uma situação em que o tamanho de um buffer é muito complexo para representar usando uma expressão de anotação — por exemplo, quando é computado examinando um conjunto de dados de entrada e, em seguida, contando os membros selecionados.|  
|`_Nullterm_length_(param)`|`param` é o número de elementos no buffer até, mas não incluindo um terminador nulo. Ele pode ser aplicado a qualquer buffer de tipo não agregado e não nulo.|  
|`_Old_(expr)`|Quando é avaliado em pré-condição, `_Old_` retorna o valor de entrada `expr`.  Quando é avaliado em post-Condition, ele retorna o valor `expr` como seria avaliado em pré-condição.|  
|`_Param_(n)`|O `n`o parâmetro para uma função, contando de 1 a `n`e `n` é uma constante integral literal. Se o parâmetro for nomeado, essa anotação será idêntica ao acesso ao parâmetro por nome. **Observação:** `n` pode se referir aos parâmetros posicionais que são definidos por uma elipse ou podem ser usados em protótipos de função em que os nomes não são usados.|  
|`return`|A palavra-C++ chave C/reservada `return` pode ser usada em uma expressão sal para indicar o valor de retorno de uma função.  O valor só está disponível no estado de post; é um erro de sintaxe para usá-lo em pré-estado.|  
  
## <a name="string-specific"></a>Cadeia de caracteres específica  
 As seguintes anotações de função intrínsecas habilitam a manipulação de cadeias de caracteres. Todas as quatro funções têm a mesma finalidade: para retornar o número de elementos do tipo que é encontrado antes de um terminador nulo. As diferenças são os tipos de dados nos elementos que são referenciados. Observe que, se você quiser especificar o comprimento de um buffer com terminação nula que não é composto por caracteres, use a anotação `_Nullterm_length_(param)` da seção anterior.  
  
|Anotação|DESCRIÇÃO|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` é o número de elementos na cadeia de caracteres até, mas não incluindo um terminador nulo. Esta anotação é reservada para tipos de cadeia de caracteres.|  
|`strlen(param)`|`param` é o número de elementos na cadeia de caracteres até, mas não incluindo um terminador nulo. Essa anotação é reservada para uso em matrizes de caracteres e é semelhante à função de tempo de execução C [strlen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
|`wcslen(param)`|`param` é o número de elementos na cadeia de caracteres até (mas não incluindo) um terminador nulo. Essa anotação é reservada para uso em matrizes de caracteres largos e é semelhante à função de tempo de execução C [wcslen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
  
## <a name="see-also"></a>Consulte Também  
 [Usando anotações de sal para reduzir os defeitosC++ de C/código](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Compreendendo o SAL](../code-quality/understanding-sal.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Comportamento de função de anotação](../code-quality/annotating-function-behavior.md)   
 [Anotando structs e Classes](../code-quality/annotating-structs-and-classes.md)   
 [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)   
 [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)
