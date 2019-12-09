---
title: Analisador e scanner do serviço de idioma herdado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b172fee8f6f5cf1c80d306a8a8b154f7316bf8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726731"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analisador e scanner do serviço de linguagem herdado
O analisador é o coração do serviço de linguagem. As classes de linguagem MPF (estrutura de pacote gerenciada) exigem um analisador de idioma para selecionar informações sobre o código que está sendo exibido. Um analisador separa o texto em tokens léxicos e, em seguida, identifica esses tokens por tipo e funcionalidade.

## <a name="discussion"></a>Discussão
 Este é um C# método.

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 Neste exemplo, os tokens são as palavras e as marcas de pontuação. Os tipos de tokens são os seguintes.

|Nome do token|Tipo de token|
|----------------|----------------|
|namespace, classe, público, void, int|keyword|
|=|operator|
|{ } ( ) ;|Delimitador|
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|
|MyNamespace|namespace|
|MyClass|classe|
|MyFunction|method|
|arg1|parâmetro|
|var1|Variável local|

 A função do analisador é identificar os tokens. Alguns tokens podem ter mais de um tipo. Depois que o analisador identificar os tokens, o serviço de idioma poderá usar as informações para fornecer recursos úteis, como realce de sintaxe, correspondência de chaves e operações do IntelliSense.

## <a name="types-of-parsers"></a>Tipos de analisadores
 Um analisador de serviço de linguagem não é o mesmo que um analisador usado como parte de um compilador. No entanto, esse tipo de analisador precisa usar um scanner e um analisador, da mesma maneira que um analisador de compilador.

- Um scanner é usado para identificar tipos de tokens. Essas informações são usadas para realce de sintaxe e para identificar rapidamente os tipos de token que podem disparar outras operações, por exemplo, correspondência de chaves. Esse scanner é representado pela interface <xref:Microsoft.VisualStudio.Package.IScanner>.

- Um analisador é usado para descrever as funções e o escopo dos tokens. Essas informações são usadas em operações do IntelliSense para identificar elementos de linguagem, como métodos, variáveis, parâmetros e declarações, e fornecer listas de membros e assinaturas de método com base no contexto. Esse analisador também é usado para localizar pares de elementos de idioma correspondentes, como chaves e parênteses. Esse analisador é acessado por meio do método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> na classe <xref:Microsoft.VisualStudio.Package.LanguageService>.

  A forma como você implementa um scanner e um analisador para o seu serviço de idioma é sua. Há vários recursos disponíveis que descrevem como funcionam os analisadores e como escrever seu próprio analisador. Além disso, vários produtos gratuitos e comerciais estão disponíveis para ajudar na criação de um analisador.

### <a name="the-parsesource-parser"></a>O analisador de análise
 Ao contrário de um analisador que é usado como parte de um compilador (onde os tokens são convertidos em alguma forma de código executável), um analisador de serviço de linguagem pode ser chamado por vários motivos diferentes e em muitos contextos diferentes. A forma como você implementa essa abordagem no método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> na classe <xref:Microsoft.VisualStudio.Package.LanguageService> é sua. É importante ter em mente que o método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> pode ser chamado em um thread em segundo plano.

> [!CAUTION]
> A estrutura de <xref:Microsoft.VisualStudio.Package.ParseRequest> contém uma referência ao objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Este objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> não pode ser usado no thread em segundo plano. Na verdade, muitas das classes de MPF base não podem ser usadas no thread em segundo plano. Isso inclui as classes <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> e qualquer outra classe que se comunica direta ou indiretamente com a exibição.

 Esse analisador normalmente analisa o arquivo de origem inteiro na primeira vez em que é chamado ou quando o valor do motivo da análise de <xref:Microsoft.VisualStudio.Package.ParseReason> é fornecido. As chamadas subsequentes para o método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> manipulam uma pequena parte do código analisado e podem ser executadas muito mais rapidamente usando os resultados da operação de análise completa anterior. O método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> comunica os resultados da operação de análise por meio dos objetos <xref:Microsoft.VisualStudio.Package.AuthoringSink> e <xref:Microsoft.VisualStudio.Package.AuthoringScope>. O objeto <xref:Microsoft.VisualStudio.Package.AuthoringSink> é usado para coletar informações para um motivo de análise específico, por exemplo, informações sobre as extensões de chaves correspondentes ou assinaturas de método que têm listas de parâmetros. O <xref:Microsoft.VisualStudio.Package.AuthoringScope> fornece coleções de declarações e assinaturas de método e também suporte para a opção ir para edição avançada (**vá para definição**, **vá para declaração**, **vá para referência**).

