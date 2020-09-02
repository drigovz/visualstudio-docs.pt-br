---
title: Avisos de globalização | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7db942f410b9a6a8c2f12a044d0e48ad1ad19950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667579"
---
# <a name="globalization-warnings"></a>Avisos de globalização
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os avisos de globalização dão suporte a bibliotecas e aplicativos preparados para o mundo.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1300: Especificar MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Para exibir corretamente uma caixa de mensagem para as culturas que usam uma ordem de leitura da direita para a esquerda, os membros RightAlign e RtlReading da enumeração MessageBoxOptions devem ser passados para o método Show.|
|[CA1301: Evitar aceleradores duplicados](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Uma tecla de acesso, também conhecida como acelerador, dá ao teclado acesso a um controle usando-se a tecla ALT. Quando vários controles têm teclas de acesso duplicadas, o comportamento da tecla de acesso não é bem definido.|
|[CA1302: Não embutir no código cadeias de caracteres específicas da localidade](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|A enumeração System.Environment.SpecialFolder contém membros que fazem referência às pastas especiais do sistema. Os locais dessas pastas podem ter valores diferentes em diferentes sistemas operacionais; o usuário pode alterar alguns dos locais; e os locais são diferentes para cada linguagem. O método Environment.GetFolderPath retorna os locais associados à enumeração Environment.SpecialFolder, localizada e apropriada para o computador atualmente em execução.|
|[CA1303: Não passar literais como parâmetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Um método visível externamente passa uma cadeia de caracteres literal como um parâmetro para um construtor ou método ou na biblioteca de classes de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], e essa cadeia de caracteres deve ser localizável.|
|[CA1304: Especificar CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)|Um método ou um construtor chama um membro que tem uma sobrecarga que aceita um parâmetro System.Globalization.CultureInfo, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro CultureInfo. Quando um objeto CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades.|
|[CA1305: Especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Um método ou um construtor chama um ou mais membros que têm sobrecargas que aceitam um parâmetro System.IFormatProvider, e o método ou o construtor não chama a sobrecarga que utiliza o parâmetro IFormatProvider. Quando um objeto System.Globalization.CultureInfo ou System.IFormatProvider não for fornecido, o valor padrão fornecido pelo membro sobrecarregado poderá não ter o efeito desejado em todas as localidades.|
|[CA1306: Definir localidade para tipos de dados](../code-quality/ca1306-set-locale-for-data-types.md)|A localidade determina os elementos de apresentação específicos da cultura para dados, como a formatação usada para valores numéricos, símbolos de moeda e ordem de classificação. Ao criar um DataTable ou um DataSet, você deve definir explicitamente a localidade.|
|[CA1307: Especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define um parâmetro StringComparison.|
|[CA1308: Normalizar cadeias de caracteres em maiúsculas](../code-quality/ca1308-normalize-strings-to-uppercase.md)|As cadeias de caracteres devem ser normalizadas em maiúsculas. Um pequeno grupo de caracteres não pode fazer uma viagem de ida e volta quando são convertidos em minúsculas.|
|[CA1309: Usar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Uma operação de comparação de cadeia de caracteres não linguística não define o parâmetro StringComparison como Ordinal ou OrdinalIgnoreCase. Definindo-se explicitamente o parâmetro como StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, o código normalmente ganha velocidade, fica mais correto e se torna mais confiável.|
|[CA2101: especificar o marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Um membro de invocação de plataforma permite chamadores parcialmente confiáveis, tem um parâmetro de cadeia de caracteres e não empacota explicitamente a cadeia de caracteres. Isso pode causar uma vulnerabilidade de segurança em potencial.|
