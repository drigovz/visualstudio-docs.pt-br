---
title: 'CA2102: Capturar exceções não CLSCompliant em manipuladores gerais'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a831e771ce771ef492089dae14f719de6429e32
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002594"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Capturar exceções não CLSCompliant em manipuladores gerais

|||
|-|-|
|NomeDoTipo|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um membro em um assembly que não está marcado com o <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> ou está marcada `RuntimeCompatibility(WrapNonExceptionThrows = false)` contém um bloco catch que manipula <xref:System.Exception?displayProperty=fullName> e não contém um bloco de captura geral imediatamente posterior. Essa regra ignora [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] assemblies.

## <a name="rule-description"></a>Descrição da regra

Um bloco catch que manipula <xref:System.Exception> captura todas as exceções de Common Language Specification (CLS) em conformidade. No entanto, ele não capturará exceções de não-CLS em conformidade. Não-CLS exceções em conformidade podem ser geradas a partir de código nativo ou código gerenciado que foi gerado pelo Microsoft intermediate language (MSIL) montador. Observe que o c# e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compiladores não permite não-CLS em conformidade com exceções sejam geradas e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não capturará exceções de não-CLS em conformidade. Se for a intenção do bloco catch tratar todas as exceções, use a seguinte sintaxe do bloco catch geral.

- C#: `catch {}`

- C++: `catch(...) {}` ou `catch(Object^) {}`

Exceção sem tratamento não-CLS em conformidade se torna um problema de segurança quando as permissões concedidas anteriormente são removidas no bloco catch. Porque as exceções de conformidade não-CLS não são capturadas, um método mal-intencionado que gera um não-CLS exceção sem conformidade pode executar com permissões elevadas.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra quando a intenção é capturar todas as exceções, substituir ou adicionar um bloco catch geral ou marcar o assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Se as permissões forem removidas em um bloco catch, duplicar a funcionalidade em geral bloco catch. Se não for a intenção para lidar com todas as exceções, substitua o bloco catch que manipula <xref:System.Exception> com blocos catch que lidam com tipos de exceção específica.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra, se o bloco try não contém todas as instruções que podem gerar uma exceção não CLS. Como qualquer código nativo ou gerenciado pode gerar um não-CLS exceção sem conformidade, isso requer conhecimento de todos os códigos que podem ser executados em todos os caminhos de código dentro do bloco try. Observe que exceções de conformidade não-CLS não são geradas pelo common language runtime.

## <a name="example-1"></a>Exemplo 1

O exemplo a seguir mostra uma classe MSIL que lança uma exceção não CLS.

```cpp
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example-2"></a>Exemplo 2

O exemplo a seguir mostra um método que contém um bloco catch geral que satisfaz a regra.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Compile os exemplos anteriores da seguinte maneira.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Regras relacionadas

[CA1031: Não capturar tipos de exceção geral](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Consulte também

- [Exceções e manipulação de exceções](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (IL Assembler)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Componentes de independência de linguagem e componentes independentes da linguagem](/dotnet/standard/language-independence-and-language-independent-components)