---
title: Analisador e scanner de serviços de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707320"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analisador e scanner do serviço de linguagem herdado
O analisador é o coração do serviço de idiomas. As classes de idiomas MPF (Managed Package Framework, estrutura de pacotes gerenciados) exigem um analisador de idiomas para selecionar informações sobre o código que está sendo exibido. Um analisador separa o texto em tokens léxicos e, em seguida, identifica esses tokens por tipo e funcionalidade.

## <a name="discussion"></a>Discussão
 O seguinte é um método C#.

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

 Neste exemplo, os tokens são as palavras e marcas de pontuação. Os tipos de tokens são os seguintes.

|Nome do Token|Tipo de token|
|----------------|----------------|
|namespace, classe, público, vazio, int|palavra-chave|
|=|operador|
|{ } ( ) ;|delimiter|
|MyNamespace, MyClass, MyFunction, arg1, var1|identificador|
|Mynamespace|namespace|
|MyClass|classe|
|Myfunction|method|
|arg1|parâmetro|
|var1|variável local|

 O papel do analisador é identificar os tokens. Alguns tokens podem ter mais de um tipo. Depois que o analisador identificar os tokens, o serviço de idiomas pode usar as informações para fornecer recursos úteis, como destaque de sintaxe, correspondência de chaves e operações do IntelliSense.

## <a name="types-of-parsers"></a>Tipos de Parsers
 Um analisador de serviço de idioma não é o mesmo que um analisador usado como parte de um compilador. No entanto, este tipo de analisador precisa usar tanto um scanner quanto um analisador, da mesma forma que um analisador de compilador.

- Um scanner é usado para identificar tipos de tokens. Estas informações são usadas para realçar a sintaxe e para identificar rapidamente tipos de tokens que podem disparar outras operações, por exemplo, correspondência de chave. Este scanner é <xref:Microsoft.VisualStudio.Package.IScanner> representado pela interface.

- Um analisador é usado para descrever as funções e o escopo dos tokens. Essas informações são usadas em operações do IntelliSense para identificar elementos de linguagem, como métodos, variáveis, parâmetros e declarações, e para fornecer listas de membros e assinaturas de métodos com base no contexto. Este analisador também é usado para localizar pares de elementos de linguagem correspondentes, como aparelhos e parênteses. Este analisador é acessado <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> através <xref:Microsoft.VisualStudio.Package.LanguageService> do método da classe.

  Como você implementa um scanner e um analisador para o seu serviço de idioma si. Vários recursos estão disponíveis que descrevem como os analisadores funcionam e como escrever seu próprio analisador. Além disso, vários produtos gratuitos e comerciais estão disponíveis que ajudam na criação de um analisador.

### <a name="the-parsesource-parser"></a>O ParseSource Parser
 Ao contrário de um analisador que é usado como parte de um compilador (onde os tokens são convertidos em alguma forma de código executável), um analisador de serviço de linguagem pode ser chamado por muitas razões diferentes e em muitos contextos diferentes. Como você implementa <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> essa abordagem no método da <xref:Microsoft.VisualStudio.Package.LanguageService> classe depende de você. É importante ter em mente <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> que o método pode ser chamado em um segmento de fundo.

> [!CAUTION]
> A <xref:Microsoft.VisualStudio.Package.ParseRequest> estrutura contém uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> referência ao objeto. Este <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto não pode ser usado na linha de fundo. Na verdade, muitas das classes básicas do MPF não podem ser usadas no segmento de fundo. Estes <xref:Microsoft.VisualStudio.Package.Source>incluem <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> as classes e qualquer outra classe que se comunique direta ou indiretamente com a vista.

 Este analisador normalmente analisa todo o arquivo de origem na primeira vez <xref:Microsoft.VisualStudio.Package.ParseReason> que é chamado ou quando o valor da razão de análise é dado. Chamadas subseqüentes para o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método lidam com uma pequena parte do código analisado e podem ser executadas muito mais rapidamente usando os resultados da operação de análise completa anterior. O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método comunica os resultados da operação <xref:Microsoft.VisualStudio.Package.AuthoringSink> de <xref:Microsoft.VisualStudio.Package.AuthoringScope> análise através dos objetos. O <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto é usado para coletar informações por uma razão específica de análise, por exemplo, informações sobre os intervalos de aparelhos correspondentes ou assinaturas de método que têm listas de parâmetros. O <xref:Microsoft.VisualStudio.Package.AuthoringScope> fornece coletas de declarações e assinaturas de método e também suporte para a opção De edição Avançada Go To (**Go to Definition**, Go to **Declaration**, Go **to Reference**).

