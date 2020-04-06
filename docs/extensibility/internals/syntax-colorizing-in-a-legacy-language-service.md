---
title: Sintaxização Colorizando em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704703"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Coloração de sintaxe em um serviço de linguagem herdado
A coloração da sintaxe é uma característica que faz com que diferentes elementos de uma linguagem de programação sejam exibidos em um arquivo de origem em diferentes cores e estilos. Para suportar esse recurso, você precisa fornecer um analisador ou scanner que possa identificar os tipos de elementos léxicos ou tokens no arquivo. Muitas línguas distinguem palavras-chave, delimitadores (como parênteses ou aparelhos), e comentários colorindo-os de diferentes maneiras.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais, consulte [Estendendo o Editor e os Serviços de Idiomas](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="implementation"></a>Implementação
 Para apoiar a colorização, o framework de <xref:Microsoft.VisualStudio.Package.Colorizer> pacote gerenciado (MPF) inclui a classe, que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface. Esta classe interage <xref:Microsoft.VisualStudio.Package.IScanner> com um para determinar o token e as cores. Para obter mais informações sobre scanners, consulte [O Analisador de Serviços de Linguagem Legado e o Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Em <xref:Microsoft.VisualStudio.Package.Colorizer> seguida, a classe marca cada caractere do token com as informações de cor e retorna essas informações ao editor exibindo o arquivo de origem.

 As informações de cor devolvidas ao editor são um índice em uma lista de itens coloridos. Cada item colorível especifica um valor de cor e um conjunto de atributos de fonte, como negrito ou strikethrough. O editor fornece um conjunto de itens coloridos padrão que seu serviço de idioma pode usar. Tudo o que você precisa fazer é especificar o índice de cor apropriado para cada tipo de token. No entanto, você pode fornecer um conjunto de itens coloríveis personalizados e os índices que você fornece para tokens e referenciar sua própria lista de itens coloridos em vez da lista padrão. Você também deve `RequestStockColors` definir a entrada do registro `RequestStockColors` como 0 (ou não especificar a entrada) para suportar cores personalizadas. Você pode definir esta entrada de registro <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> com um parâmetro nomeado para o atributo definido pelo usuário. Para obter mais informações sobre como registrar um serviço de idiomas e definir suas opções, consulte [Registrando um serviço de idioma legado](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Itens personalizados que podem ser coloridos
 Para fornecer seus próprios itens coloridos personalizados, <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> você <xref:Microsoft.VisualStudio.Package.LanguageService> deve substituir o <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> método e o método da classe. O primeiro método retorna o número de itens coloráveis personalizados que o serviço de idioma suporta e o segundo obtém o item colorível personalizado por índice. Você cria a lista padrão de itens coloríveis personalizados. No construtor do seu serviço de idiomas, tudo o que você precisa fazer é fornecer cada item colorível com um nome. O Visual Studio lida automaticamente com o estojo em que o usuário seleciona um conjunto diferente de itens coloridos. Este nome é o que aparece na página de propriedade **Fontes e Cores** na caixa de diálogo **Opções** (disponível no menu Visual Studio **Tools)** e este nome determina qual cor um usuário substituiu. As escolhas do usuário são armazenadas em um cache no registro e acessadas pelo nome da cor. A página de propriedades Fontes e Cores lista todos os nomes de cores em ordem alfabética, para que você possa agrupar suas cores **personalizadas** precedendo cada nome de cor com o nome do idioma; por exemplo, "**TestLanguage-Comment**" e "**TestLanguage-Keyword**". Ou você pode agrupar seus itens coloridos por tipo, "**Comment (TestLanguage)**" e "**Keyword (TestLanguage)**". O agrupamento por nome do idioma é preferido.

> [!CAUTION]
> É fortemente recomendável que você inclua o nome do idioma no nome do item colorível para evitar colisões com nomes de itens coloríveis existentes.

> [!NOTE]
> Se você alterar o nome de uma de suas cores durante o desenvolvimento, você deve redefinir o cache que o Visual Studio criou na primeira vez que suas cores foram acessadas. Você pode fazê-lo executando o comando **Reset the Experimental Hive** do menu do programa Visual Studio SDK.

 Observe que o primeiro item da sua lista de itens coloridos nunca é referenciado. O Visual Studio sempre fornece as cores e atributos de texto padrão para esse item. A maneira mais fácil de lidar com isso é fornecer um item colorível de espaço reservado como o primeiro item.

### <a name="high-color-colorable-items"></a>Itens coloráveis de alta cor
 Itens coloridos também podem suportar valores de cores <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> de 24 bits ou altos através da interface. A <xref:Microsoft.VisualStudio.Package.ColorableItem> classe MPF <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> suporta a interface e as cores de 24 bits são especificadas no construtor, juntamente com as cores normais. Consulte <xref:Microsoft.VisualStudio.Package.ColorableItem> a classe para mais detalhes. O exemplo abaixo mostra como definir as cores de 24 bits para palavras-chave e comentários. As cores de 24 bits são usadas quando a cor de 24 bits é suportada na área de trabalho do usuário; caso contrário, as cores de texto normais são usadas.

 Lembre-se, essas são as cores padrão para o seu idioma; o usuário pode mudar essas cores para o que quiser.

### <a name="example"></a>Exemplo
 Este exemplo mostra uma maneira de declarar e preencher uma <xref:Microsoft.VisualStudio.Package.ColorableItem> matriz de itens coloríveis personalizados usando a classe. Este exemplo define as cores de palavras-chave e comentários usando cores de 24 bits.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>A classe Colorizer e o Scanner
 A <xref:Microsoft.VisualStudio.Package.LanguageService> classe base <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> tem um método <xref:Microsoft.VisualStudio.Package.Colorizer> que instancia a classe. O scanner que é <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> devolvido do método <xref:Microsoft.VisualStudio.Package.Colorizer> é passado para o construtor de classe.

 Você deve <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> implementar o método em <xref:Microsoft.VisualStudio.Package.LanguageService> sua própria versão da classe. A <xref:Microsoft.VisualStudio.Package.Colorizer> classe usa o scanner para obter todas as informações de cor do token.

 O scanner precisa <xref:Microsoft.VisualStudio.Package.TokenInfo> preencher uma estrutura para cada token que encontrar. Esta estrutura contém informações como o comprimento que o token ocupa, o índice de cor a <xref:Microsoft.VisualStudio.Package.TokenTriggers>ser usado, qual tipo é o token e os gatilhos de token (ver ). Apenas o comprimento e o índice de <xref:Microsoft.VisualStudio.Package.Colorizer> cor são necessários para coloração pela classe.

 O índice de <xref:Microsoft.VisualStudio.Package.TokenInfo> cor armazenado na estrutura <xref:Microsoft.VisualStudio.Package.TokenColor> é tipicamente um valor da enumeração, que fornece uma série de índices nomeados correspondentes a vários elementos de linguagem, como palavras-chave e operadores. Se a lista de itens coloridos personalizados corresponder <xref:Microsoft.VisualStudio.Package.TokenColor> aos itens apresentados na enumeração, então você pode usar a enumeração como cor para cada token. No entanto, se você tiver itens coloráveis adicionais ou não quiser usar os valores existentes nessa ordem, você pode organizar sua lista de itens coloridos personalizados para atender às suas necessidades e retornar o índice apropriado para essa lista. Apenas certifique-se de lançar <xref:Microsoft.VisualStudio.Package.TokenColor> o índice para <xref:Microsoft.VisualStudio.Package.TokenInfo> um ao armazená-lo na estrutura; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] vê apenas o índice.

### <a name="example"></a>Exemplo
 O exemplo a seguir mostra como o scanner pode identificar três tipos de tokens: números, pontuação e identificadores (qualquer coisa que não seja um número ou pontuação). Este exemplo é apenas para fins ilustrativos e não representa uma implementação abrangente de analisador e scanner. Ele assume que há `Lexer` uma `GetNextToken()` classe com um método que retorna uma seqüência.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>Confira também
- [Recursos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-features1.md)
- [Analisador e scanner do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)
