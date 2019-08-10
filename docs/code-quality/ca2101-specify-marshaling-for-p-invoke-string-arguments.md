---
title: 'CA2101: Especificar marshaling para argumentos de cadeias de caracteres P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1eb4c2535060f9a110d149e88ac2532e6ad1412
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921096"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Especificar marshaling para argumentos de cadeias de caracteres P/Invoke

|||
|-|-|
|NomeDoTipo|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um membro de invocação de plataforma permite chamadores parcialmente confiáveis, tem um parâmetro de cadeia de caracteres e não empacota explicitamente a cadeia de caracteres.

## <a name="rule-description"></a>Descrição da regra
Quando você converte de Unicode para ANSI, é possível que nem todos os caracteres Unicode possam ser representados em uma página de código ANSI específica. O *mapeamento de melhor ajuste* tenta resolver esse problema, substituindo um caractere para o caractere que não pode ser representado. O uso desse recurso pode causar uma possível vulnerabilidade de segurança porque você não pode controlar o caractere escolhido. Por exemplo, um código mal-intencionado poderia criar intencionalmente uma cadeia de caracteres Unicode que contenha personagens que não foram encontrados em uma página de código específica, que são convertidas em caracteres especiais do sistema de arquivos, como '.. ' ou '/'. Observe também que as verificações de segurança de caracteres especiais ocorrem com frequência antes que a cadeia de caracteres seja convertida em ANSI.

O mapeamento de melhor ajuste é o padrão para a conversão não gerenciada, WChar para MByte. A menos que você desabilite explicitamente o mapeamento de melhor ajuste, seu código pode conter uma vulnerabilidade de segurança explorável devido a esse problema.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, desempacotar explicitamente os tipos de dados de cadeia de caracteres.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um método que viola essa regra e, em seguida, mostra como corrigir a violação.

[!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]