### <a name="the-iscanner-scanner"></a>O scanner iScanner
 Você também deve implementar um <xref:Microsoft.VisualStudio.Package.IScanner>scanner que implemente . No entanto, como este scanner opera em uma <xref:Microsoft.VisualStudio.Package.Colorizer> base linha por linha através da classe, é tipicamente mais fácil de implementar. No início de cada linha, <xref:Microsoft.VisualStudio.Package.Colorizer> o MPF dá à classe um valor para usar como variável de estado que é passada para o scanner. No final de cada linha, o scanner retorna a variável de estado atualizada. O MPF armazena essas informações de estado para cada linha para que o scanner possa iniciar o análise de qualquer linha sem ter que iniciar no início do arquivo de origem. Esta varredura rápida de uma única linha permite que o editor forneça feedback rápido ao usuário.

## <a name="parsing-for-matching-braces"></a>Análise para aparelhos correspondentes
 Este exemplo mostra o fluxo de controle para combinar uma cinta de fechamento que o usuário digitou. Neste processo, o scanner usado para coloração também é usado para determinar o tipo de token e se o token pode desencadear uma operação de match-brace. Se o gatilho for <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> encontrado, o método é chamado para encontrar a cinta correspondente. Finalmente, as duas chaves são destacadas.

 Embora os aparelhos sejam usados nos nomes dos gatilhos e das razões de análise, este processo não se limita a aparelhos reais. Qualquer par de caracteres especificados como um par correspondente é suportado. Exemplos incluem ( \< e ), e >, e [ e ].

 Presuma que o serviço de idiomas suporta aparelhos correspondentes.

1. O usuário digita uma cinta encaracolada de fechamento (}).

2. A cinta encaracolada é inserida no cursor no arquivo de origem e o cursor é avançado por um.

3. O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método <xref:Microsoft.VisualStudio.Package.Source> da classe é chamado com a chave de fechamento digitada.

4. O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chama o <xref:Microsoft.VisualStudio.Package.Source> método na classe para obter o token na posição pouco antes da posição atual do cursor. Este token corresponde à chave de fechamento digitada).

    1. O <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> chama o <xref:Microsoft.VisualStudio.Package.Colorizer> método no objeto para obter todos os tokens na linha atual.

    2. O <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> chama o <xref:Microsoft.VisualStudio.Package.IScanner> método no objeto com o texto da linha atual.

    3. O <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método chama <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> repetidamente <xref:Microsoft.VisualStudio.Package.IScanner> o método no objeto para coletar todos os tokens da linha atual.

    4. O <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método chama um <xref:Microsoft.VisualStudio.Package.Source> método privado na classe para obter o token que contém a posição desejada e passa na lista de tokens obtidos a partir do <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método.

5. O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método procura uma bandeira <xref:Microsoft.VisualStudio.Package.TokenTriggers> de gatilho de token no <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> token que é devolvida do método; ou seja, o token que representa a cinta de fechamento).

6. Se a bandeira <xref:Microsoft.VisualStudio.Package.TokenTriggers> de gatilho <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> for <xref:Microsoft.VisualStudio.Package.Source> encontrada, o método da classe é chamado.

7. O <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método inicia uma operação de análise com <xref:Microsoft.VisualStudio.Package.ParseReason>o valor da razão de análise de . Esta operação, em <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> última <xref:Microsoft.VisualStudio.Package.LanguageService> análise, chama o método na classe. Se o parsonismo assíncrono estiver <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ativado, essa chamada para o método ocorrerá em um segmento de fundo.

8. Quando a operação de análise é concluída, um manipulador de conclusão `HandleMatchBracesResponse` interna (também <xref:Microsoft.VisualStudio.Package.Source> conhecido como método de retorno de chamada) é chamado na classe. Esta chamada é feita <xref:Microsoft.VisualStudio.Package.LanguageService> automaticamente pela classe base, não pelo analisador.

9. O `HandleMatchBracesResponse` método obtém uma lista <xref:Microsoft.VisualStudio.Package.AuthoringSink> de extensões do <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto armazenado no objeto. (Um intervalo <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> é uma estrutura que especifica uma gama de linhas e caracteres no arquivo de origem.) Esta lista de vãos normalmente contém dois vãos, um cada para as chaves de abertura e fechamento.

10. O `HandleBracesResponse` método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> método no objeto <xref:Microsoft.VisualStudio.Package.ParseRequest> armazenado no objeto. Isso destaca os períodos dados.

11. Se <xref:Microsoft.VisualStudio.Package.LanguagePreferences> a <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> propriedade estiver `HandleBracesResponse` habilitada, o método obtém o texto que é englobado pela extensão correspondente e exibe os primeiros 80 caracteres desse período na barra de status. Isso funciona melhor <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> se o método incluir o elemento de idioma que acompanha o par correspondente. Para obter mais informações, consulte a propriedade <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Concluído.

