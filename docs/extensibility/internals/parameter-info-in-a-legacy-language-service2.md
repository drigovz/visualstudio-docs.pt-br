---
title: Informações de parâmetros em um serviço de linguagem legado2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706742"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informações de parâmetro em um serviço de linguagem herdado
IntelliSense Parameter Info é uma dica de ferramenta que exibe a assinatura de um método quando o usuário digita o caractere iniciar da lista de parâmetros (tipicamente um parêntese aberto) para a lista de parâmetros do método. À medida que cada parâmetro é inserido e o separador de parâmetros (tipicamente uma comma) é digitado, a dica de ferramenta é atualizada para mostrar o próximo parâmetro em negrito.

 As classes de quadro de pacote gerenciado (MPF) fornecem suporte para o gerenciamento da dica de ferramenta Parameter Info. O analisador deve detectar caracteres finais de parâmetro, parâmetro em seguida e parâmetro, e deve fornecer uma lista das assinaturas do método e seus parâmetros associados.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais, consulte [Estendendo o Editor e os Serviços de Idiomas](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="implementation"></a>Implementação
 O analisador deve definir <xref:Microsoft.VisualStudio.Package.TokenTriggers> o valor do gatilho definido quando encontra um caractere inicial da lista de parâmetros (muitas vezes um parêntese aberto). Ele deve <xref:Microsoft.VisualStudio.Package.TokenTriggers> definir um gatilho quando encontrar um separador de parâmetros (muitas vezes uma comma). Isso faz com que uma dica de ferramenta Parâmetro Info seja atualizada e mostre o próximo parâmetro em negrito. O analisador deve definir <xref:Microsoft.VisualStudio.Package.TokenTriggers> o valor do gatilho quando se encontrar o caractere final da lista de parâmetros (muitas vezes um parêntese próximo).

 O <xref:Microsoft.VisualStudio.Package.TokenTriggers> valor do gatilho inicia <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> uma chamada para <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> o método, que por <xref:Microsoft.VisualStudio.Package.ParseReason>sua vez chama o analisador de método com uma razão de análise de . Se o analisador determinar que o identificador antes do caractere inicial da lista de parâmetros <xref:Microsoft.VisualStudio.Package.AuthoringScope> é um nome de método reconhecido, ele retorna uma lista de assinaturas do método correspondente no objeto. Se alguma assinatura do método for encontrada, a dica da ferramenta Parâmetro Info será exibida com a primeira assinatura da lista. Esta dica de ferramenta é então atualizada à medida que mais da assinatura é digitada. Quando o caractere final da lista de parâmetros é digitado, a dica de ferramenta Parâmetro Info é removida da exibição.

> [!NOTE]
> Para garantir que a dica de ferramenta Parâmetro Info esteja devidamente <xref:Microsoft.VisualStudio.Package.Methods> formatada, você deve substituir as propriedades na classe para fornecer os caracteres apropriados. A <xref:Microsoft.VisualStudio.Package.Methods> classe base assume uma assinatura de método c#-style. Consulte <xref:Microsoft.VisualStudio.Package.Methods> a classe para obter detalhes sobre como isso pode ser feito.

## <a name="enabling-support-for-the-parameter-info"></a>Ativando o suporte para as informações do parâmetro
 Para suportar as dicas de ferramentas `ShowCompletion` Parâmetro Info, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> você `true`deve definir o parâmetro nomeado do to . O serviço de idiomas lê o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> valor desta entrada de registro da propriedade.

 Além disso, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> a propriedade `true` deve ser definida para que a dica de ferramenta Parâmetro Info seja mostrada.

### <a name="example"></a>Exemplo
 Aqui está um exemplo simplificado de detectar os caracteres da lista de parâmetros e definir os gatilhos apropriados. Este exemplo é apenas para fins ilustrativos. Ele assume que o scanner `GetNextToken` contém um método que identifica e retorna tokens de uma linha de texto. O código de exemplo simplesmente define os gatilhos sempre que vê o tipo certo de caractere.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Suporte à dica de ferramenta de informações de parâmetros no analisador
 A <xref:Microsoft.VisualStudio.Package.Source> classe faz algumas suposições <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> sobre o conteúdo das classes e quando a dica de ferramenta Parâmetro Info é exibida e atualizada.

- O analisador <xref:Microsoft.VisualStudio.Package.ParseReason> é dado quando o caractere inicial da lista de parâmetros é digitado.

- A localização dada no <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto é imediatamente após o caractere de início da lista de parâmetros. O analisador deve coletar as assinaturas de todas as declarações de método disponíveis <xref:Microsoft.VisualStudio.Package.AuthoringScope> nessa posição e armazená-las em uma lista na sua versão do objeto. Esta lista inclui o nome do método, o tipo de método (ou tipo de retorno) e uma lista de possíveis parâmetros. Esta lista é posteriormente pesquisada para a assinatura do método ou assinaturas para exibir na dica de ferramenta Parâmetro Info.

  O analisador deve então analisar a <xref:Microsoft.VisualStudio.Package.ParseRequest> linha especificada pelo objeto para reunir o nome do método que está sendo inserido, bem como o quão longe o usuário está nos parâmetros de digitação. Isso é feito passando o nome <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> do método <xref:Microsoft.VisualStudio.Package.AuthoringSink> para o <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> método no objeto e, em seguida, chamando o método quando o caractere inicial da lista de parâmetros é analisado, chamando o <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> método quando o parâmetro lista o próximo caractere é analisado e, finalmente, chamando o <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> método quando o caractere final da lista de parâmetros é analisado. Os resultados dessas chamadas de <xref:Microsoft.VisualStudio.Package.Source> método são usados pela classe para atualizar a dica de ferramenta Parâmetro Info adequadamente.

### <a name="example"></a>Exemplo
 Aqui está uma linha de texto que o usuário pode inserir. Os números abaixo da linha indicam qual passo é dado pelo analisador nessa posição na linha (assumindo que a análise se move da esquerda para a direita). A suposição aqui é que tudo antes da linha já foi analisado para assinaturas do método, incluindo a assinatura do método "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Os passos que o analisador toma são descritos abaixo:

1. O analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> chama com o texto "testfunc".

2. O analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>chama.

3. O analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>chama.

4. O analisador <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>chama.
