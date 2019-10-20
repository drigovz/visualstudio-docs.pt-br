---
title: 'CA1400: P-invocar pontos de entrada deve existir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d1083f7bbdf3b3af78b83aed293b31d898ae7522
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661372"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: os pontos de entrada P/Invoke devem existir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um método público ou protegido é marcado com o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Não foi possível localizar a biblioteca não gerenciada ou não foi possível comparar o método a uma função na biblioteca. Se a regra não puder localizar o nome do método exatamente como foi especificado, ele procurará as versões ANSI ou de caracteres largos do método, sufixando o nome do método com ' A ' ou ' W '. Se nenhuma correspondência for encontrada, a regra tentará localizar uma função usando o formato de nome __stdcall (_MyMethod@12, em que 12 representa o comprimento dos argumentos). Se nenhuma correspondência for encontrada e o nome do método começar com ' # ', a regra pesquisará a função como uma referência ordinal em vez de uma referência de nome.

## <a name="rule-description"></a>Descrição da Regra
 Nenhuma verificação de tempo de compilação está disponível para garantir que os métodos marcados com <xref:System.Runtime.InteropServices.DllImportAttribute> estejam localizados na DLL não gerenciada referenciada. Se nenhuma função com o nome especificado estiver na biblioteca ou os argumentos para o método não corresponderem aos argumentos da função, o Common Language Runtime gerará uma exceção.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, corrija o método que tem o atributo <xref:System.Runtime.InteropServices.DllImportAttribute>. Verifique se a biblioteca não gerenciada existe e se está no mesmo diretório que o assembly que contém o método. Se a biblioteca estiver presente e corretamente referenciada, verifique se o nome do método, o tipo de retorno e a assinatura do argumento correspondem à função da biblioteca.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir um aviso dessa regra quando a biblioteca não gerenciada estiver no mesmo diretório que o assembly gerenciado que faz referência a ela. Pode ser seguro suprimir um aviso dessa regra no caso em que a biblioteca não gerenciada não pôde ser localizada.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra. Nenhuma função chamada `DoSomethingUnmanaged` ocorre em Kernel32. dll.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
