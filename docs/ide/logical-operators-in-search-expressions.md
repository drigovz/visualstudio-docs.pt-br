---
title: Operadores lógicos e operadores avançados em expressões de pesquisa
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2c189afe9051d0f85c7f5f24a928d475d0eaca9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872844"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Operadores lógicos e avançados em expressões de pesquisa

É possível usar operadores lógicos e operadores de pesquisa avançada para refinar sua pesquisa de conteúdo da Ajuda no **Help Viewer**.

## <a name="logical-operators"></a>Operadores lógicos

Os operadores lógicos especificam como vários termos de pesquisa devem ser combinados em uma consulta de pesquisa. A tabela a seguir mostra os operadores lógicos AND, OR, NOT e NEAR.

|Para pesquisar|Use|Exemplo|Resultado|
|-------------------|---------|-------------|------------|
|Ambos os termos no mesmo artigo|AND|dib AND paleta|Tópicos que contêm "dib" e "paleta".|
|Um dos termos em um artigo|OU|varredura OR vetor|Tópicos que contêm "varredura" ou "vetor".|
|Primeiro termo sem o segundo termo no mesmo artigo|NOT|"operating system" NOT DOS|Tópicos que contêm "sistema operacional", mas não "DOS".|
|Os dois termos, próximos, em um artigo|PRÓXIMO|usuário NEAR kernel|Tópicos que contêm "usuário" bastante próximo de "kernel".|

> [!IMPORTANT]
> Você deve inserir os operadores lógicos em letras maiúsculas para o mecanismo de pesquisa reconhecê-los.

## <a name="advanced-operators"></a>Operadores avançados

Os operadores de pesquisa avançada refinam sua pesquisa de conteúdo especificando o local a procurar o termo da pesquisa em um artigo. A tabela a seguir descreve os quatro operadores de pesquisa avançada disponíveis.

|Para pesquisar|Use|Exemplo|Resultado|
|-------------------|---------|-------------|------------|
|Um termo no título do artigo|`title:`|`title:binaryreader`|Tópicos que contêm "binaryreader" em seus títulos.|
|Um termo em um exemplo de código|`code:`|`code:readdouble`|Tópicos que contêm "readdouble" em um exemplo de código.|
|Um termo em um exemplo de uma linguagem de programação específica|`code:vb:`|`code:vb:string`|Tópicos que contêm "string" em um exemplo de código do Visual Basic.|
|Um artigo associado a uma palavra-chave de índice específica|`keyword:`|`keyword:readbyte`|Tópicos associados à palavra-chave de índice "readbyte".|

> [!IMPORTANT]
> Você precisa inserir os operadores de pesquisa avançada com dois pontos finais e nenhum espaço intermediário antes dos dois pontos para o mecanismo de pesquisa os reconheça.

### <a name="programming-languages-for-code-examples"></a>Linguagens de programação para exemplos de código

Você pode usar o operador `code:` para localizar conteúdo sobre qualquer uma das várias linguagens de programação. Para retornar exemplos de uma linguagem de programação específica, use um dos seguintes valores de linguagem de programação:

|Linguagem de programação|Sintaxe do operador de pesquisa|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> O operador `code:` localiza apenas o conteúdo que está marcado com um rótulo de linguagem de programação e não um conteúdo marcado genericamente como código.

## <a name="see-also"></a>Consulte também

- [Como procurar tópicos](how-to-search-for-topics.md)
- [Microsoft Help Viewer](microsoft-help-viewer.md)
