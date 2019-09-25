---
title: Práticas recomendadas e exemplos (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 27570e282c230d4bec47e70aa1bcdd053b75597c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236752"
---
# <a name="best-practices-and-examples-sal"></a>Práticas recomendadas e exemplos (SAL)
Aqui estão algumas maneiras de aproveitar ao máximo a SAL (linguagem de anotação de código-fonte) e evitar alguns problemas comuns.

## <a name="_in_"></a>\_In\_

Se a função deve gravar no elemento, use `_Inout_` em vez de. `_In_` Isso é particularmente relevante em casos de conversão automatizada de macros antigas para SAL. Antes do sal, muitos programadores usaram macros como comentários — macros que `IN`foram `OUT`nomeadas,, `IN_OUT`ou variantes desses nomes. Embora seja recomendável converter essas macros em SAL, também recomendamos que você tenha cuidado ao convertê-las porque o código pode ter sido alterado desde que o protótipo original foi escrito e a macro antiga pode não refletir mais o que o código faz. Seja especialmente cuidadoso com relação `OPTIONAL` à macro comment porque ela é freqüentemente colocada incorretamente, por exemplo, no lado errado de uma vírgula.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="_opt_"></a>\_opt\_

Se o chamador não tiver permissão para passar um ponteiro nulo, `_In_` use ou `_Out_` em vez de `_In_opt_` ou `_Out_opt_`. Isso se aplica mesmo a uma função que verifica seus parâmetros e retorna um erro se ele for nulo quando não deveria ser. Embora ter uma função Verifique seu parâmetro para NULL inesperado e retornar normalmente é uma boa prática de codificação defensiva, isso não significa que a anotação de parâmetro pode ser de um`_*Xxx*_opt_`tipo opcional ().

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}
```

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Pré\_-\_ defensiva e\_pós\_-defesa\_

Se uma função aparecer em um limite de confiança, recomendamos que você use `_Pre_defensive_` a anotação.  O modificador "defensiva" modifica certas anotações para indicar que, no ponto de chamada, a interface deve ser marcada estritamente, mas no corpo da implementação, ela deve assumir que os parâmetros incorretos podem ser passados. Nesse caso, `_In_ _Pre_defensive_` é preferencial em um limite de confiança para indicar que, embora um chamador receba um erro se tentar passar NULL, o corpo da função será analisado como se o parâmetro fosse nulo e qualquer tentativa de fazer referência ao ponteiro sem primeiro a verificação de NULL será sinalizada.  Uma `_Post_defensive_` anotação também está disponível, para uso em retornos de chamada, em que a parte confiável é considerada como o chamador e o código não confiável é o código chamado.

## <a name="_out_writes_"></a>\_Saída\_de gravações\_

O exemplo a seguir demonstra um uso indevido comum de `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

A anotação `_Out_writes_` significa que você tem um buffer. Ele tem `cb` bytes alocados, com o primeiro byte inicializado na saída. Essa anotação não é estritamente errada e é útil expressar o tamanho alocado. No entanto, ele não informa quantos elementos são inicializados pela função.

O exemplo a seguir mostra três maneiras corretas de especificar completamente o tamanho exato da parte inicializada do buffer.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);
```

## <a name="_out_-pstr"></a>\_PSTR\_ out

O uso de `_Out_ PSTR` está quase sempre errado. Isso é interpretado como tendo um parâmetro de saída que aponta para um buffer de caracteres e é encerrado com NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Uma anotação como `_In_ PCSTR` é comum e útil. Ele aponta para uma cadeia de caracteres de entrada que tem terminação nula porque `_In_` a pré-condição de permite o reconhecimento de uma cadeia de caracteres terminada em nulo.

## <a name="_in_-wchar-p"></a>\_No\_ WCHAR * p

`_In_ WCHAR* p`diz que há um ponteiro `p` de entrada que aponta para um caractere. No entanto, na maioria dos casos, essa provavelmente não é a especificação pretendida. Em vez disso, o que é provavelmente pretendido é a especificação de uma matriz terminada em nulo; para fazer isso, use `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

A especificação apropriada de terminação nula não é comum. Use a versão `STR` apropriada para substituir o tipo, conforme mostrado no exemplo a seguir.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}
```

## <a name="_out_range_"></a>\_Fora\_do intervalo\_

Se o parâmetro for um ponteiro e você quiser expressar o intervalo do valor do elemento que é apontado pelo ponteiro, use `_Deref_out_range_` em vez de. `_Out_range_` No exemplo a seguir, o intervalo de * pcbFilled é expresso, não pcbFilled.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);
```

`_Deref_out_range_(0, cbSize)`Não é estritamente necessário para algumas ferramentas porque ela pode ser inferida de `_Out_writes_to_(cbSize,*pcbFilled)`, mas é mostrada aqui para fins de integridade.

## <a name="wrong-context-in-_when_"></a>Contexto errado em \_quando\_

Outro erro comum é usar a avaliação de pós-Estado para pré-condições. No exemplo a seguir, `_Requires_lock_held_` é uma pré-condição.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

A expressão `result` refere-se a um valor de pós-Estado que não está disponível em pré-estado.

## <a name="true-in-_success_"></a>Verdadeiro em \_caso de sucesso\_

Se a função for bem-sucedida quando o valor de retorno for diferente de `return != 0` zero, use como a condição `return == TRUE`de êxito em vez de. Diferente de zero não significa necessariamente a equivalência para o valor real que o compilador fornece `TRUE`. O parâmetro para `_Success_` é uma expressão, e as expressões a seguir são avaliadas como `return != 0`equivalentes `return != FALSE`:, `return` `return != false`, e sem parâmetros ou comparações.

```cpp

// Incorrect
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);
```

## <a name="reference-variable"></a>Variável de referência

Para uma variável de referência, a versão anterior de sal usou o ponteiro implícito como o alvo da anotação e exigia a adição `__deref` de uma para anotações que foram anexadas a uma variável de referência. Essa versão usa o próprio objeto e não requer o adicional `_Deref_`.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);
```

## <a name="annotations-on-return-values"></a>Anotações em valores de retorno

O exemplo a seguir mostra um problema comum em anotações de valor de retorno.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

Neste exemplo, `_Out_opt_` diz que o ponteiro pode ser nulo como parte da pré-condição. No entanto, as pré-condições não podem ser aplicadas ao valor de retorno. Nesse caso, a anotação correta é `_Ret_maybenull_`.

## <a name="see-also"></a>Consulte também

[Usando anotações de SAL para reduzir defeitos de código do C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[Noções básicas de SAL](../code-quality/understanding-sal.md)  
[Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)  
[Anotando o comportamento da função](../code-quality/annotating-function-behavior.md)  
[Anotando estruturas e classes](../code-quality/annotating-structs-and-classes.md)  
[Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)  
[Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[Funções intrínsecas](../code-quality/intrinsic-functions.md)  
