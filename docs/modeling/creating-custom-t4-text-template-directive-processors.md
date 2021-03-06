---
title: Criando processadores de diretiva de modelo de texto T4 personalizados
description: Saiba mais sobre o processo de transformação de modelo de texto e como criar um processador de diretiva de modelo de texto T4 personalizado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf17d2a7e3b38e267f0353f71c7cd83826b141bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945325"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Criar processadores personalizados de diretiva de modelo de texto T4

O *processo de transformação de modelo de texto* usa um arquivo de *modelo de texto* como a entrada e produz um arquivo de texto como a saída. O *mecanismo de transformação de modelo de texto* controla o processo, e o mecanismo interage com um host de transformação de modelo de texto e um ou mais *processadores de diretiva* de modelo de texto para concluir o processo. Para obter mais informações, consulte [o processo de transformação do modelo de texto](../modeling/the-text-template-transformation-process.md).

Para criar um processador de diretriz personalizado, é preciso criar uma classe herdada de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ou de <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

A diferença entre esses dois é que <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementa a interface mínima necessária para obter parâmetros do usuário e gerar o código que produz o arquivo de saída de modelo. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa o padrão de design Requires/fornece. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> o lida com dois parâmetros especiais `requires` e `provides` .  Por exemplo, um processador de diretiva personalizado pode aceitar um nome de arquivo do usuário, abrir e ler o arquivo e, em seguida, armazenar o texto do arquivo em uma variável denominada `fileText` . Uma subclasse da <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> classe pode pegar um nome de arquivo do usuário como o valor do `requires` parâmetro e o nome da variável na qual armazenar o texto como o valor do `provides` parâmetro. Esse processador abriria e lerá o arquivo e, em seguida, armazenaria o texto do arquivo na variável especificada.

Antes de chamar um processador de diretiva personalizado a partir de um modelo de texto no Visual Studio, você deve registrá-lo.

Para obter mais informações sobre como adicionar a chave do registro, consulte [implantando um processador de diretiva personalizada](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Diretivas personalizadas

Uma diretiva personalizada é parecida com esta:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Você pode usar um processador de diretiva personalizada quando desejar acessar dados externos ou recursos de um modelo de texto.

Modelos de texto diferentes podem compartilhar a funcionalidade que um processador de diretiva única fornece, de modo que os processadores de diretiva fornecem uma maneira de considerar o código para reutilização. A `include` diretiva interna é semelhante, pois você pode usá-la para fatorar o código e compartilhá-lo entre diferentes modelos de texto. A diferença é que qualquer funcionalidade fornecida pela `include` diretiva é fixa e não aceita parâmetros. Se você quiser fornecer funcionalidade comum a um modelo de texto e permitir que o modelo passe parâmetros, você deve criar um processador de diretiva personalizado.

Alguns exemplos de processadores de diretiva personalizada podem ser:

- Um processador de diretiva para retornar dados de um banco de dado que aceita um nome de usuário e senha como parâmetros.

- Um processador de diretiva para abrir e ler um arquivo que aceita o nome do arquivo como um parâmetro.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Partes principais de um processador de diretriz personalizado

Para desenvolver um processador de diretiva, você deve criar uma classe que herde de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ou <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

Os métodos mais importantes `DirectiveProcessor` que devem ser implementados são os seguintes.

- `bool IsDirectiveSupported(string directiveName)` -Retornar `true` se o processador de diretiva puder lidar com a diretiva nomeada.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -O mecanismo de modelo chama esse método para cada ocorrência de uma diretiva no modelo. O processador deve salvar os resultados.

Depois de todas as chamadas para ProcessDirective (), o mecanismo de modelagem chamará esses métodos:

- `string[] GetReferencesForProcessingRun()` -Retornar os nomes dos assemblies que o código do modelo requer.

- `string[] GetImportsForProcessingRun()` -Retornar os namespaces que podem ser usados no código do modelo.

- `string GetClassCodeForProcessingRun()` -Retorna o código de métodos, propriedades e outras declarações que o código de modelo pode usar. A maneira mais fácil de fazer isso é criar uma cadeia de caracteres contendo o código C# ou Visual Basic. Para tornar o processador de diretivas capaz de ser chamado por meio de um modelo que usa qualquer linguagem CLR, você pode construir as instruções como uma árvore CodeDom e retornar o resultado da serialização da árvore no idioma usado pelo modelo.

- Para obter mais informações, consulte [Walkthrough: Criando um processador de diretiva personalizada](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Confira também

- [Implantar um processador de diretiva personalizado](../modeling/deploying-a-custom-directive-processor.md) explica como registrar um processador de diretiva personalizado.
- [Walkthrough: criar um processador de diretiva personalizado](../modeling/walkthrough-creating-a-custom-directive-processor.md) descreve como criar um processador de diretiva personalizado, como registrar e testar o processador de diretivas e como formatar o arquivo de saída como HTML.
