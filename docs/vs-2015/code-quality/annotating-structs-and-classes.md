---
title: Anotando structs e classes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 6db2202971facb0419db68c04835c8d5c848f528
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271573"
---
# <a name="annotating-structs-and-classes"></a>Anotando estruturas e classes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode anotar os membros de struct e de classe usando anotações que agem como invariáveis – eles devem ser verdadeiros em qualquer chamada de função ou entrada/saída de função que envolva a estrutura delimitadora como um parâmetro ou um valor de resultado.  
  
## <a name="struct-and-class-annotations"></a>Anotações de struct e classe  
  
- `_Field_range_(low, high)`  
  
     O campo está no intervalo (inclusivo) de `low` para `high`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` aplicado ao objeto anotado usando as condições anteriores ou posteriores.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Um campo que tem um tamanho gravável em elementos (ou bytes) conforme especificado por `size`.  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`, `_Field_size_bytes_part_(size, count)``_Field_size_bytes_part_opt_(size, count)`  
  
     Um campo que tem um tamanho gravável em elementos (ou bytes) conforme especificado por `size`e o `count` desses elementos (bytes) que são legíveis.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Um campo que tem o tamanho legível e gravável em elementos (ou bytes) conforme especificado por `size`.  
  
- `_Struct_size_bytes_(size)`  
  
     Um campo que tem o tamanho legível e gravável em elementos (ou bytes) conforme especificado por `size`.  
  
     Aplica-se à declaração struct ou Class.  Indica que um objeto válido desse tipo pode ser maior que o tipo declarado, com o número de bytes sendo especificado por `size`.  Por exemplo:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     O tamanho do buffer, em bytes de um parâmetro `pM` do tipo `MyStruct *`, é então usado como:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Consulte Também  
 [Usando anotações de sal para reduzir os defeitosC++ de C/código](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Compreendendo o SAL](../code-quality/understanding-sal.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Comportamento de função de anotação](../code-quality/annotating-function-behavior.md)   
 [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)   
 [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funções intrínsecas](../code-quality/intrinsic-functions.md)   
 [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)
