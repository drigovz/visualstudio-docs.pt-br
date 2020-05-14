---
title: Brace Matching em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709811"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Corresponder a brace em um serviço de linguagem legado
A correspondência de chaves ajuda o desenvolvedor a rastrear elementos de linguagem que precisam ocorrer juntos, como parênteses e chaves. Quando um desenvolvedor entra em uma cinta de fechamento, a cinta de abertura é destacada.

 Você pode combinar dois ou três elementos co-ocorrendo, chamados pares e triplos. Triplos são conjuntos de três elementos co-ocorrendo. Por exemplo, em C#, `foreach` a `foreach()`declaração forma um triplo: , `{`e `}`. Todos os três elementos são destacados quando a cinta de fechamento é digitada.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais sobre a nova maneira de implementar a correspondência do aparelho, consulte [Passo a Passo: Exibir aparelhos correspondentes](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

 A <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe suporta pares e triplos <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> com os métodos.

## <a name="implementation"></a>Implementação
 O serviço de idiomas precisa identificar todos os elementos compatíveis no idioma e, em seguida, localizar todos os pares correspondentes. Isso é normalmente realizado <xref:Microsoft.VisualStudio.Package.IScanner> implementando para detectar uma <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> linguagem combinada e, em seguida, usando o método para combinar com os elementos.

 O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método chama o scanner para tokenizar a linha e devolver o token pouco antes do caret. O scanner indica que um par de elementos de <xref:Microsoft.VisualStudio.Package.TokenTriggers> linguagem foi encontrado definindo um valor de gatilho de token no token atual. O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> chama o método <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> que, por sua vez, chama o método com o valor da razão de análise para <xref:Microsoft.VisualStudio.Package.ParseReason> localizar o elemento de linguagem correspondente. Quando o elemento de linguagem correspondente é encontrado, ambos os elementos são destacados.

 Para obter uma descrição completa de como digitar uma cinta aciona o destaque da cinta, consulte a seção *De operação de análise exemplo* no artigo [Analisador de serviço de linguagem legado e scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Habilite o suporte para correspondência de cinta
 O <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo pode definir as entradas de registro **MatchBraces,** **MatchBracesAtCaret** <xref:Microsoft.VisualStudio.Package.LanguagePreferences> e **ShowMatchingBrace** que definem as propriedades correspondentes da classe. As propriedades de preferência de idioma também podem ser definidas pelo usuário.

|Entrada de Registro|Propriedade|Descrição|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Permite a correspondência da cinta.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Permite a correspondência da cinta à medida que o cuidado se move.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Destaca a cinta correspondente.|

## <a name="match-conditional-statements"></a>Corresponder declarações condicionais
 Você pode combinar declarações `if`condicionais, `else`tais `#if` `#elif`como `#else` `#endif`, `else if`e , ou , , , , , da mesma forma que delimitadores correspondentes. Você pode subclassificar a <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe e fornecer um método que pode adicionar intervalos de texto, bem como delimitadores à matriz interna de elementos correspondentes.

## <a name="set-the-trigger"></a>Defina o gatilho
 O exemplo a seguir mostra como detectar parênteses correspondentes, chaves e chaves e fixações quadradas e definir o gatilho para ele no scanner. O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método <xref:Microsoft.VisualStudio.Package.Source> na classe detecta o gatilho e chama o analisador para encontrar o par correspondente (consulte a seção *Encontrar a correspondência* neste artigo). Este exemplo é apenas para fins ilustrativos. Ele assume que o scanner `GetNextToken` contém um método que identifica e retorna tokens de uma linha de texto.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Combine as chaves
 Aqui está um exemplo simplificado `{ }`para `( )`combinar `[ ]`os elementos da <xref:Microsoft.VisualStudio.Package.AuthoringSink> linguagem , e , e adicionar seus comprimentos ao objeto. Esta abordagem não é uma abordagem recomendada para analisar o código-fonte; é apenas para fins ilustrativos.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>Confira também
- [Recursos de serviço de idioma legado](../../extensibility/internals/legacy-language-service-features1.md)
- [Analisador e scanner de serviços de linguagem legado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
