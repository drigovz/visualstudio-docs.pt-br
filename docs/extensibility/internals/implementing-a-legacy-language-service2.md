---
title: Implementando um serviço de linguagem legado2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707670"
---
# <a name="implementing-a-legacy-language-service"></a>Implementando um serviço de linguagem herdado
Para implementar um serviço de idioma usando o mpf (framework <xref:Microsoft.VisualStudio.Package.LanguageService> de pacote gerenciado), você deve obter uma classe da classe e implementar os seguintes métodos e propriedades abstratas:

- O método <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- O método <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- O método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- A propriedade <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Consulte as seções apropriadas abaixo para obter detalhes sobre a implementação desses métodos e propriedades.

  Para suportar recursos adicionais, seu serviço de idiomas pode ter que derivar uma classe de uma das classes de serviço de idiomas do MPF; por exemplo, para suportar comandos adicionais de <xref:Microsoft.VisualStudio.Package.ViewFilter> menu, você deve derivar uma classe <xref:Microsoft.VisualStudio.Package.ViewFilter> da classe e substituir vários dos métodos de manipulação de comandos (veja para obter detalhes). A <xref:Microsoft.VisualStudio.Package.LanguageService> classe fornece uma série de métodos que são chamados para criar novas instâncias de várias classes e você anula o método de criação apropriado para fornecer uma instância de sua classe. Por exemplo, você precisa <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> substituir o <xref:Microsoft.VisualStudio.Package.LanguageService> método na classe para <xref:Microsoft.VisualStudio.Package.ViewFilter> retornar uma instância de sua própria classe. Consulte a seção "Instanciando classes personalizadas" para obter mais detalhes.

  Seu serviço de idiomas também pode fornecer seus próprios ícones, que são usados em muitos lugares. Por exemplo, quando uma lista de conclusão do IntelliSense é mostrada, cada item da lista pode ter um ícone associado a ele, marcando o item como um método, classe, namespace, propriedade ou o que for necessário para o seu idioma. Esses ícones são usados em todas as listas do IntelliSense, na **barra de navegação**e na janela de **tarefas Lista de** erros. Consulte a seção "Imagens de Serviço de Linguagem" abaixo para obter detalhes.

## <a name="getlanguagepreferences-method"></a>Método GetLanguagePreferences
 O <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> método sempre retorna a <xref:Microsoft.VisualStudio.Package.LanguagePreferences> mesma instância de uma classe. Você pode usar <xref:Microsoft.VisualStudio.Package.LanguagePreferences> a classe base se não precisar de preferências adicionais para o seu serviço de idioma. As aulas de serviço suinotístico do MPF assumem a presença de pelo menos a classe de base. <xref:Microsoft.VisualStudio.Package.LanguagePreferences>

### <a name="example"></a>Exemplo
 Este exemplo mostra uma <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> implementação típica do método. Este exemplo usa <xref:Microsoft.VisualStudio.Package.LanguagePreferences> a classe base.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>Método GetScanner
 Este método retorna uma <xref:Microsoft.VisualStudio.Package.IScanner> instância de um objeto que implementa um analisador ou scanner orientado para linha usado para obter tokens e seus tipos e gatilhos. Este scanner é <xref:Microsoft.VisualStudio.Package.Colorizer> usado na classe para coloração, embora o scanner também possa ser usado para obter tipos de tokens e gatilhos como um prelúdio para uma operação de análise mais complexa. Você deve fornecer a classe <xref:Microsoft.VisualStudio.Package.IScanner> que implementa a interface e <xref:Microsoft.VisualStudio.Package.IScanner> você deve implementar todos os métodos na interface.

### <a name="example"></a>Exemplo
 Este exemplo mostra uma <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> implementação típica do método. A `TestScanner` classe implementa a <xref:Microsoft.VisualStudio.Package.IScanner> interface (não mostrada).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>Método ParseSource
 Analisa o arquivo de origem com base em várias razões diferentes. Este método recebe <xref:Microsoft.VisualStudio.Package.ParseRequest> um objeto que descreve o que é esperado de uma determinada operação de análise. O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método invoca um analisador mais complexo que determina a funcionalidade e o escopo do token. O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método é usado no suporte para operações IntelliSense, bem como na correspondência de chaves. Mesmo que você não suporte operações tão avançadas, você ainda deve retornar um objeto válido <xref:Microsoft.VisualStudio.Package.AuthoringScope> e isso exige que você crie uma classe que implemente a <xref:Microsoft.VisualStudio.Package.AuthoringScope> interface e implemente todos os métodos nessa interface. Você pode devolver valores nulos <xref:Microsoft.VisualStudio.Package.AuthoringScope> de todos os métodos, mas o objeto em si não deve ser um valor nulo.

