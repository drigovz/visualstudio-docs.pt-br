---
title: Gerar arquivos de um modelo UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 832dc3f7fea959ff4d2834aba921cd16f1117b5c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666142"
---
# <a name="generate-files-from-a-uml-model"></a>Gerar arquivos por meio de um modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De um modelo UML, você pode gerar código de programa, esquemas, documentos, recursos e outros artefatos de qualquer tipo. Um método conveniente para gerar arquivos de texto a partir de um modelo UML é usar [modelos de texto](../modeling/code-generation-and-t4-text-templates.md). Eles permitem que você incorpore o código do programa dentro do texto que você deseja gerar.

 Há três cenários principais:

- [Gerando arquivos de um comando de menu](#Command) ou gesto. Você define um comando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que está disponível em modelos UML.

- [Gerando arquivos de um aplicativo](#Application). Você escreve um aplicativo que lê modelos UML e gera arquivos.

- [Gerando em tempo de design](#Design). Você usa um modelo para definir algumas das funcionalidades do aplicativo e gera código, recursos e assim por diante dentro de sua solução de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

  Este tópico termina com uma discussão sobre [como usar a geração de texto](#What). Para obter mais informações, consulte [geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="Command"></a>Gerando arquivos de um comando de menu
 Você pode usar modelos de texto de pré-processamento em um comando de menu UML. Dentro do código do modelo de texto ou em uma classe parcial separada, você pode ler o modelo que é exibido pelo diagrama.

 Para obter mais informações sobre esses recursos, leia os seguintes tópicos:

- [Definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [Geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)

- [Navegar no modelo UML](../modeling/navigate-the-uml-model.md)

  A abordagem demonstrada no exemplo a seguir é adequada para gerar texto de um único modelo, quando você inicia a operação a partir de um dos diagramas de modelo. Para processar um modelo em um contexto separado, considere usar o [Visual Studio ModelBus](../modeling/integrate-uml-models-with-other-models-and-tools.md) para acessar o modelo e seus elementos.

### <a name="example"></a>Exemplo
 Para executar este exemplo, crie um projeto de VSIX (extensão de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]). O nome do projeto que é usado neste exemplo é `VdmGenerator`. No arquivo **Source. Extension. vsixmanifest** , clique em **adicionar conteúdo** e defina o campo tipo como **componente MEF** e caminho de origem referenciando o projeto atual. Para obter mais informações sobre como configurar esse tipo de projeto, consulte [definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

 Adicione ao projeto um C# arquivo que contém o código a seguir. Essa classe define um comando de menu que será exibido em um diagrama de classes UML.

```
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace VdmGenerator
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  public class GenerateVdmFromClasses : ICommandExtension
  {
    [Import] public IDiagramContext DiagramContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      // Initialize the template with the Model Store.
      VdmGen generator = new VdmGen(
             DiagramContext.CurrentDiagram.ModelStore);
      // Generate the text and write it.
      System.IO.File.WriteAllText
        (System.IO.Path.Combine(
            Environment.GetFolderPath(
                Environment.SpecialFolder.Desktop),
            "Generated.txt")
         , generator.TransformText());
    }
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }
    public string Text
    { get { return "Generate VDM"; } }
  }
}
```

 O arquivo a seguir é o modelo de texto. Ele gera uma linha de texto para cada classe UML no modelo e uma linha para cada atributo em cada classe. O código para ler o modelo é inserido no texto, delimitado por `<# ... #>`.

 Para criar esse arquivo, clique com o botão direito do mouse no projeto no Gerenciador de Soluções, aponte para **Adicionar**e clique em **novo item**. Selecione o **modelo de texto pré-processado**. O nome do arquivo para este exemplo deve ser **VdmGen.tt**. A propriedade da **ferramenta personalizada** do arquivo deve ser **TextTemplatingFilePreprocessor**. Para obter mais informações sobre modelos de texto pré-processados, consulte [geração de texto em tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

```
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#
   foreach (IClass classElement in store.AllInstances<IClass>())   {
#>
Type <#= classElement.Name #> ::
<#
     foreach (IProperty attribute in classElement.OwnedAttributes)     {
#>
       <#= attribute.Name #> : <#=
           attribute.Type == null ? ""
                                  : attribute.Type.Name #>
<#
     }   }
#>
```

 O modelo de texto gera C# uma classe parcial, que se torna parte de seu projeto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Em um arquivo separado, adicione outra declaração parcial da mesma classe. Esse código fornece o modelo com acesso ao armazenamento de modelos UML:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
namespace VdmGenerator
{
    public partial class VdmGen
    {
        private IModelStore store;
        public VdmGen(IModelStore s)
        { store = s; }
    }
}
```

 Para testar o projeto, pressione **F5**. Uma nova instância do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] será iniciada. Nessa instância, abra ou crie um modelo UML que contenha um diagrama de classe. Adicione algumas classes ao diagrama e adicione alguns atributos a cada classe. Clique com o botão direito do mouse no diagrama e clique no comando de exemplo `Generate VDM`. O comando cria o arquivo `C:\Generated.txt`. Inspecione este arquivo. Seu conteúdo deve se parecer com o texto a seguir, mas listará suas próprias classes e atributos:

```
Type Class1 ::
          Attribute1 : int
          Attribute2 : string
Type Class2 ::
          Attribute3 : string
```

## <a name="Application"></a>Gerando arquivos de um aplicativo
 Você pode gerar arquivos de um aplicativo que lê um modelo UML. Para essa finalidade, o método mais flexível e robusto de acessar o modelo e seus elementos é o [Visual Studio ModelBus](../modeling/integrate-uml-models-with-other-models-and-tools.md).

 Você também pode usar a API básica para carregar o modelo e passar o modelo para modelos de texto usando as mesmas técnicas da seção anterior. Para obter mais informações sobre como carregar um modelo, consulte [ler um modelo UML no código do programa](../modeling/read-a-uml-model-in-program-code.md).

## <a name="Design"></a>Gerando arquivos em tempo de design
 Se o seu projeto tiver um método padrão de interpretação de UML como código, você poderá criar modelos de texto que permitem gerar código em seu projeto a partir de um modelo UML. Normalmente, você teria uma solução que contém o projeto de modelo UML e um ou mais projetos para o código do aplicativo. Cada projeto de código pode conter vários modelos que geram código de programa, recursos e arquivos de configuração, com base no conteúdo do modelo. O desenvolvedor pode executar todos os modelos clicando na barra de ferramentas **transformar todos os modelos** na Gerenciador de soluções. O código do programa geralmente é gerado na forma de classes parciais, para facilitar a integração de partes escritas manualmente.

 Um projeto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] desse tipo pode ser distribuído na forma de um modelo, de modo que todos os membros de uma equipe possam criar projetos que gerem código de um modelo da mesma maneira. Normalmente, o modelo faz parte de um pacote de extensão que inclui restrições de validação no modelo para garantir que as pré-condições do código de geração sejam atendidas.

### <a name="outline-procedure-for-generating-files"></a>Procedimento de estrutura de tópicos para gerar arquivos

- Para adicionar um modelo a um projeto, selecione **modelo de texto** na caixa de diálogo Adicionar novo arquivo. Você pode adicionar um modelo à maioria dos tipos de projeto, mas não modelar projetos.

- A propriedade de ferramentas personalizadas do arquivo de modelo deve ser **TextTemplatingFileGenerator**e a extensão de nome de arquivo deve ser. tt.

- O modelo deve ter pelo menos uma diretiva de saída:

     `<#@ output extension=".cs" #>`

     Defina o campo de extensão de acordo com o idioma do seu projeto.

- Para permitir que o código de geração em seu modelo acesse o modelo, grave `<#@ assembly #>` diretivas para os assemblies necessários para ler um modelo UML. Use `ModelingProject.LoadReadOnly()` para abrir o modelo. Para obter mais informações, consulte [ler um modelo UML no código do programa](../modeling/read-a-uml-model-in-program-code.md).

- O modelo é executado quando você o salva e quando clica em **transformar todos os modelos** na barra de ferramentas Gerenciador de soluções.

- Para obter mais informações sobre esse tipo de modelo, consulte [geração de código em tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

- Em um projeto típico, você terá vários modelos que geram arquivos diferentes do mesmo modelo. A primeira parte de cada modelo será a mesma. Para reduzir essa duplicação, mova as partes comuns para um arquivo de texto separado e, em seguida, invoque-as usando a diretiva `<#@include file="common.txt"#>` em cada modelo.

- Você também pode definir um processador de diretiva especializado que permite que você forneça parâmetros para o processo de geração de texto. Para obter mais informações, consulte [Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md).

### <a name="example"></a>Exemplo
 Este exemplo gera uma C# classe para cada classe UML no modelo de origem.

##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Para configurar uma solução do Visual Studio para este exemplo

1. Crie um diagrama de classe UML em um projeto de modelagem em uma nova solução.

   1. No menu **arquitetura** , clique em **novo diagrama**.

   2. Selecione **diagrama de classe UML**.

   3. Siga os prompts para criar um novo projeto de solução e modelagem.

   4. Adicione algumas classes ao diagrama arrastando a ferramenta de classe UML da caixa de ferramentas.

   5. Salve o arquivo.

2. Crie um C# ou Visual Basic projeto na mesma solução.

   - Em Gerenciador de Soluções, clique com o botão direito do mouse na solução, aponte para **Adicionar**e clique em **novo projeto**. Em **modelos instalados**, clique **em Visual Basic** ou  **C#visual e,** em seguida, selecione um tipo de projeto, como aplicativo de **console**.

3. Adicione um arquivo de texto sem formatação C# ao projeto do ou Visual Basic. Esse arquivo conterá o código compartilhado se você quiser escrever vários modelos de texto.

   - Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto, aponte para **Adicionar**e clique em **novo item**. Selecione **arquivo de texto**.

     Insira o texto mostrado na seção a seguir.

4. Adicione um arquivo de modelo de texto C# ao projeto do ou Visual Basic.

   - Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto, aponte para **Adicionar**e clique em **novo item**. Selecione o **modelo de texto**.

     Insira o código a seguir no arquivo de modelo de texto.

5. Salve o arquivo de modelo de texto.

6. Inspecione o código no arquivo da subsidiária. Ele deve conter uma classe para cada classe UML no modelo.

   1. Em um projeto Visual Basic, clique em **Mostrar todos os arquivos** na barra de ferramentas Gerenciador de soluções.

   2. Expanda o nó arquivo de modelo em Gerenciador de Soluções.

#### <a name="content-of-the-shared-text-file"></a>Conteúdo do arquivo de texto compartilhado
 Neste exemplo, o arquivo é chamado de SharedTemplateCode. txt e está na mesma pasta que os modelos de texto.

```
<# /* Common material for inclusion in my model templates */ #>
<# /* hostspecific allows access to the Visual Studio API */ #>
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>
<#+  // Note this is a Class Feature Block
///<summary>
/// Text templates are run in a common AppDomain, so
/// we can cache the model store that we find.
///</summary>
private IModelStore StoreCache
{
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }
}
private bool CacheIsOld()
{
    DateTime? dt = AppDomain.CurrentDomain
           .GetData("latestAccessTime") as DateTime?;
    DateTime t = dt.HasValue ? dt.Value : new DateTime();
    DateTime now = DateTime.Now;
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);
    return now.Subtract(t).Seconds > 3;
}

///<summary>
/// Find the UML modeling project in this solution,
/// and load the model.
///</summary>
private IModelStore ModelStore
{
  get
  {
    // Avoid loading the model for every template:
    if (StoreCache == null || CacheIsOld())
    {
      // Use Visual Studio API to find modeling project:
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
      EnvDTE.Project project = null;
      foreach (EnvDTE.Project p in dte.Solution.Projects)
      {
        if (p.FullName.EndsWith(".modelproj"))
        {
          project = p;
          break;
        }
      }
      if (project == null) return null;

      // Load UML model into this AppDomain
      // and access model store:
      IModelingProjectReader reader =
           ModelingProject.LoadReadOnly(project.FullName);
      StoreCache = reader.Store;
    }
    return StoreCache;
  }
}
#>
```

#### <a name="content-of-the-text-template-file"></a>Conteúdo do arquivo de modelo de texto
 O texto a seguir é colocado no arquivo **. tt** . Este exemplo gera classes em um C# arquivo a partir das classes UML no modelo. No entanto, você pode gerar arquivos de qualquer tipo. O idioma do arquivo gerado não está relacionado ao idioma no qual o código do modelo de texto é escrito.

```
<#@include file="SharedTemplateCode.txt"#>
<#@ output extension=".cs" #>
namespace Test{
<#
      foreach (IClass c in ModelStore.AllInstances<IClass>())
      {
#>
   public partial class <#=c.Name#>
   {   }
<#
      }
#>
}
```

## <a name="What"></a>Como usar a geração de texto
 O poder real da modelagem é obtido quando você usa modelos para projetar no nível de requisitos ou arquitetura. Você pode usar modelos de texto para fazer parte do trabalho de converter as ideias de alto nível no código. Em muitos casos, isso não leva a uma correspondência de um para um entre os elementos nos modelos UML e as classes ou outras partes do código do programa.

 Além disso, a transformação depende do seu domínio problemático; Não há mapeamento universal entre modelos e código.

 Aqui estão alguns exemplos de como gerar código a partir de modelos:

- **Linhas de produtos**. A Fabrikam, Inc. cria e instala sistemas de manuseio de bagagem de aeroportos. Grande parte do software é muito semelhante entre uma instalação e a próxima, mas a configuração do software depende de qual conjunto de máquinas de manuseio está instalado e de como essas partes são interconectadas por esteiras transportadoras. No início de um contrato, os analistas da Fabrikam abordam os requisitos com o gerenciamento de aeroportos e capturam o plano de hardware usando um diagrama de atividades UML. A partir desse modelo, a equipe de desenvolvimento gera arquivos de configuração, código de programa, planos e documentos de usuário. Eles concluem o trabalho por adições manuais e ajustes no código. À medida que eles recebem experiência de um trabalho para o outro, eles estendem o escopo do material gerado.

- **Padrões**. Os desenvolvedores da Contoso, Ltd geralmente criam sites da Web e projetam o esquema de navegação usando diagramas de classe UML. Cada página da Web é representada por uma classe e as associações representam links de navegação. Os desenvolvedores geram grande parte do código de um site a partir do modelo. Cada página da Web corresponde a várias classes e entradas de arquivo de recurso.  Esse método tem os benefícios que a construção de cada página está em conformidade com um único padrão, tornando-o mais confiável e flexível do que o código escrito à mão. O padrão está na geração de modelos, enquanto o modelo é usado para capturar os aspectos variáveis.

- **Esquemas**. A Humongous Insurance tem milhares de sistemas no mundo todo. Esses sistemas usam diferentes bancos de dados, linguagens e interfaces. A equipe de arquitetura central publica modelos internos de processos e conceitos de negócios. A partir desses modelos, as equipes locais geram partes de seus esquemas de banco de dados e intercâmbio, declarações no código do programa e assim por diante. A apresentação gráfica dos modelos ajuda as equipes a discutir as propostas. As equipes criam vários diagramas que mostram subconjuntos do modelo que se aplicam a diferentes áreas de negócios. Eles também usam cores para realçar áreas sujeitas a alterações.

## <a name="important-techniques-for-generating-artifacts"></a>Técnicas importantes para a geração de artefatos
 Nos exemplos anteriores, os modelos são usados para diversas finalidades dependentes de negócios, e a interpretação de elementos de modelagem, como classes e atividades, varia de um aplicativo para outro. As técnicas a seguir são úteis quando você gera artefatos de modelos.

- **Perfis**. Mesmo dentro de uma área de negócios, a interpretação de um tipo de elemento pode variar. Por exemplo, em um diagrama de site da Web, algumas classes podem representar páginas da Web e outras representam blocos de conteúdo. Para facilitar que os usuários registrem essas distinções, defina os estereótipos. Estereótipos também possibilitam anexar propriedades adicionais que se aplicam a elementos desse tipo. Os estereótipos são empacotados dentro de perfis. Para obter mais informações, consulte [definir um perfil para estender o UML](../modeling/define-a-profile-to-extend-uml.md).

     No código de modelo, é fácil acessar os estereótipos que são definidos em um objeto. Por exemplo:

    ```
    public bool HasStereotype(IClass c, string profile, string stereo)
    { return c.AppliedStereotypes.Any
       (s => s.Profile == profile && s.Name == stereo ); }
    ```

- **Modelos restritos**. Nem todos os modelos que você pode criar são válidos para cada finalidade. Por exemplo, nos modelos de bagagem do aeroporto da Fabrikam, seria incorreto ter uma mesa de check-in sem um transportador de saída. Você pode definir funções de validação que ajudam os usuários a observar essas restrições. Para obter mais informações, consulte [definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).

- **Preserve alterações manuais**. Somente alguns dos arquivos de solução podem ser gerados a partir de um modelo. Na maioria dos casos, você precisa ser capaz de adicionar ou ajustar o conteúdo gerado manualmente. No entanto, é importante que essas alterações manuais sejam preservadas quando a transformação do modelo for executada novamente.

     Onde os modelos geram código em idiomas [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)], eles devem gerar classes parciais para que os desenvolvedores possam adicionar métodos e código. Também é útil gerar cada classe como um par: uma classe base abstrata que contém os métodos e uma classe herdeira que contém apenas o construtor. Isso permite que os desenvolvedores substituam os métodos. Para permitir que a inicialização seja substituída, ela é feita em um método separado, em vez de nos construtores.

     Quando um modelo gera XML e outros tipos de saída, pode ser mais difícil manter o conteúdo manual separado do conteúdo gerado. Um método é criar uma tarefa no processo de compilação que combina dois arquivos. Outro método é para os desenvolvedores ajustarem uma cópia local do modelo de geração.

- **Mova o código para assemblies separados**. Não recomendamos escrever grandes corpos de código em modelos. É preferível manter o conteúdo gerado separado da computação e os modelos de texto não têm suporte para edição de código.

     Em vez disso, se você precisar executar computações substanciais para gerar texto, crie essas funções em um assembly separado e chame seus métodos do modelo.