### <a name="the-iscanner-scanner"></a>O scanner isgravar
 Você também deve implementar um scanner que implemente <xref:Microsoft.VisualStudio.Package.IScanner>. No entanto, como esse scanner funciona em uma base linha por linha por meio da classe <xref:Microsoft.VisualStudio.Package.Colorizer>, normalmente é mais fácil de implementar. No início de cada linha, o MPF dá ao <xref:Microsoft.VisualStudio.Package.Colorizer> classe um valor a ser usado como uma variável de estado que é passada para o scanner. No final de cada linha, o verificador retorna a variável de estado atualizado. O MPF armazena em cache essas informações de estado para cada linha para que o verificador possa iniciar a análise de qualquer linha sem precisar iniciar no início do arquivo de origem. Essa verificação rápida de uma única linha permite que o editor forneça comentários rápidos ao usuário.

## <a name="parsing-for-matching-braces"></a>Análise para chaves correspondentes
 Este exemplo mostra o fluxo de controle para corresponder a uma chave de fechamento que o usuário tenha digitado. Nesse processo, o verificador usado para a colorização também é usado para determinar o tipo de token e se o token pode disparar uma operação de chave de correspondência. Se o gatilho for encontrado, o método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> será chamado para localizar a chave correspondente. Por fim, as duas chaves são realçadas.

 Embora chaves sejam usadas nos nomes de gatilhos e motivos de análise, esse processo não está limitado a chaves reais. Há suporte para qualquer par de caracteres especificado para ser um par correspondente. Os exemplos incluem (e), \< e > e [e].

 Suponha que o serviço de linguagem dê suporte a chaves correspondentes.

1. O usuário digita uma chave de fechamento (}).

2. A chave é inserida no cursor no arquivo de origem e o cursor é avançado por um.

3. O método <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> na classe <xref:Microsoft.VisualStudio.Package.Source> é chamado com a chave de fechamento digitada.

4. O método <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> chama o método <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> na classe <xref:Microsoft.VisualStudio.Package.Source> para obter o token na posição logo antes da posição atual do cursor. Esse token corresponde à chave de fechamento digitada).

    1. O método <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chama o método <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> no objeto <xref:Microsoft.VisualStudio.Package.Colorizer> para obter todos os tokens na linha atual.

    2. O método <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> chama o método <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> no objeto <xref:Microsoft.VisualStudio.Package.IScanner> com o texto da linha atual.

    3. O método <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> chama repetidamente o método <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> no objeto <xref:Microsoft.VisualStudio.Package.IScanner> para reunir todos os tokens da linha atual.

    4. O método <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chama um método particular na classe <xref:Microsoft.VisualStudio.Package.Source> para obter o token que contém a posição desejada e passa a lista de tokens obtidos do método <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>.

5. O método <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> procura um sinalizador de gatilho de token de <xref:Microsoft.VisualStudio.Package.TokenTriggers> no token que é retornado do método <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>; ou seja, o token que representa a chave de fechamento).

6. Se o sinalizador de gatilho de <xref:Microsoft.VisualStudio.Package.TokenTriggers> for encontrado, o método <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> na classe <xref:Microsoft.VisualStudio.Package.Source> será chamado.

7. O método <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> inicia uma operação de análise com o valor da razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>. Essa operação finalmente chama o método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> na classe <xref:Microsoft.VisualStudio.Package.LanguageService>. Se a análise assíncrona estiver habilitada, essa chamada para o método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ocorrerá em um thread em segundo plano.

8. Quando a operação de análise é concluída, um manipulador de conclusão interno (também conhecido como um método de retorno de chamada) chamado `HandleMatchBracesResponse` é chamado na classe <xref:Microsoft.VisualStudio.Package.Source>. Essa chamada é feita automaticamente pela classe base <xref:Microsoft.VisualStudio.Package.LanguageService>, não pelo analisador.

9. O método `HandleMatchBracesResponse` Obtém uma lista de Spans do objeto <xref:Microsoft.VisualStudio.Package.AuthoringSink> que é armazenado no objeto <xref:Microsoft.VisualStudio.Package.ParseRequest>. (Um Span é uma estrutura de <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> que especifica um intervalo de linhas e caracteres no arquivo de origem.) Essa lista de Spans normalmente contém duas extensões, uma para as chaves de abertura e fechamento.

10. O método `HandleBracesResponse` chama o método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> no objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> que é armazenado no objeto <xref:Microsoft.VisualStudio.Package.ParseRequest>. Isso realça os intervalos fornecidos.

11. Se a propriedade <xref:Microsoft.VisualStudio.Package.LanguagePreferences> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> estiver habilitada, o método `HandleBracesResponse` obterá o texto que é incluído pelo intervalo correspondente e exibirá os primeiros 80 caracteres desse intervalo na barra de status. Isso funcionará melhor se o método de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> incluir o elemento de linguagem que acompanha o par correspondente. Para obter mais informações, consulte a propriedade <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Trabalhado.