### <a name="example"></a>Exemplo
 Este exemplo mostra uma <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> implementação <xref:Microsoft.VisualStudio.Package.AuthoringScope> mínima do método e da classe, suficiente para permitir que o serviço de idiomas compile e funcione sem realmente suportar qualquer um dos recursos mais avançados.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Propriedade Name
 Esta propriedade retorna o nome do serviço de idiomas. Este deve ser o mesmo nome dado quando o serviço de idiomas foi registrado. Este nome é usado em vários lugares, sendo o <xref:Microsoft.VisualStudio.Package.LanguagePreferences> mais proeminente o nome onde o nome é usado para acessar o registro. O nome devolvido por esta propriedade não deve ser localizado, pois é usado no registro para entrada de registro e nomes-chave.

### <a name="example"></a>Exemplo
 Este exemplo mostra uma <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> possível implementação da propriedade. Observe que o nome aqui é codificado: o nome real deve ser obtido a partir de um arquivo de recursos para que ele possa ser usado no registro de um serviço de idioma (consulte [Registrando um Serviço de Linguagem Legado](../../extensibility/internals/registering-a-legacy-language-service1.md)).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>Instantivaaulas Personalizadas
 Os seguintes métodos nas classes especificadas podem ser substituídos para fornecer instâncias de suas próprias versões de cada classe.

### <a name="in-the-languageservice-class"></a>Na aula LanguageService

|Método|Classe Devolvida|Descrição|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Para suportar adições personalizadas à exibição de texto.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Para suportar propriedades de documentos personalizados.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Para suportar a **barra de navegação**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Para suportar funções em modelos de trecho de código.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Para suportar trechos de código (este método normalmente não é substituído).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Para suportar a <xref:Microsoft.VisualStudio.Package.ParseRequest> personalização da estrutura (este método normalmente não é substituído).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Para suportar a formatação do código-fonte, especificar caracteres de comentários e personalizar assinaturas do método.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Para suportar comandos adicionais do menu.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Para suportar o destaque da sintaxe (este método normalmente não é substituído).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Para apoiar o acesso às preferências de idioma. Este método deve ser implementado, mas pode retornar uma instância da classe base.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Para fornecer um analisador usado para identificar tipos de tokens em uma linha. Este método deve <xref:Microsoft.VisualStudio.Package.IScanner> ser implementado e deve ser derivado.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Para fornecer um analisador usado para identificar funcionalidade e escopo em todo um arquivo de origem. Este método deve ser implementado e deve retornar <xref:Microsoft.VisualStudio.Package.AuthoringScope> uma instância de sua versão da classe. Se tudo o que você quer suportar é <xref:Microsoft.VisualStudio.Package.IScanner> o destaque da <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> sintaxe (que requer o parser retornado do método), você não pode fazer nada neste método além de retornar uma versão da <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe cujos métodos todos retornam valores nulos.|

### <a name="in-the-source-class"></a>Na Classe de Origem

|Método|Classe Devolvida|Descrição|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Para personalizar a exibição das listas de conclusão do IntelliSense (este método normalmente não é substituído).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Para suportar marcadores na lista de tarefas Lista de erros; especificamente, suporte para recursos além de abrir o arquivo e saltar para a linha que causou o erro.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Para personalizar a exibição do IntelliSense Parameter Info ToolTips.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Por apoiar o código de comentários.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Para coletar informações durante a operação de análise.|

### <a name="in-the-authoringscope-class"></a>Na classe AuthoringScope

|Método|Classe Devolvida|Descrição|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Fornece uma lista de declarações, como membros ou tipos. Este método deve ser implementado, mas pode retornar um valor nulo. Se este método retornar um objeto válido, o objeto <xref:Microsoft.VisualStudio.Package.Declarations> deve ser uma instância da sua versão da classe.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Fornece uma lista de assinaturas de método satisfaz um determinado contexto. Este método deve ser implementado, mas pode retornar um valor nulo. Se este método retornar um objeto válido, o objeto <xref:Microsoft.VisualStudio.Package.Methods> deve ser uma instância da sua versão da classe.|

