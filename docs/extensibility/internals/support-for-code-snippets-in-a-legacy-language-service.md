---
title: Suporte para trechos de código em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704907"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Suporte para snippets de código em um serviço de linguagem herdado
Um trecho de código é um pedaço de código que é inserido no arquivo de origem. O trecho em si é um modelo baseado em XML com um conjunto de campos. Esses campos são destacados após a inserção do trecho e podem ter valores diferentes dependendo do contexto em que o trecho é inserido. Imediatamente após a inserção do trecho, o serviço de idioma pode formatar o trecho.

 O trecho é inserido em um modo de edição especial que permite que os campos do trecho sejam navegados usando a tecla TAB. Os campos podem suportar menus suspensos no estilo IntelliSense. O usuário compromete o trecho ao arquivo de origem digitando a chave ENTER ou ESC. Para saber mais sobre trechos, consulte [Code Snippets](../../ide/code-snippets.md).

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais, consulte [Passo a Passo: Implementando Trechos de Código](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="managed-package-framework-support-for-code-snippets"></a>Suporte ao framework do pacote gerenciado para trechos de código
 O MPF (Managed Package Framework, quadro de pacotes gerenciados) suporta a maioria das funcionalidades de trechos, desde a leitura do modelo até a inserção do trecho e a habilitação do modo de edição especial. O suporte é <xref:Microsoft.VisualStudio.Package.ExpansionProvider> gerenciado através da classe.

 Quando <xref:Microsoft.VisualStudio.Package.Source> a classe é <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> instanciada, <xref:Microsoft.VisualStudio.Package.LanguageService> o método na <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe é chamado <xref:Microsoft.VisualStudio.Package.LanguageService> para obter <xref:Microsoft.VisualStudio.Package.ExpansionProvider> um objeto <xref:Microsoft.VisualStudio.Package.Source> (observe que a classe base sempre retorna um novo objeto para cada objeto).

 O MPF não suporta funções de expansão. Uma função de expansão é uma função nomeada que está incorporada em um modelo de trecho e retorna um ou mais valores para serem colocados em um campo. Os valores são devolvidos pelo <xref:Microsoft.VisualStudio.Package.ExpansionFunction> próprio serviço de linguagem através de um objeto. O <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objeto deve ser implementado pelo serviço de idiomas para suportar funções de expansão.

## <a name="providing-support-for-code-snippets"></a>Fornecendo suporte para trechos de código
 Para habilitar o suporte para trechos de código, você deve fornecer ou instalar os trechos e deve fornecer os meios para que o usuário insira esses trechos. Existem três etapas para habilitar o suporte para trechos de código:

1. Instalando os arquivos de trecho.

2. Habilitando trechos de código para o seu serviço de idioma.

3. Invocando <xref:Microsoft.VisualStudio.Package.ExpansionProvider> o objeto.

### <a name="installing-the-snippet-files"></a>Instalando os arquivos de snippet
 Todos os trechos de um idioma são armazenados como modelos em arquivos XML, normalmente um modelo de trecho por arquivo. Para obter detalhes sobre o esquema XML usado para modelos de trechos de código, consulte [Code Snippets Schema Reference](../../ide/code-snippets-schema-reference.md). Cada modelo de trecho é identificado com um ID de idioma. Este ID de idioma é especificado no `Language` registro \<e é colocado no atributo da marca Code> no modelo.

 Existem tipicamente dois locais onde os arquivos de modelo de trecho são armazenados: 1) onde seu idioma foi instalado e 2) na pasta do usuário. Esses locais são adicionados ao registro para que o Gerenciador **de Trechos de Código visual** do estúdio possa encontrar os trechos. A pasta do usuário é onde os trechos criados pelo usuário são armazenados.

 O layout típico da pasta para os arquivos de modelo de trecho instalados é\\assim: *[InstallRoot]*\\ *[TestLanguage]* \Snippets *[LCID]* \Snippets.

 *[InstallRoot]* é a pasta em que seu idioma está instalado.

 *[TestLanguage]* é o nome do seu idioma como um nome de pasta.

 *[LCID]* é o ID local. É assim que as versões localizadas de seus trechos são armazenadas. Por exemplo, o ID local para inglês é 1033, então *[LCID]* é substituído por 1033.

 Um arquivo adicional deve ser fornecido e esse é um arquivo de índice, tipicamente chamado SnippetsIndex.xml ou ExpansionsIndex.xml (você pode usar qualquer nome de arquivo válido terminando em .xml). Este arquivo é normalmente armazenado na pasta *[InstallRoot]*\\ *[TestLanguage]* e especifica a localização exata da pasta de trechos, bem como o ID de idioma e GUID do serviço de idioma que usa os trechos. O caminho exato do arquivo de índice é colocado no registro conforme descrito posteriormente em "Instalação das Entradas de Registro". Aqui está um exemplo de um arquivo SnippetsIndex.xml:

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 A \<tag> idioma especifica o `Lang` ID do idioma (o atributo) e o serviço de idioma GUID.

 Este exemplo pressupõe que você tenha instalado seu serviço de idioma na pasta de instalação do Visual Studio. O %LCID% é substituído pelo ID local atual do usuário. Várias \<tags SnippetDir> podem ser adicionadas, uma para cada diretório e local diferentes. Além disso, uma pasta de trecho pode conter subpastas, cada uma \<das quais é identificada no arquivo \<de índice com a tag SnippetSubDir> que está incorporada em uma tag SnippetDir>.

 Os usuários também podem criar seus próprios trechos para o seu idioma. Estes são normalmente armazenados na pasta de configurações do usuário, por\\exemplo *[TestDocs]* \Code Snippets *[TestLanguage]* \Test Code Snippets, onde *[TestDocs]* é a localização da pasta de configurações do usuário para o Visual Studio.

 Os seguintes elementos de substituição podem \<ser colocados no caminho armazenado na> de DirPath no arquivo de índice.

