---
title: 'CA2105: Campos de matriz não devem ser somente leitura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4741b30d1429a1a179328c8fb4b150fc4f920612
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154383"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Campos de matrizes não devem ser somente leitura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um campo público ou protegido que contém uma matriz é declarado como somente leitura.

## <a name="rule-description"></a>Descrição da Regra
 Quando você aplica a `readonly` (`ReadOnly` em [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) modificador para um campo que contém uma matriz, o campo não pode ser alterado para fazer referência a uma matriz diferente. No entanto, os elementos da matriz que são armazenados em um campo somente leitura podem ser alterados. Código que toma decisões ou realize operações com base nos elementos de uma matriz de somente leitura que podem ser acessados publicamente pode conter uma vulnerabilidade de segurança explorável.

 Observe que também ter um campo público viola a regra de criação [CA1051: Não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir a vulnerabilidade de segurança que é identificada por essa regra, não confie no conteúdo de uma matriz de somente leitura que podem ser acessados publicamente. É altamente recomendável que você use um dos procedimentos a seguir:

- Substitua a matriz uma coleção fortemente tipada que não pode ser alterada. Para obter mais informações, consulte <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Substitua o campo público com um método que retorna um clone de uma matriz privada. Porque seu código não depende do clone, há nenhum risco se os elementos são modificados.

  Se você escolher a segunda abordagem, não substitua o campo com uma propriedade; propriedades que retornam matrizes negativamente afetam o desempenho. Para obter mais informações, consulte [CA1819: Propriedades não devem retornar matrizes](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 A exclusão de um aviso nessa regra é altamente desaconselhável. Quase nenhum cenário ocorre em que o conteúdo de um campo somente leitura não é importante. Se esse for o caso com seu cenário, remova o `readonly` modificador em vez de excluir a mensagem.

## <a name="example"></a>Exemplo
 Este exemplo demonstra os perigos da violação dessa regra. A primeira parte mostra uma biblioteca de exemplo que tem um tipo `MyClassWithReadOnlyArrayField`, que contém dois campos (`grades` e `privateGrades`) que não são seguras. O campo `grades` é público e, portanto, vulnerável a qualquer chamador. O campo `privateGrades` é privado, mas ainda estará vulnerável porque ele é retornado para os chamadores pelo `GetPrivateGrades` método. O `securePrivateGrades` campo é exposto de maneira segura pelo `GetSecurePrivateGrades` método. Ele é declarado como particular siga as práticas de bom design. A segunda parte mostra o código que altera os valores armazenados na `grades` e `privateGrades` membros.

 A biblioteca de classes de exemplo é exibido no exemplo a seguir.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Exemplo
 O código a seguir usa a biblioteca de classes de exemplo para ilustrar os problemas de segurança de matriz somente leitura.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 A saída deste exemplo é:

 **Antes de adulteração: Notas: 90, 90, 90 notas de privada: 90, 90, 90 secure notas, 90, 90, 90**
**após a violação: Notas: 90, 555, notas de 90 privada: 90, 90 e 555 secure notas, 90, 90, 90**
## <a name="see-also"></a>Consulte também
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
