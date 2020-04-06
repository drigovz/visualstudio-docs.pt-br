---
title: Conclusão de membros em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707194"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Preenchimento de membro em um serviço de linguagem herdado

O Preenchimento do Membro IntelliSense é uma dica de ferramenta que exibe uma lista de possíveis membros de um escopo específico, como uma classe, estrutura, enumeração ou namespace. Por exemplo, em C#, se o usuário digita "isso" seguido de um período, uma lista de todos os membros da classe ou estrutura no escopo atual é apresentada em uma lista da qual o usuário pode selecionar.

O quadro de pacote gerenciado (MPF) fornece suporte para a ponta da ferramenta e o gerenciamento da lista na ponta da ferramenta; tudo o que é necessário é a cooperação do analisador para fornecer os dados que aparecem na lista.

Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais, consulte [Estendendo o Editor e os Serviços de Idiomas](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="how-it-works"></a>Como funciona

A seguir, as duas maneiras pelas quais uma lista de membros é mostrada usando as classes do MPF:

- Posicionando o caret em um identificador ou após um caractere de conclusão de membro e selecionando Membros da **lista** no menu **IntelliSense.**

- O <xref:Microsoft.VisualStudio.Package.IScanner> scanner detecta um caractere de conclusão de membro e define um gatilho de token de [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) para esse caractere.

Um caractere de conclusão de membro indica que um membro de uma classe, estrutura ou enumeração deve seguir. Por exemplo, em C# ou Visual Basic `.`o caractere de conclusão do `.` membro `->`é um , enquanto em C++ o caractere é um ou um . O valor do gatilho é definido quando o caractere selecionado pelo membro é digitalizado.

### <a name="the-intellisense-member-list-command"></a>O comando da lista de membros do IntelliSense

O <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando inicia uma <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> chamada para <xref:Microsoft.VisualStudio.Package.Source> o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método na classe e <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> o método, por sua vez, chama o analisador de método com a razão de análise de [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

O analisador determina o contexto da posição atual, bem como o token abaixo ou imediatamente antes da posição atual. Com base neste token, uma lista de declarações é apresentada. Por exemplo, em C#, se você posicionar o cuidador em um membro da classe e selecionar **Membros da lista,** você terá uma lista de todos os membros da classe. Se você posicionar o cuidador após um período que segue uma variável de objeto, você terá uma lista de todos os membros da classe que o objeto representa. Observe que se o cuidador estiver posicionado em um membro quando a lista de membros for mostrada, selecionar um membro da lista substitui o membro que o cuidador está com o da lista.

### <a name="the-token-trigger"></a>O gatilho de token

O gatilho [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) inicia uma <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> chamada <xref:Microsoft.VisualStudio.Package.Source> para o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método na classe e o método, por sua vez, chama o analisador com a razão de análise de [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Se o gatilho de token também incluiu o sinalizador [TokenTriggers.MatchBraces,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) a razão da análise é [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), que combina seleção de membros e destaque da cinta.

O analisador determina o contexto da posição atual, bem como o que foi digitado antes do caractere de seleção do membro. A partir dessas informações, o analisador cria uma lista de todos os membros do escopo solicitado. Esta lista de declarações <xref:Microsoft.VisualStudio.Package.AuthoringScope> é armazenada no objeto <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> que é devolvido do método. Se alguma declaração for devolvida, a dica da ferramenta de conclusão do membro será exibida. A ponta da ferramenta é gerenciada por uma instância da <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.

## <a name="enable-support-for-member-completion"></a>Habilite o suporte para a conclusão de membros

Você deve `CodeSense` ter a entrada de registro definida como 1 para suportar qualquer operação do IntelliSense. Esta entrada de registro pode ser definida <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> com um parâmetro nomeado passado para o atributo do usuário associado ao pacote de idiomas. As classes de serviço de idiomas <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> leem <xref:Microsoft.VisualStudio.Package.LanguagePreferences> o valor desta entrada de registro da propriedade na classe.

Se o scanner retornar o gatilho de token do [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)e o analisador retornar uma lista de declarações, a lista de conclusão do membro será exibida.

## <a name="support-member-completion-in-the-scanner"></a>Suporte à conclusão do membro no scanner

O scanner deve ser capaz de detectar um caractere de conclusão de membro e definir o gatilho de token do [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) quando esse caractere for analisado.

### <a name="scanner-example"></a>Exemplo de scanner

Aqui está um exemplo simplificado de detectar o <xref:Microsoft.VisualStudio.Package.TokenTriggers> caractere de conclusão do membro e definir o sinalizador apropriado. Este exemplo é apenas para fins ilustrativos. Ele assume que o scanner `GetNextToken` contém um método que identifica e retorna tokens de uma linha de texto. O código de exemplo simplesmente define o gatilho sempre que vê o tipo certo de caractere.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char memberSelectChar = '.';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (c == memberSelectChar)
                {
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;
                }
            }
            return foundToken;
        }
    }
}
```

## <a name="support-member-completion-in-the-parser"></a>Conclusão do membro de suporte no analisador

Para a conclusão <xref:Microsoft.VisualStudio.Package.Source> dos <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> membros, a classe chama o método. Você deve implementar a lista em uma <xref:Microsoft.VisualStudio.Package.Declarations> classe derivada da classe. Consulte <xref:Microsoft.VisualStudio.Package.Declarations> a classe para obter detalhes sobre os métodos que você deve implementar.

O analisador é chamado com [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) ou [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) quando um caractere selecionado por membro é digitado. A localização dada no <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto é imediatamente após o membro selecionar caractere. O analisador deve coletar os nomes de todos os membros que podem aparecer em uma lista de membros nesse ponto específico do código-fonte. Em seguida, o analisador deve analisar a linha atual para determinar o escopo que o usuário deseja associado ao caractere de seleção do membro.

Este escopo é baseado no tipo do identificador antes de o caractere de seleção do membro. Por exemplo, em C#, `languageService` dada a `LanguageService`variável membro que tem um tipo de , digitando **languageService.** produz uma lista de todos `LanguageService` os membros da classe. Também em C#, digitando **isso.** produz uma lista de todos os membros da classe no escopo atual.

### <a name="parser-example"></a>Exemplo de analisador

O exemplo a seguir mostra <xref:Microsoft.VisualStudio.Package.Declarations> uma maneira de preencher uma lista. Este código assume que o analisador constrói uma declaração e `AddDeclaration` a `TestAuthoringScope` adiciona à lista chamando um método na classe.

```csharp
using System.Collections;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclaration
    {
        public string Name;            // Name of declaration
        public int     TypeImageIndex; // Glyph index
        public string Description;     // Description of declaration

        public TestDeclaration(string name, int typeImageIndex, string description)
        {
            this.Name = name;
            this.TypeImageIndex = typeImageIndex;
            this.Description = description;
        }
    }

    //===================================================
    internal class TestDeclarations : Declarations
    {
        private ArrayList declarations;

        public TestDeclarations()
            : base()
        {
            declarations = new ArrayList();
        }

        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        //////////////////////////////////////////////////////////////////////
        // Declarations of class methods that must be implemented.
        public override int GetCount()
        {
            // Return the number of declarations to show.
            return declarations.Count;
        }

        public override string GetDescription(int index)
        {
            // Return the description of the specified item.
            string description = "";
            if (index >= 0 && index < declarations.Count)
            {
                description = ((TestDeclaration)declarations[index]).Description;
            }
            return description;
        }

        public override string GetDisplayText(int index)
        {
            // Determine what is displayed in the tool tip list.
            string text = null;
            if (index >= 0 && index < declarations.Count)
            {
                text = ((TestDeclaration)declarations[index]).Name;
            }
            return text;
        }

        public override int GetGlyph(int index)
        {
            // Return index of image to display next to the display text.
            int imageIndex = -1;
            if (index >= 0 && index < declarations.Count)
            {
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;
            }
            return imageIndex;
        }

        public override string GetName(int index)
        {
            string name = null;
            if (index >= 0 && index < declarations.Count)
            {
                name = ((TestDeclaration)declarations[index]).Name;
            }
            return name;
        }
    }

    //===================================================
    public class TestAuthoringScope : AuthoringScope
    {
        private TestDeclarations declarationsList;

        public void AddDeclaration(TestDeclaration declaration)
        {
            if (declaration != null)
            {
                if (declarationsList == null)
                {
                    declarationsList = new TestDeclarations();
                }
                declarationsList.AddDeclaration(declaration);
            }
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return declarationsList;
        }

        /////////////////////////////////////////////////
        // Remainder of AuthoringScope methods not shown.
        /////////////////////////////////////////////////
    }

    //===================================================
    class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            TestAuthoringScope scope = new TestAuthoringScope();
            if (req.Reason == ParseReason.MemberSelect ||
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)
            {
                // Gather list of declarations based on what the user
                // has typed so far. In this example, this list is an array of
                // MemberDeclaration objects (a helper class you might implement
                // to hold member declarations).
                // How this list is gathered is dependent on the parser
                // and is not shown here.
                MemberDeclarations memberDeclarations;
                memberDeclarations = GetDeclarationsForScope();

                // Now populate the Declarations list in the authoring scope.
                // GetImageIndexBasedOnType() is a helper method you
                // might implement to convert a member type to an index into
                // the image list returned from the language service.
                foreach (MemberDeclaration dec in memberDeclarations)
                {
                    scope.AddDeclaration(new TestDeclaration(
                                             dec.Name,
                                             GetImageIndexBasedOnType(dec.Type),
                                             dec.Description));
                }
            }
            return scope;
        }
    }
}
```
