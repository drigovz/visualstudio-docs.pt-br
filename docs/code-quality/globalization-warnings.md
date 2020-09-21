---
title: Regras de globalização
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e046f7e885ea0a6002d07b6a06b6b3728bf607aa
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808633"
---
# <a name="globalization-rules"></a>Regras de globalização
As regras de globalização dão suporte a bibliotecas e aplicativos preparados para o mundo.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1303: Não passar literais como parâmetros localizados](../code-quality/ca1303.md)|Um método visível externamente passa um literal de cadeia de caracteres como um parâmetro para um construtor ou método .NET, e essa cadeia de caracteres deve ser localizável.|
|[CA1304: Especificar CultureInfo](../code-quality/ca1304.md)|Um método ou um construtor chama um membro que tem uma sobrecarga que aceita um parâmetro System.Globalization.CultureInfo, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro CultureInfo. Quando um objeto CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades.|
|[CA1305: Especificar IFormatProvider](../code-quality/ca1305.md)|Um método ou um construtor chama um ou mais membros que têm sobrecargas que aceitam um parâmetro System.IFormatProvider, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro IFormatProvider. Quando um objeto System.Globalization.CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades.|
|[CA1306: Definir localidade para tipos de dados](../code-quality/ca1306.md)|A localidade determina os elementos de apresentação específicos da cultura para dados, como a formatação usada para valores numéricos, símbolos de moeda e ordem de classificação. Ao criar um DataTable ou um DataSet, você deve definir explicitamente a localidade.|
|[CA1307: Especificar StringComparison para garantir a clareza](../code-quality/ca1307.md)|Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define um parâmetro StringComparison.|
|[CA1308: Normalizar cadeias de caracteres em maiúsculas](../code-quality/ca1308.md)|As cadeias de caracteres devem ser normalizadas em maiúsculas. Um pequeno grupo de caracteres não pode fazer uma viagem de ida e volta quando são convertidos em minúsculas.|
|[CA1309: Usar StringComparison ordinal](../code-quality/ca1309.md)|Uma operação de comparação de cadeia de caracteres não linguística não define o parâmetro StringComparison como Ordinal ou OrdinalIgnoreCase. Definindo-se explicitamente o parâmetro como StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, o código normalmente ganha velocidade, fica mais correto e se torna mais confiável.|
|[CA1310: Especificar StringComparison para garantir a exatidão](../code-quality/ca1310.md)|Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define um parâmetro StringComparison e usa a comparação de cadeia de caracteres específica de cultura por padrão.|
|[CA2101: especificar o marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101.md)|Um membro de invocação de plataforma permite chamadores parcialmente confiáveis, tem um parâmetro de cadeia de caracteres e não empacota explicitamente a cadeia de caracteres. Isso pode causar uma vulnerabilidade de segurança em potencial.|