### <a name="summary"></a>Resumo
 A operação de chaves correspondentes normalmente é limitada a pares simples de elementos de linguagem. Elementos mais complexos, como percorridas correspondentes ("`if(...)`", "`{`" e "`}`" ou "`else`", "`{`" e "`}`"), podem ser realçados como parte de uma operação de conclusão de palavras. Por exemplo, quando a palavra "else" for concluída, a instrução "`if`" correspondente poderá ser realçada. Se houver uma série de `if` / instruções `else if`, todas elas poderão ser realçadas usando o mesmo mecanismo que as chaves correspondentes. A classe base <xref:Microsoft.VisualStudio.Package.Source> já dá suporte a isso, da seguinte maneira: o verificador deve retornar o valor do gatilho de token <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinado com o valor do gatilho <xref:Microsoft.VisualStudio.Package.TokenTriggers> para o token que está antes da posição do cursor.

 Para obter mais informações, consulte [correspondência de chaves em um serviço de idioma herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Análise para colorização
 A colorização do código-fonte é simples, apenas identifique o tipo de token e as informações de cor de retorno sobre esse tipo. A classe <xref:Microsoft.VisualStudio.Package.Colorizer> atua como o intermediário entre o editor e o scanner para fornecer informações de cores sobre cada token. A classe <xref:Microsoft.VisualStudio.Package.Colorizer> usa o objeto <xref:Microsoft.VisualStudio.Package.IScanner> para ajudar a colorir uma linha e também para coletar informações de estado de todas as linhas no arquivo de origem. Nas classes de serviço de linguagem MPF, a classe <xref:Microsoft.VisualStudio.Package.Colorizer> não precisa ser substituída porque se comunica com o scanner somente por meio da interface <xref:Microsoft.VisualStudio.Package.IScanner>. Você fornece o objeto que implementa a interface <xref:Microsoft.VisualStudio.Package.IScanner> substituindo o método <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> na classe <xref:Microsoft.VisualStudio.Package.LanguageService>.

 O <xref:Microsoft.VisualStudio.Package.IScanner> scanner recebe uma linha de código-fonte por meio do método <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>. As chamadas para o método <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> são repetidas para obter o próximo token na linha até que a linha seja esgotada de tokens. Para a colorização, o MPF trata todo o código-fonte como uma sequência de linhas. Portanto, o verificador deve ser capaz de lidar com a origem que está chegando a ele como linhas. Além disso, qualquer linha pode ser passada para o scanner a qualquer momento, e a única garantia é que o verificador recebe a variável de estado da linha antes da linha a ser verificada.

 A classe <xref:Microsoft.VisualStudio.Package.Colorizer> também é usada para identificar gatilhos de token. Esses gatilhos informam ao MPF que um determinado token pode iniciar uma operação mais complexa, como preenchimento de palavras ou chaves correspondentes. Como a identificação desses gatilhos deve ser rápida e deve ocorrer em qualquer local, o verificador é mais adequado para essa tarefa.

 Para obter mais informações, consulte [colorir sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Análise de funcionalidade e escopo
 A análise da funcionalidade e do escopo requer mais esforço do que apenas identificar os tipos de tokens encontrados. O analisador precisa identificar não apenas o tipo de token, mas também a funcionalidade para a qual o token é usado. Por exemplo, um identificador é apenas um nome, mas em seu idioma, um identificador pode ser o nome de uma classe, namespace, método ou variável, dependendo do contexto. O tipo geral do token pode ser um identificador, mas o identificador também pode ter outros significados, dependendo do que é e onde ele está definido. Essa identificação exige que o analisador tenha um conhecimento mais extensivo sobre a linguagem que está sendo analisada. É aí que entra a classe <xref:Microsoft.VisualStudio.Package.AuthoringSink>. A classe <xref:Microsoft.VisualStudio.Package.AuthoringSink> coleta informações sobre identificadores, métodos, pares de idiomas correspondentes (como chaves e parênteses) e processamentos de idiomas (semelhantes a pares de idiomas, exceto pelo fato de que há três partes, por exemplo, "`foreach()`" "`{`" e "`}`") . Além disso, você pode substituir a classe <xref:Microsoft.VisualStudio.Package.AuthoringSink> para dar suporte à identificação de código, que é usada na validação antecipada de pontos de interrupção para que o depurador não precise ser carregado e a janela de depuração de **autoização** , que mostra variáveis e parâmetros locais automaticamente quando um programa está sendo depurado e requer que o analisador identifique variáveis locais e parâmetros apropriados além daqueles apresentados pelo depurador.

 O objeto <xref:Microsoft.VisualStudio.Package.AuthoringSink> é passado para o analisador como parte do objeto <xref:Microsoft.VisualStudio.Package.ParseRequest>, e um novo objeto <xref:Microsoft.VisualStudio.Package.AuthoringSink> é criado toda vez que um novo objeto <xref:Microsoft.VisualStudio.Package.ParseRequest> é criado. Além disso, o método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> deve retornar um objeto <xref:Microsoft.VisualStudio.Package.AuthoringScope>, que é usado para lidar com várias operações do IntelliSense. O objeto <xref:Microsoft.VisualStudio.Package.AuthoringScope> mantém uma lista de declarações e uma lista de métodos, que é preenchida, dependendo do motivo da análise. A classe de <xref:Microsoft.VisualStudio.Package.AuthoringScope> deve ser implementada.

## <a name="see-also"></a>Consulte também
- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Visão geral do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-overview.md)
- [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Correspondência de chave em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)