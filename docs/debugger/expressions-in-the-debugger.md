---
title: Expressões no depurador | Microsoft Docs
description: Editar e continuar está disponível para projetos do Visual C#. Saiba quais edições têm suporte e como pode controlar se, e quando, suas edições são aplicadas.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 28d04ce836316024eb4aef9f1b4a9955d98dbba8
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862861"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Expressões no depurador do Visual Studio
O depurador do Visual Studio inclui os avaliadores de expressão que funcionam quando você insere uma expressão na caixa de diálogo **QuickWatch**, na janela **Inspeção** ou na janela **Imediato**. Os avaliadores de expressão também estão no trabalho na janela **Pontos de interrupção** e em muitos outros locais no depurador.

As seções a seguir descrevem as limitações de avaliação de expressão para idiomas com suporte no Visual Studio.

## <a name="f-expressions-are-not-supported"></a>Não há suporte para expressões F #
Expressões F # não são reconhecidas. Se estiver depurando o código F #, você precisará converter suas expressões em sintaxe C# antes de inserir as expressões em uma janela ou caixa de diálogo do depurador. Quando você converter expressões de F# em C#, certifique-se de que C# usa o operador `==` para testar a igualdade, enquanto F# usa o `=` único.

## <a name="c-expressions"></a>Expressões C++
Para obter informações sobre como usar operadores de contexto com expressões em C++, consulte [Context Operator (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>Expressões sem suporte em C++

#### <a name="constructors-destructors-and-conversions"></a>Construtores, destruidores e conversões
Você não pode chamar um construtor ou destruidor para um objeto, explícita ou implicitamente. Por exemplo, a expressão a seguir chama explicitamente um construtor e resulta em uma mensagem de erro:

```C++
my_date( 2, 3, 1985 )
```

Você não pode chamar uma função de conversão se o destino da conversão for uma classe. Essa conversão envolve a construção de um objeto. Por exemplo, se `myFraction` for uma instância de `CFraction`, que define o operador da função de conversão `FixedPoint`, a expressão a seguir resultará em erro:

```C++
(FixedPoint)myFraction
```

Você não pode chamar os operadores New ou Delete. Por exemplo, não há suporte para a seguinte expressão:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Macros de pré-processador
Não há suporte para macros de pré-processador no depurador. Por exemplo, se uma constante `VALUE` for declarada como: `#define VALUE 3` , você não poderá usar `VALUE` na janela **Watch** . Para evitar essa limitação, você deve substituir as `#define` enumerações e funções sempre que possível.

### <a name="using-namespace-declarations"></a>usando declarações de namespace
Você não pode usar `using namespace` declarações.  Para acessar um nome de tipo ou variável fora do namespace atual, você deve usar o nome totalmente qualificado.

### <a name="anonymous-namespaces"></a>Namespaces anônimos
Não há suporte para namespaces anônimos. Se você tiver o código a seguir, não poderá adicionar `test` à janela Watch:

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

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Usando funções intrínsecas do depurador para manter o estado
As funções intrínsecas do depurador oferecem uma maneira de chamar determinadas funções C/C++ em expressões sem alterar o estado do aplicativo.

Funções intrínsecas do depurador:

- São certamente seguras: executar uma função intrínseca do depurador não corromperá o processo que está sendo depurado.

- São permitidas em todas as expressões, mesmo em cenários onde os efeitos colaterais e a avaliação de função não são permitidos.

- Trabalham em cenários onde as chamadas de funções normais não são possíveis, por exemplo, depurar um minidespejo.

  As funções intrínsecas do depurador também podem tornar mais convenientes as expressões de avaliação. Por exemplo, `strncmp(str, "asd")` é muito mais fácil escrever uma condição de ponto de interrupção do que `str[0] == 'a' && str[1] == 's' && str[2] == 'd'` . )

|Área|Funções intrínsecas|
|----------|-------------------------|
|**Comprimento da cadeia de caracteres**|[strlen, wcslen](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Comparação de cadeias de caracteres**|[strcmp, wcscmp](/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Pesquisa de cadeias de caracteres**|[strchr, wcschr](/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy](/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](/previous-versions/bb432242(v=vs.85)), [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [WindowsCompareStringOrdinal](/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [WindowsGetStringLen](/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Essas funções exigem que o processo que está sendo depurado seja executado no Windows 8. Depurar os arquivos de despejo gerados a partir de um dispositivo do Windows 8 também exige que o computador do Visual Studio esteja executando o Windows 8. No entanto, se você estiver depurando um dispositivo do Windows 8 remotamente, o computador do Visual Studio poderá executar o Windows 7.|
|**Diversos**|__log2//retorna a base de log 2 de um inteiro especificado, arredondado para o número inteiro mais próximo.<br /><br />__findNonNull, DecodeHString, DecodeWinRTRestrictedException, DynamicCast, DynamicMemberLookup, GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx, Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx//Concurrency:: array<>:: operator [index<>] e Operator (índice<>)<br /><br />ConcurrencyArray_OperatorBracket_int//Concurrency:: array<>:: Operator (int, int,...)<br /><br />ConcurrencyArray_OperatorBracket_tidx//Concurrency:: array<>:: operator [tiled_index<>] e operador (tiled_index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_idx//Concurrency:: array_view<>:: operator [index<>] e Operator (index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_int//Concurrency:: array_view<>:: Operator (int, int,...)<br /><br />ConcurrencyArrayView_OperatorBracket_tidx//Concurrency:: array_view<>:: operator [tiled_index<>] e operador (tiled_index<>)<br /><br />TreeTraverse_Init//Inicializa uma nova passagem de árvore<br /><br />TreeTraverse_Next//retorna nós em uma árvore<br /><br />TreeTraverse_Skip//ignora nós em uma árvore de percurso pendente '|

## <a name="ccli---unsupported-expressions"></a>C++/CLI-expressões sem suporte

- Não há suporte para conversões que envolvem ponteiros ou conversões definidas pelo usuário.

- Não há suporte para comparação de objetos e atribuição.

- Não há suporte para operadores sobrecarregados e funções sobrecarregadas.

- Não há suporte para boxing e unboxing.

- `Sizeof` Não há suporte para o operador.

## <a name="c---unsupported-expressions"></a>C# – expressões sem suporte

### <a name="dynamic-objects"></a>Objetos dinâmicos
Você pode usar variáveis em expressões de depurador que são digitadas estaticamente como dinâmicas. Quando os objetos implementados <xref:System.Dynamic.IDynamicMetaObjectProvider> são avaliados no janela inspeção, um nó de exibição dinâmica é adicionado. O nó do Modo de Exibição Dinâmico exibe membros do objeto, mas não permite editar os valores dos membros.

Os seguintes recursos de objetos dinâmicos não têm suporte:

- Os operadores compostos `+=` , `-=` , `%=` , `/=` e `*=`

- Várias conversões, inclusive conversões numéricas e conversões de tipo de argumento

- Chamadas de método com mais de dois argumentos

- Getters da propriedade com mais de dois argumentos

- Setters de propriedade com argumentos

- Atribuição a um indexador

- Operadores boolianos `&&` e `||`

### <a name="anonymous-methods"></a>Métodos anônimos
Não há suporte para a criação de novos métodos anônimos.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic-expressões sem suporte

### <a name="dynamic-objects"></a>Objetos dinâmicos
Você pode usar variáveis em expressões de depurador que são digitadas estaticamente como dinâmicas. Quando os objetos que implementam o <xref:System.Dynamic.IDynamicMetaObjectProvider> são avaliados no janela inspeção, um nó de exibição dinâmica é adicionado. O nó do Modo de Exibição Dinâmico exibe membros do objeto, mas não permite editar os valores dos membros.

Os seguintes recursos de objetos dinâmicos não têm suporte:

- Os operadores compostos `+=` , `-=` , `%=` , `/=` e `*=`

- Várias conversões, inclusive conversões numéricas e conversões de tipo de argumento

- Chamadas de método com mais de dois argumentos

- Getters da propriedade com mais de dois argumentos

- Setters de propriedade com argumentos

- Atribuição a um indexador

- Operadores boolianos `&&` e `||`

### <a name="local-constants"></a>Constantes locais
As constantes locais não têm suporte.

### <a name="import-aliases"></a>Aliases de importação
Não há suporte para aliases de importação.

### <a name="variable-declarations"></a>Declarações de variável
Você não pode declarar novas variáveis explícitas nas janelas do depurador. No entanto, você pode atribuir novas variáveis implícitas dentro da janela **imediata** . Essas variáveis implícitas têm como escopo a sessão de depuração e não podem ser acessadas fora do depurador. Por exemplo, a instrução `o = 5` Cria implicitamente uma nova variável `o` e atribui o valor 5 a ela. Essas variáveis implícitas são do tipo **Object** , a menos que o tipo possa ser inferido pelo depurador.

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

- Palavras-chave de namespace ou nível de módulo, como `End Sub` ou `Module` .

## <a name="see-also"></a>Confira também
- [Especificadores de formato em C++](../debugger/format-specifiers-in-cpp.md)
- [Operador de contexto (C++)](../debugger/context-operator-cpp.md)
- [Especificadores de formato em C #](../debugger/format-specifiers-in-csharp.md)
- [Pseudovariáveis](../debugger/pseudovariables.md)