---
title: 'CA1045: Não passar tipos por referência'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6a8fda526647a1a9f7f999928cb08978a61bd04
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235775"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Não passar tipos por referência

|||
|-|-|
|NomeDoTipo|DoNotPassTypesByReference|
|CheckId|CA1045|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um método público ou protegido em um tipo público tem um `ref` parâmetro que usa um tipo primitivo, um tipo de referência ou um tipo de valor que não é um dos tipos internos.

## <a name="rule-description"></a>Descrição da regra
Passar tipos por referência (usando `out` ou `ref`) requer experiência com ponteiros, compreendendo como tipos de valor e tipos de referência diferem e manipulando métodos que têm vários valores de retorno. Além disso, a diferença `out` entre `ref` os parâmetros e não é amplamente compreendida.

Quando um tipo de referência é passado "por referência", o método pretende usar o parâmetro para retornar uma instância diferente do objeto. (Passar um tipo de referência por referência também é conhecido como usar um ponteiro duplo, um ponteiro para um ponteiro ou um indireção duplo.) Usando a Convenção de chamada padrão, que é Pass "por valor", um parâmetro que usa um tipo de referência já recebe um ponteiro para o objeto. O ponteiro, não o objeto ao qual ele aponta, é passado por valor. A passagem por valor significa que o método não pode alterar o ponteiro para que ele aponte para uma nova instância do tipo de referência, mas pode alterar o conteúdo do objeto para o qual ele aponta. Para a maioria dos aplicativos, isso é suficiente e produz o comportamento desejado.

Se um método precisar retornar uma instância diferente, use o valor de retorno do método para fazer isso. Consulte a <xref:System.String?displayProperty=fullName> classe de uma variedade de métodos que operam em cadeias de caracteres e retornam uma nova instância de uma cadeia de caracteres. Ao usar esse modelo, ele é deixado para o chamador a fim de decidir se o objeto original é preservado.

Embora os valores de retorno sejam comuns e usados intensamente, `out` a `ref` aplicação e os parâmetros corretos exigem design intermediário e habilidades de codificação. Os arquitetos de biblioteca que projetam um público geral não devem esperar que os `out` usuários `ref` façam o mestre de trabalho com os parâmetros ou.

> [!NOTE]
> Quando você trabalha com parâmetros que são estruturas grandes, os recursos adicionais necessários para copiar essas estruturas podem causar um efeito de desempenho quando você passa por valor. Nesses casos, você pode considerar o uso `ref` de `out` parâmetros ou.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra causada por um tipo de valor, faça com que o método retorne o objeto como seu valor de retorno. Se o método deve retornar vários valores, recrie-o para retornar uma única instância de um objeto que contém os valores.

Para corrigir uma violação dessa regra que é causada por um tipo de referência, verifique se o comportamento desejado é retornar uma nova instância da referência. Se for, o método deve usar seu valor de retorno para fazer isso.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra; no entanto, esse design pode causar problemas de usabilidade.

## <a name="example"></a>Exemplo
A biblioteca a seguir mostra duas implementações de uma classe que gera respostas para os comentários do usuário. A primeira implementação (`BadRefAndOut`) força o usuário da biblioteca a gerenciar três valores de retorno. A segunda implementação (`RedesignedRefAndOut`) simplifica a experiência do usuário retornando uma instância de uma classe de contêiner`ReplyData`() que gerencia os dados como uma única unidade.

[!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>Exemplo
O aplicativo a seguir ilustra a experiência do usuário. A chamada para a biblioteca remodelada (`UseTheSimplifiedClass` método) é mais simples, e as informações retornadas pelo método são facilmente gerenciadas. A saída dos dois métodos é idêntica.

[!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>Exemplo
A biblioteca de exemplo a seguir `ref` ilustra como os parâmetros para tipos de referência são usados e mostra uma maneira melhor de implementar essa funcionalidade.

[!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>Exemplo
O aplicativo a seguir chama cada método na biblioteca para demonstrar o comportamento.

[!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]

Este exemplo gera a seguinte saída:

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="related-rules"></a>Regras relacionadas
[CA1021: Evitar parâmetros de saída](../code-quality/ca1021-avoid-out-parameters.md)