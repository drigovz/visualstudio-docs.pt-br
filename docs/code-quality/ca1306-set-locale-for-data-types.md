---
title: 'CA1306: Definir localidade para tipos de dados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 893844741c848bee759f56dd027c9976a21902e8
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922786"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Definir localidade para tipos de dados

|||
|-|-|
|NomeDoTipo|SetLocaleForDataTypes|
|CheckId|CA1306|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um método ou Construtor criou uma ou mais <xref:System.Data.DataTable?displayProperty=fullName> instâncias <xref:System.Data.DataSet?displayProperty=fullName> ou e não definiu explicitamente a propriedade locale (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> ou <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Descrição da regra
A localidade determina elementos de apresentação específicos da cultura para dados, como formatação usada para valores numéricos, símbolos de moeda e ordem de classificação. Ao criar um <xref:System.Data.DataTable> ou <xref:System.Data.DataSet>, você deve definir a localidade explicitamente. Por padrão, a localidade para esses tipos é a cultura atual. Para dados que são armazenados em um arquivo ou banco de dado e são compartilhados globalmente, a localidade normalmente deve ser definida como a cultura<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>invariável (). Quando os dados são compartilhados entre culturas, o uso da localidade padrão pode fazer com que <xref:System.Data.DataTable> o <xref:System.Data.DataSet> conteúdo do ou seja apresentado ou interpretado incorretamente.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, defina explicitamente a localidade para o <xref:System.Data.DataTable> ou. <xref:System.Data.DataSet>

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra quando a biblioteca ou o aplicativo é para um público local limitado, os dados não são compartilhados ou a configuração padrão gera o comportamento desejado em todos os cenários com suporte.

## <a name="example"></a>Exemplo
O exemplo a seguir cria <xref:System.Data.DataTable> duas instâncias.

[!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>