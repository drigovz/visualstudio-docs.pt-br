---
title: Especificando quando e onde uma anotação se aplica | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: ba14fdbc23968fcaf10355f73517ab6cd54f8797
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923677"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Especificando quando e onde uma anotação se aplica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando uma anotação condicional, ele pode exigir outras anotações para especificar que para o analisador.  Por exemplo, se uma função tiver uma variável que pode ser síncrono ou assíncrono, a função se comporta da seguinte maneira: No caso síncrono sempre eventualmente tenha êxito, mas no caso assíncrono relata um erro se ele não conseguir obter êxito imediatamente. Quando a função é chamada de forma síncrona, verificar o valor do resultado não fornece nenhum valor para o analisador de código porque ele não poderia ter retornado.  No entanto, quando a função é chamada de forma assíncrona e o resultado da função não estiver marcado, pode ocorrer um erro grave. Este exemplo ilustra uma situação em que você pode usar o `_When_` anotação — descrito mais adiante neste artigo — para habilitar a verificação.  
  
## <a name="structural-annotations"></a>Anotações estruturais  
 Para controlar quando e onde aplicam de anotações, use as seguintes anotações estruturais.  
  
|Anotação|Descrição|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` é uma expressão que produz um lvalue. As anotações na `anno-list` são aplicadas ao objeto que é nomeado pelo `expr`. Para cada anotação na `anno-list`, `expr` é interpretado em pré-condição se a anotação é interpretada em pré-condição e, na pós-condição de se a anotação é interpretada em pós-condições.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` é uma expressão que produz um lvalue. As anotações na `anno-list` são aplicadas ao objeto que é nomeado pelo `expr`. Para cada anotação na `anno-list`, `expr` é interpretado em pré-condição se a anotação é interpretada na pré-condição e na pós-condição de se a anotação é interpretada em pós-condições.<br /><br /> `iter` é o nome de uma variável que tem como escopo a anotação (inclusiva de `anno-list`). `iter` tem um tipo implícito `long`. Variáveis de nomes idêntico em qualquer escopo delimitador estão ocultos da avaliação.<br /><br /> `elem-count` é uma expressão que é avaliada como um inteiro.|  
|`_Group_(anno-list)`|As anotações no `anno-list` são considerados para ter qualquer qualificador que aplica-se para a anotação de grupo é aplicada a cada anotação.|  
|`_When_(expr, anno-list)`|`expr` é uma expressão que pode ser convertida em `bool`. Quando ele for diferente de zero (`true`), as anotações que são especificadas em `anno-list` são considerados aplicável.<br /><br /> Por padrão, para cada anotação na `anno-list`, `expr` é interpretado como usando os valores de entrada, se a anotação é uma pré-condição, e como usar os valores de saída se a anotação é uma pós condição de. Para substituir o padrão, você pode usar o `_Old_` intrínseco quando você avalia uma pós-condição de para indicar que os valores de entrada devem ser usados. **Observação:**  Anotações diferentes podem ser habilitadas como consequência usando `_When_` se um valor mutável — por exemplo, `*pLength`— está envolvido porque o resultado avaliado da `expr` na pré-condição pode ser diferente do seu resultado avaliado em pós-condições.|  
  
## <a name="see-also"></a>Consulte também  
 [Usando anotações de SAL para reduzir defeitos de código C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Noções básicas de SAL](../code-quality/understanding-sal.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotando o comportamento da função](../code-quality/annotating-function-behavior.md)   
 [Anotando estruturas e Classes](../code-quality/annotating-structs-and-classes.md)   
 [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)   
 [Funções intrínsecas](../code-quality/intrinsic-functions.md)   
 [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)