|Elemento|Descrição|
|-------------|-----------------|
|%LCID%|ID Locale.|
|%InstallRoot%|Pasta de instalação raiz para o Visual Studio, por exemplo, C:\Program Files\Microsoft Visual Studio 8.|
|%ProjDir%|Pasta contendo o projeto atual.|
|%ProjItem%|Pasta contendo o item atual do projeto.|
|%TestDocs%|Pasta na pasta de configurações do usuário, por exemplo,\\C:\Documentos e Configurações *[nome de usuário]* \Meus documentos\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Habilitando trechos de código para o seu serviço de idioma
 Você pode habilitar trechos de código <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> para o seu serviço de idioma adicionando o atributo ao seu VSPackage (consulte [Registrando um serviço de idioma legado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obter detalhes). Os <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parâmetros e parâmetros são `SearchPaths` opcionais, mas você deve incluir o parâmetro nomeado para informar o **Gerenciador de trechos** de código da localização de seus trechos.

 A seguir, um exemplo de como usar este atributo:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Chamando o Provedor de Expansão
 O serviço de idiomacontrola a inserção de qualquer trecho de código, bem como a forma como a inserção é invocada.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Chamando o provedor de expansão para trechos de código
 Existem duas maneiras de invocar o provedor de expansão: usando um comando de menu ou usando um atalho de uma lista de conclusão.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Inserindo um trecho de código usando um comando menu
 Para usar um comando de menu para exibir o navegador de <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> trecho, <xref:Microsoft.VisualStudio.Package.ExpansionProvider> adicione um comando de menu e, em seguida, chame o método na interface em resposta a esse comando menu.

1. Adicione um comando e um botão ao seu arquivo .vsct. Você pode encontrar instruções para [fazê-lo](../../extensibility/creating-an-extension-with-a-menu-command.md)em Criar uma extensão com um comando menu .

2. Obtenha uma classe <xref:Microsoft.VisualStudio.Package.ViewFilter> da classe <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> e anule o método para indicar suporte para o novo comando menu. Este exemplo sempre permite o comando menu.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. Anular o <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> método <xref:Microsoft.VisualStudio.Package.ViewFilter> na classe <xref:Microsoft.VisualStudio.Package.ExpansionProvider> para obter <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> o objeto e chamar o método sobre esse objeto.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     Os seguintes métodos na <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe são chamados pelo Visual Studio na ordem dada durante o processo de inserção do trecho:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Depois <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> que o método é chamado, o trecho <xref:Microsoft.VisualStudio.Package.ExpansionProvider> foi inserido e o objeto está em um modo de edição especial usado para modificar um trecho que acaba de ser inserido.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Inserindo um trecho de código usando um atalho
 A implementação de um atalho de uma lista de conclusão está muito mais envolvida do que implementar um comando de menu. Primeiro, você deve adicionar atalhos de trecho à lista de conclusão de palavras do IntelliSense. Em seguida, você deve detectar quando um nome de atalho de trecho foi inserido como resultado da conclusão. Finalmente, você deve obter o título e o caminho do trecho <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> usando <xref:Microsoft.VisualStudio.Package.ExpansionProvider> o nome do atalho e passar essas informações para o método no método.

 Para adicionar atalhos de trecho à lista de <xref:Microsoft.VisualStudio.Package.Declarations> conclusão de <xref:Microsoft.VisualStudio.Package.AuthoringScope> palavras, adicione-os ao objeto da sua classe. Você deve ter certeza de que pode identificar o atalho como um nome de trecho. Por exemplo, consulte [Passo a Passo: Obtendo uma lista de trechos de código instalados (implementação legado)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Você pode detectar a inserção do <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> atalho de <xref:Microsoft.VisualStudio.Package.Declarations> trecho de código no método da classe. Como o nome do trecho já foi inserido no arquivo de origem, ele deve ser removido quando a expansão for inserida. O <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> método toma um período que descreve o ponto de inserção para o trecho; se a extensão incluir o nome de trecho inteiro no arquivo de origem, esse nome será substituído pelo trecho.

 Aqui está uma <xref:Microsoft.VisualStudio.Package.Declarations> versão de uma classe que lida com a inserção de trechos dado um nome de atalho. Outros métodos <xref:Microsoft.VisualStudio.Package.Declarations> da classe foram omitidos para clareza. Note que o construtor desta <xref:Microsoft.VisualStudio.Package.LanguageService> classe leva um objeto. Isso pode ser passado a <xref:Microsoft.VisualStudio.Package.AuthoringScope> partir de sua versão do <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto (por exemplo, sua implementação da classe pode pegar o <xref:Microsoft.VisualStudio.Package.LanguageService> objeto em seu construtor e passar esse objeto para o construtor `TestDeclarations` da classe).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 Quando o serviço de idioma recebe <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> o nome do atalho, ele chama o método para obter o nome do arquivo e o título do trecho de código. O serviço de <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> idiomas <xref:Microsoft.VisualStudio.Package.ExpansionProvider> então chama o método na classe para inserir o trecho de código. Os seguintes métodos são chamados pelo Visual <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Studio na ordem dada na classe durante o processo de inserção do trecho:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Para obter mais informações sobre como obter uma lista de trechos de código instalados para o serviço de idioma, consulte [Passo a Passo: Obtendo uma lista de trechos de código instalados (Implementação legado)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implementando a classe expansionfunction class
 Uma função de expansão é uma função nomeada que está incorporada em um modelo de trecho e retorna um ou mais valores para serem colocados em um campo. Para suportar funções de expansão em seu serviço de <xref:Microsoft.VisualStudio.Package.ExpansionFunction> idioma, <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> você deve derivar uma classe da classe e implementar o método. Em seguida, você <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> deve <xref:Microsoft.VisualStudio.Package.LanguageService> substituir o método na classe para retornar <xref:Microsoft.VisualStudio.Package.ExpansionFunction> uma nova instanciação da sua versão da classe para cada função de expansão que você suporta. Se você apoiar uma lista de valores possíveis de <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> uma função <xref:Microsoft.VisualStudio.Package.ExpansionFunction> de expansão, você também deve substituir o método na classe para retornar uma lista desses valores.

 Uma função de expansão que leva argumentos ou necessidades para acessar outros campos não deve ser associada a um campo editável, pois o provedor de expansão pode não ser totalmente inicializado no momento em que a função de expansão é chamada. Como resultado, a função de expansão não é capaz de obter o valor de seus argumentos ou qualquer outro campo.

### <a name="example"></a>Exemplo
 Aqui está um exemplo de como `GetName` uma simples função de expansão chamada pode ser implementada. Esta função de expansão anexa um número a um nome de classe base cada vez que a função de expansão é instanciada (o que corresponde a cada vez que o trecho de código associado é inserido).

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>Confira também
- [Recursos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Snippets de código](../../ide/code-snippets.md)
- [Passo a passo: obtendo uma lista de snippets de código instalados (implementação herdada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
