---
title: 'CA1303: não passe literais como parâmetros localizados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce85a3a933d9453c63ef118d5dfd9e0b17cbf130
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661453"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: não passar literais como parâmetros localizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um método passa um literal de cadeia de caracteres como um parâmetro para um construtor ou método na biblioteca de classes [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] e essa cadeia de caracteres deve ser localizável.

 Esse aviso é gerado quando uma cadeia de caracteres literal é passada como um valor para um parâmetro ou propriedade e um ou mais dos seguintes casos é verdadeiro:

- O atributo <xref:System.ComponentModel.LocalizableAttribute> do parâmetro ou da propriedade é definido como true.

- O nome do parâmetro ou da propriedade contém "texto", "mensagem" ou "legenda".

- O nome do parâmetro de cadeia de caracteres que é passado para um método Console. Write ou console. WriteLine é "value" ou "Format".

## <a name="rule-description"></a>Descrição da Regra
 Literais de cadeia de caracteres inseridos no código-fonte são difíceis de localizar.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, substitua o literal da cadeia de caracteres por uma cadeia de caracteres recuperada por meio de uma instância da classe <xref:System.Resources.ResourceManager>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se a biblioteca de códigos não for localizada ou se a cadeia de caracteres não for exposta ao usuário final ou a um desenvolvedor usando a biblioteca de códigos.

 Os usuários podem eliminar ruídos em relação a métodos que não devem passar cadeias de caracteres localizadas renomeando o parâmetro ou a propriedade chamada ou marcando esses itens como condicionais.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que gera uma exceção quando qualquer um dos dois argumentos está fora do intervalo. Para o primeiro argumento, o construtor de exceção recebe uma cadeia de caracteres literal, que viola essa regra. Para o segundo argumento, o Construtor passa corretamente uma cadeia de caracteres recuperada por meio de um <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Consulte também
 [Recursos em aplicativos de área de trabalho](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