### <a name="summary"></a>Resumo
 A operação de aparelhos correspondentes é tipicamente limitada a pares simples de elementos linguísticos. Elementos mais complexos, como`if(...)`a`{`combinação de`}`triplos`else`(" ", " e " " ou " ",`{`" e " " " " e "`}`"), podem ser destacados como parte de uma operação de conclusão de palavras. Por exemplo, quando a palavra "else"`if`é concluída, a declaração correspondente " pode ser destacada. Se houvesse uma `if` / `else if` série de declarações, todas elas poderiam ser destacadas usando o mesmo mecanismo que aparelhos correspondentes. A <xref:Microsoft.VisualStudio.Package.Source> classe base já suporta isso, da seguinte forma: O <xref:Microsoft.VisualStudio.Package.TokenTriggers> scanner deve retornar <xref:Microsoft.VisualStudio.Package.TokenTriggers> o valor do gatilho do token combinado com o valor do gatilho para o token que está antes da posição do cursor.

 Para obter mais informações, consulte [Brace Matching em um serviço de linguagem legado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Parsing for Colorization
 Colorir o código-fonte é simples, basta identificar o tipo de token e retornar informações de cores sobre esse tipo. A <xref:Microsoft.VisualStudio.Package.Colorizer> classe atua como intermediária entre o editor e o scanner para fornecer informações coloridas sobre cada token. A <xref:Microsoft.VisualStudio.Package.Colorizer> classe <xref:Microsoft.VisualStudio.Package.IScanner> usa o objeto para ajudar a colorir uma linha e também para coletar informações de estado para todas as linhas no arquivo de origem. Nas aulas de serviço <xref:Microsoft.VisualStudio.Package.Colorizer> de idiomas do MPF, a classe não precisa ser <xref:Microsoft.VisualStudio.Package.IScanner> substituída porque se comunica com o scanner apenas através da interface. Você fornece o objeto <xref:Microsoft.VisualStudio.Package.IScanner> que implementa <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> a interface <xref:Microsoft.VisualStudio.Package.LanguageService> substituindo o método na classe.

 O <xref:Microsoft.VisualStudio.Package.IScanner> scanner recebe uma linha de <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> código fonte através do método. As chamadas <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> para o método são repetidas para obter o próximo token na linha até que a linha esteja esgotada de tokens. Para coloração, o MPF trata todo o código fonte como uma seqüência de linhas. Portanto, o scanner deve ser capaz de lidar com a fonte vindo para ele como linhas. Além disso, qualquer linha pode ser passada para o scanner a qualquer momento, e a única garantia é que o scanner receba a variável estado da linha antes da linha prestes a ser digitalizada.

 A <xref:Microsoft.VisualStudio.Package.Colorizer> classe também é usada para identificar gatilhos de token. Esses gatilhos dizem ao MPF que um determinado token pode iniciar uma operação mais complexa, como a conclusão de palavras ou aparelhos correspondentes. Como a identificação desses gatilhos deve ser rápida e deve ocorrer em qualquer local, o scanner é o mais adequado para essa tarefa.

 Para obter mais informações, consulte [Sintaxdimensionar colorir em um serviço de linguagem legado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Análise de funcionalidade e escopo
 Analisar a funcionalidade e o escopo requer mais esforço do que apenas identificar os tipos de tokens encontrados. O analisador tem que identificar não apenas o tipo de token, mas também a funcionalidade para a qual o token é usado. Por exemplo, um identificador é apenas um nome, mas no seu idioma, um identificador pode ser o nome de uma classe, namespace, método ou variável, dependendo do contexto. O tipo geral do token pode ser um identificador, mas o identificador também pode ter outros significados, dependendo do que é e onde é definido. Essa identificação exige que o analisador tenha um conhecimento mais amplo sobre a língua que está sendo analisado. É aqui <xref:Microsoft.VisualStudio.Package.AuthoringSink> que entra a aula. A <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe coleta informações sobre identificadores, métodos, pares de idiomas correspondentes (como aparelhos e parênteses) e triplos`foreach()`de`{`idiomas`}`(semelhantes aos pares de idiomas, exceto que há três partes, por exemplo, " " " e " "). Além disso, você pode <xref:Microsoft.VisualStudio.Package.AuthoringSink> substituir a classe para suportar a identificação de código, que é usada na validação antecipada de pontos de interrupção para que o depurador não precise ser carregado, e a janela de depuração **autos,** que mostra variáveis e parâmetros locais automaticamente quando um programa está sendo depurado e requer que o analisador identifique variáveis e parâmetros locais apropriados, além daqueles que o depurador apresenta.

 O <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto é passado para o <xref:Microsoft.VisualStudio.Package.ParseRequest> analisador como <xref:Microsoft.VisualStudio.Package.AuthoringSink> parte do objeto, e <xref:Microsoft.VisualStudio.Package.ParseRequest> um novo objeto é criado toda vez que um novo objeto é criado. Além disso, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> o método <xref:Microsoft.VisualStudio.Package.AuthoringScope> deve retornar um objeto, que é usado para lidar com várias operações do IntelliSense. O <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto mantém uma lista de declarações e uma lista de métodos, qualquer um dos quais é preenchido, dependendo do motivo da análise. A <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe deve ser implementada.

## <a name="see-also"></a>Confira também
- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Visão geral do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-overview.md)
- [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Correspondência de chaves em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
