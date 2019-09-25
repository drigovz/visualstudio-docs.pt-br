---
title: 'CA1303: Não passar literais como parâmetros localizados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2700dc2ade7ba901f15f67045e3170e2bbb40ff8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235111"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Não passar literais como parâmetros localizados

|||
|-|-|
|NomeDoTipo|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Categoria|Microsoft. Globalization|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um método passa um literal de cadeia de caracteres como um parâmetro para um construtor ou método .NET e essa cadeia de caracteres deve ser localizável.

Esse aviso é gerado quando uma cadeia de caracteres literal é passada como um valor para um parâmetro ou propriedade e um ou mais dos seguintes casos é verdadeiro:

- O <xref:System.ComponentModel.LocalizableAttribute> atributo do parâmetro ou da propriedade é definido como true.

- O nome do parâmetro ou da propriedade contém "texto", "mensagem" ou "legenda".

- O nome do parâmetro de cadeia de caracteres que é passado para um método Console. Write ou console. WriteLine é "value" ou "Format".

## <a name="rule-description"></a>Descrição da regra

Literais de cadeia de caracteres inseridos no código-fonte são difíceis de localizar.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, substitua o literal da cadeia de caracteres por uma cadeia de caracteres recuperada <xref:System.Resources.ResourceManager> por meio de uma instância da classe.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra se a biblioteca de códigos não for localizada ou se a cadeia de caracteres não for exposta ao usuário final ou a um desenvolvedor usando a biblioteca de códigos.

Os usuários podem eliminar ruídos em relação a métodos que não devem passar cadeias de caracteres localizadas renomeando o parâmetro ou a propriedade, ou marcando esses itens como condicionais.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um método que gera uma exceção quando qualquer um dos dois argumentos está fora do intervalo. Para o primeiro argumento, o construtor de exceção recebe uma cadeia de caracteres literal, que viola essa regra. Para o segundo argumento, o Construtor passa corretamente uma cadeia de caracteres recuperada <xref:System.Resources.ResourceManager>por meio de um.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Consulte também

- [Recursos em aplicativos da área de trabalho](/dotnet/framework/resources/index)