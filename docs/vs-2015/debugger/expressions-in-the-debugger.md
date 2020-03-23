---
title: Expressões no Depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VBScript
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
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3999737a2fad04c9b513722ae11608574a72c410
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302521"
---
# <a name="expressions-in-the-debugger"></a>Expressões no depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O depurador do Visual Studio inclui os avaliadores de expressão que funcionam quando você insere uma expressão na caixa de diálogo **QuickWatch**, na janela **Inspeção** ou na janela **Imediato**. Os avaliadores de expressão também estão no trabalho na janela **Pontos de interrupção** e em muitos outros locais no depurador.  
  
 As seções a seguir dão detalhes sobre expressões em diferentes idiomas.  
  
## <a name="f-expressions-are-not-supported"></a>As expressões F# não são suportadas  
 F# expressões não são reconhecidas. Se você estiver depurando o código F#, você precisa traduzir suas expressões em sintaxe C# antes de inserir as expressões em uma janela de depurador ou caixa de diálogo. Quando você converter expressões de F# em C#, certifique-se de que C# usa o operador `==` para testar a igualdade, enquanto F# usa o `=` único.  
  
## <a name="c-expressions"></a>Expressões C++  
 Para obter informações sobre o uso de operadores de contexto com expressões em C++, consulte [Context Operator (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Expressões sem suporte em C++  
  
#### <a name="constructors-destructors-and-conversions"></a>Construtores, destruidores e conversões  
 Você não pode chamar um construtor ou destruidor para um objeto, seja explicitamente ou implicitamente. Por exemplo, a expressão a seguir chama explicitamente um construtor e resulta em uma mensagem de erro:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Você não pode chamar uma função de conversão se o destino da conversão for uma classe. Essa conversão envolve a construção de um objeto. Por exemplo, se `myFraction` for uma instância de `CFraction`, que define o operador da função de conversão `FixedPoint`, a expressão a seguir resultará em erro:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Não é possível chamar os operadores novos ou apagar. Por exemplo, a seguinte expressão não é suportada:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Macros de pré-processador  
 As macros do pré-processador não são suportadas no depurador. Por exemplo, se `VALUE` uma constante `#define VALUE 3`for declarada `VALUE` como: , você não poderá usar na janela **Relógio.** Para evitar essa limitação, você deve substituir `#define`'s por enums e funções sempre que possível.  
  
### <a name="using-namespace-declarations"></a>usando declarações de namespace  
 Você não `using namespace` pode usar declarações.  Para acessar um nome de tipo ou variável fora do namespace atual, você deve usar o nome totalmente qualificado.  
  
### <a name="anonymous-namespaces"></a>Namespaces anônimos  
 Espaços de nomes anônimos não são suportados. Se você tiver o seguinte `test` código, não poderá adicionar à janela do relógio:  
  
```cpp  
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
  
  As funções intrínsecas do depurador também podem tornar mais convenientes as expressões de avaliação. Por exemplo, `strncmp(str, “asd”)` é muito mais fácil escrever `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`em uma condição de ponto de ruptura do que . )  
  
|Área|Funções intrínsecas|  
|----------|-------------------------|  
|**Comprimento da cadeia de caracteres**|strlen, wcslen, strnlen, wcsnlen|  
|**Comparação de cadeias de caracteres**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Pesquisa de cadeias de caracteres**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Essas funções exigem que o processo que está sendo depurado seja executado no Windows 8. Depurar os arquivos de despejo gerados a partir de um dispositivo do Windows 8 também exige que o computador do Visual Studio esteja executando o Windows 8. No entanto, se você estiver depurando um dispositivo do Windows 8 remotamente, o computador do Visual Studio poderá executar o Windows 7.|  
|**Diversos**|__log2<br /><br /> Retorna a base 2 de log de um inteiro especificado, arredondada para o menor inteiro próximo.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLI - Expressões não suportadas  
  
- Elencos que envolvam ponteiros, ou moldes definidos pelo usuário, não são suportados.  
  
- A comparação e a atribuição de objetos não são suportadas.  
  
- Operadores sobrecarregados e funções sobrecarregadas não são suportados.  
  
- Boxe e unboxing não são suportados.  
  
- `Sizeof`operador não é suportado.  
  
## <a name="c---unsupported-expressions"></a>C# - Expressões não suportadas  
  
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
  
## <a name="see-also"></a>Consulte Também  
 [Especificadores de formato em C++](../debugger/format-specifiers-in-cpp.md)   
 [Operador de Contexto (C++)](../debugger/context-operator-cpp.md)   
 [Especificadores de formato em C #](../debugger/format-specifiers-in-csharp.md)   
 [Pseudovariáveis](../debugger/pseudovariables.md)
