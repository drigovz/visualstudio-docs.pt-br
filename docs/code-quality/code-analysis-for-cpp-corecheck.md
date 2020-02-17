---
title: Referência de verificador das diretrizes principais do C++
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 2c3e1ba77f3f78de3fc1fac4185121ecb42b1b5b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271389"
---
# <a name="c-core-guidelines-checker-reference"></a>Referência de verificador das diretrizes principais do C++

Esta seção lista avisos de verificação de diretrizes de principal do C++. Para obter informações sobre a análise de código, consulte [/Analyze (análise de código)](/cpp/build/reference/analyze-code-analysis) e [início rápido: análiseC++de código para C/](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Alguns avisos pertencem a mais de um grupo, e nem todos os avisos têm um tópico de referência completa.

## <a name="owner_pointer-group"></a>Grupo OWNER_POINTER

[DONT_HEAP_ALLOCATE_MOVABLE_RESULT C26402](C26402.md) Retorne um objeto com escopo em vez de um heap alocado se ele tiver um construtor de movimentação. Consulte [ C++ as diretrizes básicas R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[RESET_OR_DELETE_OWNER C26403](C26403.md) Redefinir ou excluir explicitamente um proprietário\<T > ponteiro '% Variable% '. Consulte [ C++ as diretrizes básicas R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[DONT_DELETE_INVALID C26404](C26404.md) Não exclua um proprietário\<T > que possa estar em estado inválido. Consulte [ C++ as diretrizes básicas R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[DONT_ASSIGN_TO_VALID C26405](C26405.md) Não atribua a um proprietário\<T > que possa estar em um estado válido. Consulte [ C++ as diretrizes básicas R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[DONT_ASSIGN_RAW_TO_OWNER C26406](C26406.md) Não atribua um ponteiro bruto a um proprietário\<T >. Consulte [ C++ as diretrizes básicas R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[DONT_HEAP_ALLOCATE_UNNECESSARILY C26407](C26407.md) Prefira objetos com escopo, não aloque heap desnecessariamente. Consulte [ C++ as diretrizes básicas R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[USE_NOTNULL C26429](C26429.md) O símbolo '% Symbol% ' nunca foi testado quanto à nulidade, ele pode ser marcado como not_null. Consulte [ C++ as diretrizes básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[TEST_ON_ALL_PATHS C26430](C26430.md) O símbolo '% Symbol% ' não é testado quanto à nulidade em todos os caminhos. Consulte [ C++ as diretrizes básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[DONT_TEST_NOTNULL C26431](C26431.md) O tipo de expressão '% expr% ' já é GSL:: not_null. Não teste-o para nullness. Consulte [ C++ as diretrizes básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>RAW_POINTER Group

[NO_RAW_POINTER_ASSIGNMENT C26400](c26400.md) Não atribua o resultado de uma alocação ou uma chamada de função com um proprietário\<T > valor de retorno a um ponteiro bruto; em vez disso, use o proprietário\<T >. Consulte [ C++ as diretrizes básicas I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[DONT_DELETE_NON_OWNER C26401](c26401.md) Não exclua um ponteiro bruto que não seja um proprietário\<T >. Consulte [ C++ as diretrizes básicas I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  retornar um objeto com escopo em vez de um heap alocado se ele tiver um Construtor move. Consulte [ C++ as diretrizes básicas R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[NO_MALLOC_FREE C26408](C26408.md) Evite malloc () e Free (), prefira a versão nothrow de New com Delete. Consulte [ C++ as diretrizes básicas R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[NO_NEW_DELETE C26409](C26409.md) Evite chamar New e Delete explicitamente e, em vez disso, use a > T:: make_unique\<. Consulte [ C++ as diretrizes básicas R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[USE_NOTNULL C26429](C26429.md) O símbolo '% Symbol% ' nunca foi testado quanto à nulidade, ele pode ser marcado como not_null. Consulte [ C++ as diretrizes básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[TEST_ON_ALL_PATHS C26430](C26430.md) O símbolo '% Symbol% ' não é testado quanto à nulidade em todos os caminhos. Consulte [ C++ as diretrizes básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[DONT_TEST_NOTNULL C26431](C26431.md) O tipo de expressão '% expr% ' já é GSL:: not_null. Não teste-o para nullness. Consulte [ C++ as diretrizes básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[NO_POINTER_ARITHMETIC C26481](C26481.md) Não use aritmética de ponteiro. Use o span. Consulte [ C++ limites de diretrizes principais. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[NO_ARRAY_TO_POINTER_DECAY C26485](C26485.md).
A expressão '% expr %': Nenhuma matriz para ponteiro de decaimento. Consulte [ C++ limites de diretrizes principais. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>UNIQUE_POINTER Group

[NO_REF_TO_CONST_UNIQUE_PTR C26410](C26410.md) O parâmetro '% Parameter% ' é uma referência a `const` ponteiro exclusivo, use const T * ou const T & em vez disso. Consulte [ C++ as diretrizes básicas R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[NO_REF_TO_UNIQUE_PTR C26411](C26411.md) O parâmetro '% Parameter% ' é uma referência a um ponteiro exclusivo e nunca é reatribuído ou redefinido. em vez disso, use T * ou T &. Consulte [ C++ as diretrizes básicas R. 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[RESET_LOCAL_SMART_PTR C26414](C26414.md) Mover, copiar, reatribuir ou redefinir um ponteiro inteligente local '% Symbol% '. Consulte [ C++ as diretrizes básicas R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[SMART_PTR_NOT_NEEDED C26415](C26415.md) O parâmetro de ponteiro inteligente '% Symbol% ' é usado somente para acessar o ponteiro contido. Use T * ou T & em vez disso. Consulte [ C++ as diretrizes básicas R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>SHARED_POINTER Group

[RESET_LOCAL_SMART_PTR C26414](C26414.md) Mover, copiar, reatribuir ou redefinir um ponteiro inteligente local '% Symbol% '. Consulte [ C++ as diretrizes básicas R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[SMART_PTR_NOT_NEEDED C26415](C26415.md) O parâmetro de ponteiro inteligente '% Symbol% ' é usado somente para acessar o ponteiro contido. Use T * ou T & em vez disso. Consulte [ C++ as diretrizes básicas R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[NO_RVALUE_REF_SHARED_PTR C26416](C26416.md) O parâmetro de ponteiro compartilhado '% Symbol% ' é passado por referência rvalue. Passe por valor. Consulte [ C++ as diretrizes básicas R. 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[NO_LVALUE_REF_SHARED_PTR C26417](C26417.md) O parâmetro de ponteiro compartilhado '% Symbol% ' é passado por referência e não é redefinido ou reatribuído. Use T * ou T & em vez disso. Consulte [ C++ as diretrizes básicas R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[NO_VALUE_OR_CONST_REF_SHARED_PTR C26418](C26418.md) O parâmetro de ponteiro compartilhado '% Symbol% ' não foi copiado ou movido. Use T * ou T & em vez disso. Consulte [ C++ as diretrizes básicas R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>DECLARAÇÃO de grupo

[NO_GLOBAL_INIT_CALLS C26426](C26426.md) O inicializador global chama uma função não constexpr '% Symbol% '. Consulte [ C++ as diretrizes básicas I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[NO_GLOBAL_INIT_EXTERNS C26427](C26427.md) O inicializador global acessa o objeto externo '% Symbol% '. Consulte [ C++ as diretrizes básicas I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[NO_UNNAMED_RAII_OBJECTS C26444](c26444.md) Evite objetos sem nome com construção e destruição personalizadas. Consulte [es. 84: não (tente) declarar uma variável local sem nome](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Grupo de classe

[DEFINE_OR_DELETE_SPECIAL_OPS C26432](C26432.md) Se você definir ou excluir qualquer operação padrão no tipo '% Symbol% ', defina ou exclua todas elas. Consulte [ C++ as diretrizes principais C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[OVERRIDE_EXPLICITLY C26433](c26433.md) A função '% Symbol% ' deve ser marcada com ' override '. Consulte [C. 128: as funções virtuais devem especificar exatamente uma das virtual, Override ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[DONT_HIDE_METHODS C26434](C26434.md) A função '% symbol_1% ' oculta uma função não virtual '% symbol_2% '. Consulte [ C++ as diretrizes básicas C. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[SINGLE_VIRTUAL_SPECIFICATION C26435](c26435.md) A função '% Symbol% ' deve especificar exatamente um dos ' virtual ', ' override ' ou ' final '. Consulte [C. 128: as funções virtuais devem especificar exatamente uma das virtual, Override ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

[NEED_VIRTUAL_DTOR C26436](C26436.md) O tipo '% Symbol% ' com uma função virtual precisa de um destruidor virtual público ou não virtual protegido. Consulte [ C++ as diretrizes básicas C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[NO_EXPLICIT_DTOR_OVERRIDE C26443](c26443.md) O destruidor de substituição não deve usar especificadores ' override ' ou ' virtual ' explícitos. Consulte [C. 128: as funções virtuais devem especificar exatamente uma das virtual, Override ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="type-group"></a>TIPO de grupo

[DONT_SLICE C26437](C26437.md) Não fatiar. Consulte [ C++ as diretrizes principais es. 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Grupo de estilo

[NO_GOTO C26438](C26438.md) Evite `goto`. Consulte [ C++ as diretrizes principais es. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Grupo de funções

[SPECIAL_NOEXCEPT C26439](C26439.md) Esse tipo de função pode não gerar. Declare-o `noexcept`. Consulte [ C++ as diretrizes básicas F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[DECLARE_NOEXCEPT C26440](C26440.md) A função '% Symbol% ' pode ser declarada `noexcept`. Consulte [ C++ as diretrizes básicas F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[DONT_THROW_IN_NOEXCEPT C26447](c26447.md) A função é declarada **noexcept** , mas chama uma função que pode gerar exceções.
Consulte [ C++ as principais diretrizes: F. 6: se sua função não puder ser lançada, declare-a sem Except](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Grupo de SIMULTANEIDADE

[NO_UNNAMED_GUARDS C26441](C26441.md) Os objetos de proteção devem ser nomeados. Consulte [ C++ as diretrizes básicas CP. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Grupo de CONST

[USE_CONST_REFERENCE_ARGUMENTS C26460](c26460.md) O argumento de referência '% Argument% ' para a função '% function% ' pode ser marcado como `const`. Consulte [ C++ as principais diretrizes con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): o argumento de ponteiro '% Argument% ' para a função '% function% ' pode ser marcado como um ponteiro para `const`. Consulte [ C++ as principais diretrizes con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[USE_CONST_POINTER_FOR_VARIABLE C26462](c26462.md) O valor apontado por '% Variable% ' é atribuído apenas uma vez, marque-o como um ponteiro para `const`. Consulte [ C++ as diretrizes básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[USE_CONST_FOR_ELEMENTS C26463](c26463.md) Os elementos da matriz '% array% ' são atribuídos apenas uma vez, marque os elementos `const`. Consulte [ C++ as diretrizes básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[USE_CONST_POINTER_FOR_ELEMENTS C26464](c26464.md) Os valores apontados por elementos da matriz '% array% ' são atribuídos apenas uma vez, marque os elementos como ponteiro para `const`. Consulte [ C++ as diretrizes básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[USE_CONST_FOR_VARIABLE C26496](c26496.md) A variável '% Variable% ' é atribuída apenas uma vez, marque-a como `const`. Consulte [ C++ as diretrizes básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[USE_CONSTEXPR_FOR_FUNCTION C26497](c26497.md) Esta função% function% pode ser marcada `constexpr` se a avaliação do tempo de compilação for desejada. Consulte [ C++ as diretrizes básicas F. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[USE_CONSTEXPR_FOR_FUNCTIONCALL C26498](c26498.md) Esta chamada de função% function% poderá usar `constexpr` se a avaliação de tempo de compilação for desejada. Consulte [ C++ as principais diretrizes con. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>TIPO de grupo

[NO_CONST_CAST_UNNECESSARY C26465](c26465.md) Não use `const_cast` para converter `const`. `const_cast` não é necessário; a constante ou a volatilidade não está sendo removida por essa conversão. Consulte [ C++ diretrizes básicas tipo. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[NO_STATIC_DOWNCAST_POLYMORPHIC C26466](c26466.md) Não use `static_cast` downcasts. Uma conversão de um tipo polimórfico deve usar dynamic_cast. Consulte [ C++ diretrizes básicas tipo. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[NO_REINTERPRET_CAST_FROM_VOID_PTR C26471](c26471.md) Não use `reinterpret_cast`. Uma conversão de void * pode usar `static_cast`. Consulte [ C++ diretrizes básicas tipo. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[NO_CASTS_FOR_ARITHMETIC_CONVERSION C26472](C26472.md) Não use um `static_cast` para conversões aritméticas. Use a inicialização da chave, gsl:: narrow_cast ou gsl:: narow. Consulte [ C++ diretrizes básicas tipo. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[NO_IDENTITY_CAST C26473](C26473.md) Não converta os tipos de ponteiro nos quais o tipo de origem e o tipo de destino são os mesmos. Consulte [ C++ diretrizes básicas tipo. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[NO_IMPLICIT_CAST C26474](C26474.md) Não converta entre tipos de ponteiro quando a conversão puder ser implícita. Consulte [ C++ diretrizes básicas tipo. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[NO_FUNCTION_STYLE_CASTS C26475](C26475.md) Não use o estilo de função C-casts. Consulte [ C++ as diretrizes básicas es. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[NO_REINTERPRET_CAST C26490](c26490.md) Não use `reinterpret_cast`. Consulte [ C++ diretrizes básicas tipo. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[NO_STATIC_DOWNCAST C26491](c26490.md) Não use `static_cast` downcasts. Consulte [ C++ diretrizes básicas tipo. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[NO_CONST_CAST C26492](c26492.md) Não use `const_cast` para converter `const`. Consulte [ C++ diretrizes básicas tipo. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[NO_CSTYLE_CAST C26493](c26493.md) Não use conversões de estilo C. Consulte [ C++ diretrizes básicas tipo. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[VAR_USE_BEFORE_INIT C26494](c26494.md) A variável '% Variable% ' não foi inicializada. Sempre inicialize um objeto. Consulte [ C++ diretrizes básicas tipo. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[MEMBER_UNINIT C26495](c26495.md) A variável '% Variable% ' não foi inicializada. Sempre inicialize uma variável de membro. Consulte [ C++ diretrizes básicas tipo. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Grupo de limites

[USE_GSL_AT C26446](c26446.md) Prefira usar `gsl::at()` em vez do operador subscrito desmarcado. Consulte [ C++ as principais diretrizes: limites. 4: não use funções e tipos de biblioteca padrão que não são associados-verificados](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[NO_POINTER_ARITHMETIC C26481](C26481.md).
Não use aritmética de ponteiro. Use o span. Consulte [ C++ limites de diretrizes principais. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[NO_DYNAMIC_ARRAY_INDEXING C26482](c26482.md) Indexe somente em matrizes usando expressões de constante. Consulte [ C++ limites de diretrizes principais. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[STATIC_INDEX_OUT_OF_RANGE C26483](c26483.md) O valor% value% está fora dos limites (0,% Bound%) da variável '% Variable% '. Somente indexe em matrizes que usam expressões de constante que estão dentro dos limites da matriz. Consulte [ C++ limites de diretrizes principais. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[NO_ARRAY_TO_POINTER_DECAY C26485](C26485.md) Expressão '% expr% ': nenhuma matriz para decaimento de ponteiro. Consulte [ C++ limites das diretrizes principais. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Grupo de GSL

[NO_SPAN_REF C26445](c26445.md) Uma referência a `gsl::span` ou `std::string_view` pode ser uma indicação de um problema de tempo de vida.
Consulte [ C++ as principais diretrizes GSL. View: views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[USE_GSL_AT C26446](c26446.md) Prefira usar `gsl::at()` em vez do operador subscrito desmarcado. Consulte [ C++ as principais diretrizes: limites. 4: não use funções e tipos de biblioteca padrão que não são associados-verificados](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[USE_GSL_FINALLY C26448](c26448.md) Considere o uso de `gsl::finally` se a ação final for pretendida. Consulte [ C++ as principais diretrizes: GSL. util: Utilities](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md)
`gsl::span` ou `std::string_view` criados de um temporário serão inválidos quando o temporário for invalidado. Consulte [ C++ as principais diretrizes: GSL. View: views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).

## <a name="deprecated-warnings"></a>Avisos preteridos

Os avisos a seguir estão presentes em um conjunto de regra experimental antecipada do verificador de diretrizes de núcleo, mas agora são preteridos e podem ser ignorados com segurança. Os avisos são substituídos pelos avisos na lista acima.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Confira também
[Usando os C++ verificadores de diretrizes principais](using-the-cpp-core-guidelines-checkers.md)
