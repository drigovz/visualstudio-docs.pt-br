---
title: Operadores de pesquisa avançada em expressões de pesquisa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5088fc04f4440260bdb9d3f040d99061c05d243
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620343"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operadores de pesquisa avançada em expressões de pesquisa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usando operadores de pesquisa avançada, você pode refinar a pesquisa de conteúdo criando expressões de pesquisa mais complicadas com base em expressões mais simples. Como a tabela a seguir mostra, esses operadores restringem o contexto no qual uma consulta é executada.

> [!WARNING]
> Você precisa inserir os operadores de pesquisa avançada com dois pontos finais e nenhum espaço intermediário antes dos dois pontos para o mecanismo de pesquisa os reconheça.

|Para pesquisar|Use|Exemplo|Resultado|
|-------------------|---------|-------------|------------|
|Um termo no título do tópico|título:|title:binaryreader|Tópicos que contêm "binaryreader" em seus títulos.|
|Um termo em um exemplo de código|código:|code:readdouble|Tópicos que contêm "readdouble" em um exemplo de código.|
|Um termo em um exemplo de uma linguagem de programação específica|code:vb:|code:vb:string|Tópicos que contêm "string" em um exemplo do Visual Basic.|
|Um tópico associado a uma palavra-chave de índice específica|keyword:|keyword:readbyte|Tópicos associados à palavra-chave de índice "readbyte".|

 Você pode usar o operador code: para encontrar conteúdo sobre qualquer uma das várias linguagens de programação, mas ele retorna resultados apenas para conteúdo marcado com uma linguagem de programação específica. A tabela a seguir lista as linguagens de programação que dão suporte a esse operador:

|Linguagem de programação|Use|
|--------------------------|---------|
|Visual Basic|code:vb<br /><br /> ou<br /><br /> code:visualbasic|
|C#|code:c#<br /><br /> ou<br /><br /> code:csharp|
|C++|code:cpp<br /><br /> ou<br /><br /> code:c++<br /><br /> ou<br /><br /> code:cplusplus|
|F#|code:f#<br /><br /> ou<br /><br /> code:fsharp|
|JavaScript|code:javascript<br /><br /> ou<br /><br /> code:js|
|XAML|code:xaml|

## <a name="see-also"></a>Consulte também
 [Operadores lógicos em expressões](../ide/logical-operators-in-search-expressions.md) de pesquisa [dicas de pesquisa de texto completo](../ide/full-text-search-tips.md)
