---
title: Expressões no depurador | Microsoft Docs
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ab66f288ad8442b6f2b5aab3499e2c1f3857632
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302164"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Expressões no depurador do Visual Studio
O depurador do Visual Studio inclui os avaliadores de expressão que funcionam quando você insere uma expressão na caixa de diálogo **QuickWatch**, na janela **Inspeção** ou na janela **Imediato**. Os avaliadores de expressão também estão no trabalho na janela **Pontos de interrupção** e em muitos outros locais no depurador.

As seções a seguir descrevem limitações de avaliação de expressão para idiomas suportados pelo Visual Studio.

## <a name="f-expressions-are-not-supported"></a>As expressões F# não são suportadas
F# expressões não são reconhecidas. Se você estiver depurando o código F#, você precisa traduzir suas expressões em sintaxe C# antes de inserir as expressões em uma janela de depurador ou caixa de diálogo. Quando você converter expressões de F# em C#, certifique-se de que C# usa o operador `==` para testar a igualdade, enquanto F# usa o `=` único.

## <a name="c-expressions"></a>Expressões C++
Para obter informações sobre o uso de operadores de contexto com expressões em C++, consulte [Context Operator (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>Expressões sem suporte em C++

#### <a name="constructors-destructors-and-conversions"></a>Construtores, destruidores e conversões
Você não pode chamar um construtor ou destruidor para um objeto, seja explicitamente ou implicitamente. Por exemplo, a expressão a seguir chama explicitamente um construtor e resulta em uma mensagem de erro:

```C++
my_date( 2, 3, 1985 )
```

Você não pode chamar uma função de conversão se o destino da conversão for uma classe. Essa conversão envolve a construção de um objeto. Por exemplo, se `myFraction` for uma instância de `CFraction`, que define o operador da função de conversão `FixedPoint`, a expressão a seguir resultará em erro:

```C++
(FixedPoint)myFraction
```

Não é possível chamar os operadores novos ou apagar. Por exemplo, a seguinte expressão não é suportada:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Macros de pré-processador
As macros do pré-processador não são suportadas no depurador. Por exemplo, se `VALUE` uma constante `#define VALUE 3`for declarada `VALUE` como: , você não poderá usar na janela **Relógio.** Para evitar essa limitação, você deve substituir `#define`'s por enums e funções sempre que possível.

### <a name="using-namespace-declarations"></a>usando declarações de namespace
Você não `using namespace` pode usar declarações.  Para acessar um nome de tipo ou variável fora do namespace atual, você deve usar o nome totalmente qualificado.

### <a name="anonymous-namespaces"></a>Namespaces anônimos
Espaços de nomes anônimos não são suportados. Se você tiver o seguinte `test` código, não poderá adicionar à janela do relógio:

```C++
namespace mars
{
    namespace
    {
        int test = 0;
    }
}
int main()
{
    // Adding a watch on test does not work.
    mars::test++;
    return 0;
}

```

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Usando funções intrínsecas de depurador para manter o estado
As funções intrínsecas do depurador oferecem uma maneira de chamar determinadas funções C/C++ em expressões sem alterar o estado do aplicativo.

Funções intrínsecas do depurador:

- São certamente seguras: executar uma função intrínseca do depurador não corromperá o processo que está sendo depurado.

- São permitidas em todas as expressões, mesmo em cenários onde os efeitos colaterais e a avaliação de função não são permitidos.

- Trabalham em cenários onde as chamadas de funções normais não são possíveis, por exemplo, depurar um minidespejo.

  As funções intrínsecas do depurador também podem tornar mais convenientes as expressões de avaliação. Por exemplo, `strncmp(str, "asd")` é muito mais fácil escrever `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`em uma condição de ponto de ruptura do que . )

|Área|Funções intrínsecas|
|----------|-------------------------|
|**Comprimento da cadeia de caracteres**|[strlen, wcslen,](https://docs.microsoft.com/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l) [strnlen, wcsnlen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Comparação de cadeias de caracteres**|[strcmp, wcscmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Pesquisa de cadeias de caracteres**|[strchr, wcschr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](https://docs.microsoft.com/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy,](https://docs.microsoft.com/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy) [DecodePointer,](https://docs.microsoft.com/previous-versions/bb432242%28v%3dvs.85%29) [GetLastError,](https://docs.microsoft.com/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) [TlsGetValue](https://docs.microsoft.com/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](https://docs.microsoft.com/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [WindowsCompareStringOrdinal,](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal) [WindowsGetStringLen,](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringlen) [WindowsGetStringRawBuffer](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Essas funções exigem que o processo que está sendo depurado seja executado no Windows 8. Depurar os arquivos de despejo gerados a partir de um dispositivo do Windows 8 também exige que o computador do Visual Studio esteja executando o Windows 8. No entanto, se você estiver depurando um dispositivo do Windows 8 remotamente, o computador do Visual Studio poderá executar o Windows 7.|
|**Diversos**|__log2 // Retorna a base de log 2 de um inteiro especificado, arredondado para o inteiro inferior mais próximo.<br /><br />__findNonNull, DecodeHString, DecodeWinRTRestrictedException, DynamicCast, DynamicMemberLookup, GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx // Concorrência::array<>::operator[index<>] e operator(index<>)<br /><br />ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)<br /><br />ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] e operador(tiled_index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_idx // Simultâneo::array_view<>::operadores (<> de índices) e operadores (<> de índice)<br /><br />ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operador(int, int, ...)<br /><br />ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operador[tiled_index<>] e operador(tiled_index<>)<br /><br />TreeTraverse_Init // Inicia uma nova travessia de árvores<br /><br />TreeTraverse_Next // Retorna os nódulos em uma árvore<br /><br />TreeTraverse_Skip // Salta os nódulos em uma travessia de árvore pendente'|

## <a name="ccli---unsupported-expressions"></a>C++/CLI - Expressões não suportadas

- Elencos que envolvam ponteiros, ou moldes definidos pelo usuário, não são suportados.

- A comparação e a atribuição de objetos não são suportadas.

- Operadores sobrecarregados e funções sobrecarregadas não são suportados.

- Boxe e unboxing não são suportados.

- `Sizeof`operador não é suportado.

## <a name="c---unsupported-expressions"></a>C# - Expressões não suportadas

### <a name="dynamic-objects"></a>Objetos dinâmicos
Você pode usar variáveis em expressões dedepurador que são digitadas estáticamente como dinâmicas. Quando os <xref:System.Dynamic.IDynamicMetaObjectProvider> objetos que são implementados são avaliados na janela Relógio, um nó de exibição dinâmica é adicionado. O nó do Modo de Exibição Dinâmico exibe membros do objeto, mas não permite editar os valores dos membros.

Os seguintes recursos de objetos dinâmicos não têm suporte:

- Os operadores `+=` `-=`compostos, e `%=` `/=``*=`

- Várias conversões, inclusive conversões numéricas e conversões de tipo de argumento

- Chamadas de método com mais de dois argumentos

- Getters da propriedade com mais de dois argumentos

- Setters de propriedade com argumentos

- Atribuição a um indexador

- Operadores boolianos `&&` e `||`

### <a name="anonymous-methods"></a>Métodos anônimos
A criação de novos métodos anônimos não é suportada.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - Expressões não suportadas

### <a name="dynamic-objects"></a>Objetos dinâmicos
Você pode usar variáveis em expressões dedepurador que são digitadas estáticamente como dinâmicas. Quando os objetos que implementam o <xref:System.Dynamic.IDynamicMetaObjectProvider> são avaliados na janela Relógio, um nó de exibição dinâmica é adicionado. O nó do Modo de Exibição Dinâmico exibe membros do objeto, mas não permite editar os valores dos membros.

Os seguintes recursos de objetos dinâmicos não têm suporte:

- Os operadores `+=` `-=`compostos, e `%=` `/=``*=`

- Várias conversões, inclusive conversões numéricas e conversões de tipo de argumento

- Chamadas de método com mais de dois argumentos

- Getters da propriedade com mais de dois argumentos

- Setters de propriedade com argumentos

- Atribuição a um indexador

- Operadores boolianos `&&` e `||`

### <a name="local-constants"></a>Constantes locais
As constantes locais não têm suporte.

### <a name="import-aliases"></a>Aliases de importação
Os pseudônimos de importação não são suportados.

### <a name="variable-declarations"></a>Declarações de variável
Você não pode declarar novas variáveis explícitas nas janelas do depurador. No entanto, você pode atribuir novas variáveis implícitas dentro da janela **Imediato.** Essas variáveis implícitas são escopo da sessão de depuração e não são acessíveis fora do depurador. Por exemplo, `o = 5` a declaração cria `o` implicitamente uma nova variável e atribui o valor 5 a ela. Tais variáveis implícitas são do tipo **Objeto,** a menos que o tipo possa ser inferido pelo depurador.

### <a name="unsupported-keywords"></a>Palavras-chave sem suporte

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- Namespace ou módulo nível palavras-chave, tais como `End Sub` ou `Module`.

## <a name="see-also"></a>Confira também
- [Especificadores de formato em C++](../debugger/format-specifiers-in-cpp.md)
- [Operador de Contexto (C++)](../debugger/context-operator-cpp.md)
- [Especificadores de formato em C #](../debugger/format-specifiers-in-csharp.md)
- [Pseudovariáveis](../debugger/pseudovariables.md)
