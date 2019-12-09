---
title: Avisos de globalização
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11202e25dee89640c5a51450610919ad6a5c294c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649544"
---
# <a name="globalization-warnings"></a>Avisos de globalização
Os avisos de globalização dão suporte a bibliotecas e aplicativos preparados para o mundo.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1300: especificar MessageBoxOptions](../code-quality/ca1300.md)|Para exibir corretamente uma caixa de mensagem para as culturas que usam uma ordem de leitura da direita para a esquerda, os membros RightAlign e RtlReading da enumeração MessageBoxOptions devem ser passados para o método Show.|
|[CA1301: evitar aceleradores duplicados](../code-quality/ca1301.md)|Uma tecla de acesso, também conhecida como acelerador, dá ao teclado acesso a um controle usando-se a tecla ALT. Quando vários controles têm chaves de acesso duplicadas, o comportamento da tecla de acesso não é bem definido.|
|[CA1302: não codificar cadeias de caracteres específicas da localidade](../code-quality/ca1302.md)|A enumeração System.Environment.SpecialFolder contém membros que fazem referência às pastas especiais do sistema. Os locais dessas pastas podem ter valores diferentes em diferentes sistemas operacionais; o usuário pode alterar alguns dos locais; e os locais são diferentes para cada linguagem. O método Environment. GetFolderPath retorna os locais associados ao ambiente. SpecialFolder Enumeration, localizado e apropriado para o computador em execução no momento.|
|[CA1303: não passar literais como parâmetros localizados](../code-quality/ca1303.md)|Um método visível externamente passa um literal de cadeia de caracteres como um parâmetro para um construtor ou método .NET, e essa cadeia de caracteres deve ser localizável.|
|[CA1304: especificar CultureInfo](../code-quality/ca1304.md)|Um método ou um construtor chama um membro que tem uma sobrecarga que aceita um parâmetro System.Globalization.CultureInfo, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro CultureInfo. Quando um objeto CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades.|
|[CA1305: especificar IFormatProvider](../code-quality/ca1305.md)|Um método ou um construtor chama um ou mais membros que têm sobrecargas que aceitam um parâmetro System.IFormatProvider, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro IFormatProvider. Quando um objeto System.Globalization.CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades.|
|[CA1306: definir localidade para tipos de dados](../code-quality/ca1306.md)|A localidade determina os elementos de apresentação específicos da cultura para dados, como a formatação usada para valores numéricos, símbolos de moeda e ordem de classificação. Ao criar um DataTable ou um DataSet, você deve definir explicitamente a localidade.|
|[CA1307: especificar StringComparison](../code-quality/ca1307.md)|Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define um parâmetro StringComparison.|
|[CA1308: normalizar cadeias de caracteres para maiúsculas](../code-quality/ca1308.md)|As cadeias de caracteres devem ser normalizadas em maiúsculas. Um pequeno grupo de caracteres não pode fazer uma viagem de ida e volta quando são convertidos em minúsculas.|
|[CA1309: usar StringComparison ordinal](../code-quality/ca1309.md)|Uma operação de comparação de cadeia de caracteres não linguística não define o parâmetro StringComparison como Ordinal ou OrdinalIgnoreCase. Definindo-se explicitamente o parâmetro como StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, o código normalmente ganha velocidade, fica mais correto e se torna mais confiável.|
|[CA2101: especificar marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101.md)|Um membro de invocação de plataforma permite chamadores parcialmente confiáveis, tem um parâmetro de cadeia de caracteres e não empacota explicitamente a cadeia de caracteres. Isso pode causar uma vulnerabilidade de segurança em potencial.|