## <a name="language-service-images"></a>Imagens de serviço de idioma
 Para fornecer uma lista de ícones a serem usados em todo o serviço de idiomas, anule o <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método na <xref:Microsoft.VisualStudio.Package.LanguageService> classe e retorne um <xref:System.Windows.Forms.ImageList> contendo os ícones. A <xref:Microsoft.VisualStudio.Package.LanguageService> classe base carrega um conjunto padrão de ícones. Uma vez que você especifica o índice exato de imagem nesses lugares que precisam de ícones, como você organiza sua própria lista de imagens depende inteiramente de você.

### <a name="images-used-in-intellisense-completion-lists"></a>Imagens usadas nas listas de conclusão do IntelliSense
 Para listas de conclusão do IntelliSense, o índice <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> de imagem <xref:Microsoft.VisualStudio.Package.Declarations> é especificado para cada item no método da classe, que você deve substituir se quiser fornecer um índice de imagem. O valor retornado <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> do método é um índice <xref:Microsoft.VisualStudio.Package.CompletionSet> na lista de imagens fornecida ao construtor <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> de <xref:Microsoft.VisualStudio.Package.LanguageService> classe e que é a mesma <xref:Microsoft.VisualStudio.Package.CompletionSet> lista de imagens devolvida do método na classe (você pode alterar qual lista de imagens usar para o se você substituir o <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> método na <xref:Microsoft.VisualStudio.Package.Source> classe para fornecer uma lista de imagem diferente).

### <a name="images-used-in-the-navigation-bar"></a>Imagens usadas na barra de navegação
 A **barra de navegação** exibe listas de tipos e membros e é usada para navegação rápida pode mostrar ícones. Esses ícones são obtidos a partir do <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método da <xref:Microsoft.VisualStudio.Package.LanguageService> classe e não podem ser substituídos especificamente para a barra de **navegação**. Os índices usados para cada item nas caixas de combinação são especificados quando as <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> listas que <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> representam as caixas de combinação são preenchidas no método da classe (consulte [Suporte para a Barra de Navegação em um Serviço de Linguagem Legado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Esses índices de imagem são obtidos de alguma forma <xref:Microsoft.VisualStudio.Package.Declarations> a partir do analisador, tipicamente através de sua versão da classe. Como os índices são obtidos depende inteiramente de você.

### <a name="images-used-in-the-error-list-task-window"></a>Imagens usadas na janela de tarefa da lista de erros
 Sempre <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> que o analisador de método (ver [Analisador de Serviço de Linguagem Legado e Scanner)](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)encontrar um erro e passar esse erro para o <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> método na <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe, o erro é relatado na janela de tarefa Lista de **erros.** Um ícone pode ser associado a cada item que aparece na janela de tarefas e esse ícone vem da mesma lista de imagens retornada do <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> método na <xref:Microsoft.VisualStudio.Package.LanguageService> classe. O comportamento padrão das classes do MPF é não mostrar uma imagem com a mensagem de erro. No entanto, você pode anular esse comportamento, derivando uma classe da <xref:Microsoft.VisualStudio.Package.Source> classe e substituindo o <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> método. Nesse método, você cria <xref:Microsoft.VisualStudio.Package.DocumentTask> um novo objeto. Antes de retornar esse objeto, <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> você <xref:Microsoft.VisualStudio.Package.DocumentTask> pode usar a propriedade no objeto para definir o índice de imagem. Isso se pareceria com o seguinte exemplo. Note `TestIconImageIndex` que é uma enumeração que lista todos os ícones e é específica para este exemplo. Você pode ter uma maneira diferente de identificar ícones no seu serviço de idioma.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>A lista de imagens padrão para um serviço de idioma
 A lista de imagens padrão fornecida suprida com as classes de serviço de idioma sinuoso do MPF contém uma série de ícones associados aos elementos de idioma mais comuns. A maior parte desses ícones está disposta em conjuntos de seis variações, correspondendo aos conceitos de acesso de público, interno, amigo, protegido, privado e atalho. Por exemplo, você pode ter diferentes ícones para um método, dependendo se ele é público, protegido ou privado.

 A enumeração a seguir especifica nomes típicos para cada conjunto de ícones e especifica o índice associado. Por exemplo, com base na enumeração, você pode especificar o índice de imagem para um método protegido como `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Você pode alterar os nomes nesta enumeração conforme desejado.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>Confira também
- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Visão geral do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-overview.md)
- [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Analisador e scanner do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
