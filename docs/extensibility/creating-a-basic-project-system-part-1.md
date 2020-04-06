---
title: Criando um sistema básico de projetos, parte 1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739728"
---
# <a name="create-a-basic-project-system-part-1"></a>Crie um sistema básico de projeto, parte 1
No Visual Studio, os projetos são os contêineres que os desenvolvedores usam para organizar arquivos de código-fonte e outros ativos. Projetos aparecem como filhos de soluções no **Solution Explorer**. Os projetos permitem que você organize, crie, depura e implante código-fonte e crie referências a serviços web, bancos de dados e outros recursos.

 Os projetos são definidos em arquivos de projeto, por exemplo, um arquivo *.csproj* para um projeto Visual C#. Você pode criar seu próprio tipo de projeto que tenha sua própria extensão de nome de arquivo de projeto. Para obter mais informações sobre os tipos de projetos, consulte [os tipos de projeto](../extensibility/internals/project-types.md).

> [!NOTE]
> Se você precisar estender o Visual Studio com um tipo de projeto personalizado, recomendamos fortemente aproveitar o sistema de [projetos Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS), que tem uma série de vantagens sobre a construção de um sistema de projeto do zero:
>
> - Mais fácil de embarcar.  Mesmo um sistema básico de projeto requer dezenas de milhares de linhas de código.  O uso do VSPS reduz o custo de onboarding a alguns cliques antes de estar pronto para personalizá-lo às suas necessidades.
> - Manutenção mais fácil.  Ao aproveitar o VSPS, você só precisa manter seus próprios cenários.  Nós lidamos com a manutenção de toda a infra-estrutura do sistema de projetos.
>
>   Se você precisar segmentar versões do Visual Studio mais antigas que o Visual Studio 2013, você não será capaz de aproveitar o VSPS em uma extensão do Visual Studio.  Se esse for o caso, este passo a passo é um bom lugar para começar.

 Este passo a passo mostra como criar um tipo de projeto que tenha a extensão do nome do arquivo do projeto *.myproj*. Este passo a passo é emprestado do sistema de projeto Visual C# existente.

> [!NOTE]
> Para obter mais exemplos de projetos de extensão, consulte [amostras VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 Este passo a passo ensina como realizar essas tarefas:

- Crie um tipo básico de projeto.

- Crie um modelo básico de projeto.

- Registre o modelo do projeto no Visual Studio.

- Crie uma instância de projeto abrindo a caixa de diálogo **Novo Projeto** e, em seguida, usando seu modelo.

- Crie uma fábrica de projetos para o seu sistema de projetos.

- Crie um nó de projeto para o seu sistema de projeto.

- Adicione ícones personalizados para o sistema de projeto.

- Implementar a substituição do parâmetro de modelo básico.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

 Você também deve baixar o código-fonte do [Managed Package Framework para projetos](https://github.com/tunnelvisionlabs/MPFProj10). Extrair o arquivo para um local acessível à solução que você vai criar.

## <a name="create-a-basic-project-type"></a>Crie um tipo básico de projeto
 Crie um projeto C# VSIX chamado **SimpleProject**. (**Arquivo** > **Novo** > **Projeto** e, em **seguida, Visual C#** > **Extensibility** > **VSIX Project**). Adicione um modelo de item do projeto Visual Studio Package (no **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e selecione **Adicionar** > **novo item,** depois vá para **Extensibility** > **Visual Studio Package**). Nomeie o arquivo *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Criando um modelo básico de projeto
 Agora, você pode modificar este VSPackage básico para implementar o novo tipo de projeto *.myproj.* Para criar um projeto baseado no tipo de projeto *.myproj,* o Visual Studio precisa saber quais arquivos, recursos e referências para adicionar ao novo projeto. Para fornecer essas informações, coloque arquivos de projeto em uma pasta de modelo de projeto. Quando um usuário usa o projeto *.myproj* para criar um projeto, os arquivos são copiados para o novo projeto.

### <a name="to-create-a-basic-project-template"></a>Para criar um modelo básico de projeto

1. Adicione três pastas ao projeto, uma sob a outra: *Templates\Projects\SimpleProject*. (No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto **SimpleProject,** aponte para **Adicionar**e clique em **Nova pasta**. Nomeie os *modelos da*pasta . Na pasta *Modelos,* adicione uma pasta chamada *Projetos*. Na pasta *Projetos,* adicione uma pasta chamada *SimpleProject*.)

2. Na pasta *Templates\Projects\SimpleProject,* adicione um arquivo Bitmap Image para usar como o ícone chamado *SimpleProject.ico*. Quando você **clica em Adicionar,** o editor de ícones é aberto.

3. Faça o ícone distinto. Este ícone aparecerá na caixa de diálogo **Projeto Novo** mais tarde no passo a passo.

    ![Ícone de projeto simples](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Salve o ícone e feche o editor de ícones.

5. Na pasta *Templates\Projects\SimpleProject,* adicione um item **de classe** chamado *Program.cs*.

6. Substitua o código existente pelas seguintes linhas.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > Esta não é a forma final do código *Program.cs;* os parâmetros de substituição serão tratados em uma etapa posterior. Você pode ver erros de compilação, mas enquanto o **BuildAction** do arquivo for **Conteúdo,** você deve ser capaz de construir e executar o projeto como de costume.

7. Salve o arquivo.

8. Copie o arquivo *AssemblyInfo.cs* da pasta *Propriedades* para a pasta *Projetos\SimpleProject.*

9. Na pasta *Projects\SimpleProject* adicione um arquivo XML chamado *SimpleProject.myproj*.

   > [!NOTE]
   > A extensão do nome do arquivo para todos os projetos deste tipo é *.myproj*. Se você quiser mudá-lo, você deve mudá-lo em todos os lugares que é mencionado no passo a passo.

10. Substitua o conteúdo existente pelas seguintes linhas.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. Salve o arquivo.

12. Na janela **Propriedades,** defina a Ação de **Construção** de *AssemblyInfo.cs,* *Program.cs*, *SimpleProject.ico*e *SimpleProject.myproj* para **Conteúdo**e defina suas propriedades **Include in VSIX** como **True**.

    Este modelo de projeto descreve um projeto Visual C# básico que tem uma configuração de Depuração e uma configuração de Versão. O projeto inclui dois arquivos de origem, *AssemblyInfo.cs* e *Program.cs,* e várias referências de montagem. Quando um projeto é criado a partir do modelo, o valor ProjectGuid é automaticamente substituído por um novo GUID.

    No **Solution Explorer,** a pasta **Modelos** expandido deve aparecer da seguinte forma:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Criar uma fábrica básica de projetos
 Você deve informar ao Visual Studio a localização da sua pasta de modelo de projeto. Para fazer isso, adicione um atributo à classe VSPackage que implementa a fábrica do projeto para que a localização do modelo seja escrita no registro do sistema quando o VSPackage for construído. Comece criando uma fábrica de projetos básicos que é identificada por uma fábrica de projetos GUID. Use <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> o atributo para conectar `SimpleProjectPackage` a fábrica do projeto à classe.

### <a name="to-create-a-basic-project-factory"></a>Para criar uma fábrica básica de projetos

1. Crie GUIDs para sua fábrica de projetos (no menu **Ferramentas,** clique em **Criar GUID),** ou use o do exemplo a seguir. Adicione os GUIDs `SimpleProjectPackage` à classe perto da `PackageGuidString`seção com o já definido . Os GUIDs devem estar tanto na forma GUID quanto na forma de corda. O código resultante deve se assemelhar ao seguinte exemplo.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Adicione uma classe à pasta *top SimpleProject* chamada *SimpleProjectFactory.cs*.

3. Adicione o seguinte usando as orientações:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Adicione um atributo `SimpleProjectFactory` GUID à classe. O valor do atributo é o novo projeto de fábrica GUID.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Agora você pode registrar seu modelo de projeto.

### <a name="to-register-the-project-template"></a>Para registrar o modelo do projeto

1. Em *SimpleProjectPackage.cs,* <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> adicione um `SimpleProjectPackage` atributo à classe, da seguinte forma.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Reconstrua a solução e verifique se ela é construída sem erros.

    A reconstrução registra o modelo do projeto.

   Os `defaultProjectExtension` parâmetros e `possibleProjectExtensions` são definidos para a extensão do nome do arquivo do projeto (*.myproj*). O `projectTemplatesDirectory` parâmetro é definido para o caminho relativo da pasta *Templates.* Durante a construção, esse caminho será convertido em uma construção completa e adicionado ao registro para cadastrar o sistema do projeto.

## <a name="test-the-template-registration"></a>Teste o registro do modelo
 O registro do modelo informa ao Visual Studio a localização da pasta de modelo de projeto para que o Visual Studio possa exibir o nome e o ícone do modelo na caixa de diálogo **Novo Projeto.**

### <a name="to-test-the-template-registration"></a>Para testar o registro do modelo

1. Pressione **F5** para começar a depurar uma instância experimental do Visual Studio.

2. Na instância experimental, crie um novo projeto do seu tipo de projeto recém-criado. Na caixa de diálogo **Novo Projeto,** você deve ver **SimpleProject** em **Modelos instalados**.

   Agora você tem uma fábrica de projetos que está registrada. No entanto, ainda não é possível criar um projeto. O pacote de projetos e a fábrica de projetos trabalham juntos para criar e inicializar um projeto.

## <a name="add-the-managed-package-framework-code"></a>Adicionar o código framework do pacote gerenciado
 Implementar a conexão entre o pacote do projeto e a fábrica do projeto.

- Importe os arquivos de código-fonte para o Quadro de pacotes gerenciados.

    1. Descarregue o projeto SimpleProject (no **Solution Explorer,** selecione o nó do projeto e no menu de contexto clique em **Descarregar Projeto**.) e abra o arquivo do projeto no editor XML.

    2. Adicione os seguintes blocos ao \<arquivo do projeto (logo acima dos blocos de> de importação). Defina `ProjectBasePath` para a localização do arquivo *ProjectBase.files* no código Managed Package Framework que você acabou de baixar. Você pode ter que adicionar uma barra invertida ao nome do caminho. Se você não fizer isso, o projeto pode falhar em encontrar o código-fonte do Quadro de Pacote gerenciado.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Não se esqueça da barra invertida no final do caminho.

    3. Recarregue o projeto.

    4. Adicione referências aos assemblies a seguir:

        - `Microsoft.VisualStudio.Designer.Interfaces`(em * \<VSSDK instalar>\VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Para inicializar a fábrica de projetos

1. No arquivo *SimpleProjectPackage.cs,* adicione `using` a seguinte diretiva.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Derivar `SimpleProjectPackage` a `Microsoft.VisualStudio.Package.ProjectPackage`classe de .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registre a fábrica do projeto. Adicione a seguinte `SimpleProjectPackage.Initialize` linha ao `base.Initialize`método, logo após .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementar a `ProductUserContext`propriedade abstrata:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. Em *SimpleProjectFactory.cs,* adicione `using` a seguinte `using` diretiva após as diretrizes existentes.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Derivar `SimpleProjectFactory` a `ProjectFactory`classe de .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Adicione o seguinte método de `SimpleProjectFactory` boneco à classe. Você implementará este método em uma seção posterior.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Adicione o seguinte campo e `SimpleProjectFactory` construtor à classe. Esta `SimpleProjectPackage` referência é armazenada em cache em um campo privado para que possa ser usada na definição de um site do provedor de serviços.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Reconstrua a solução e verifique se ela é construída sem erros.

## <a name="test-the-project-factory-implementation"></a>Teste a implementação da fábrica do projeto
 Teste se o construtor para a implementação da fábrica do projeto é chamado.

### <a name="to-test-the-project-factory-implementation"></a>Para testar a implementação da fábrica do projeto

1. No *arquivo SimpleProjectFactory.cs,* defina um ponto de `SimpleProjectFactory` ruptura na seguinte linha no construtor.

    ```csharp
    this.package = package;
    ```

2. Pressione **F5** para iniciar uma instância experimental do Visual Studio.

3. Na instância experimental, comece a criar um novo projeto. Na caixa de diálogo **Novo projeto,** selecione o tipo de projeto **SimpleProject** e clique em **OK**. A execução pára no ponto de ruptura.

4. Limpe o ponto de ruptura e pare de depurar. Como ainda não criamos um nó de projeto, o código de criação de projetos ainda abre exceções.

## <a name="extend-the-projectnode-class"></a>Estender a classe ProjectNode
 Agora você pode `SimpleProjectNode` implementar a classe, `ProjectNode` que deriva da classe. A `ProjectNode` classe base lida com as seguintes tarefas de criação de projetos:

- Copia o arquivo de modelo do projeto, *SimpleProject.myproj*, para a nova pasta do projeto. A cópia é renomeada de acordo com o nome inserido na caixa de diálogo **Projeto Novo.** O `ProjectGuid` valor da propriedade é substituído por um novo GUID.

- Atravessa os elementos do MSBuild do arquivo de modelo do `Compile` projeto, *SimpleProject.myproj*, e procura elementos. Para `Compile` cada arquivo de destino, copia o arquivo para a nova pasta do projeto.

  A classe `SimpleProjectNode` derivada lida com essas tarefas:

- Habilita que ícones para nós de projeto e arquivo no **Solution Explorer** sejam criados ou selecionados.

- Permite que substituições adicionais de parâmetros de modelo de projeto sejam especificadas.

### <a name="to-extend-the-projectnode-class"></a>Para estender a classe ProjectNode

1. Adicione uma classe chamada `SimpleProjectNode.cs`.

2. Substitua o código existente pelo código a seguir.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   Esta `SimpleProjectNode` implementação de classe tem esses métodos substituídos:

- `ProjectGuid`, que retorna a fábrica de projetos GUID.

- `ProjectType`, que retorna o nome localizado do tipo de projeto.

- `AddFileFromTemplate`, que copia arquivos selecionados da pasta de modelo para o projeto de destino. Este método é ainda implementado em uma seção posterior.

  O `SimpleProjectNode` construtor, como `SimpleProjectFactory` o construtor, `SimpleProjectPackage` armazena uma referência em um campo privado para uso posterior.

  Para conectar `SimpleProjectFactory` a `SimpleProjectNode` classe à classe, você `SimpleProjectNode` deve `SimpleProjectFactory.CreateProject` instanciar um novo no método e cache-lo em um campo privado para uso posterior.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Para conectar a classe de fábrica do projeto e a classe de nó

1. No arquivo *SimpleProjectFactory.cs,* adicione `using` a seguinte diretiva:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Substitua `SimpleProjectFactory.CreateProject` o método usando o seguinte código.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Reconstrua a solução e verifique se ela é construída sem erros.

## <a name="test-the-projectnode-class"></a>Teste a classe ProjectNode
 Teste sua fábrica de projetos para ver se ele cria uma hierarquia de projeto.

### <a name="to-test-the-projectnode-class"></a>Para testar a classe ProjectNode

1. Pressione **F5** para iniciar a depuração. Na instância experimental, crie um novo SimpleProject.

2. O Visual Studio deve ligar para sua fábrica de projetos para criar um projeto.

3. Feche a instância experimental do Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Adicione um ícone de nó de projeto personalizado
 O ícone do nó de projeto na seção anterior é um ícone padrão. Você pode alterá-lo para um ícone personalizado.

### <a name="to-add-a-custom-project-node-icon"></a>Para adicionar um ícone de nó de projeto personalizado

1. Na pasta **Recursos,** adicione um arquivo bitmap chamado *SimpleProjectNode.bmp*.

2. Nas **janelas Propriedades,** reduza o bitmap para 16 por 16 pixels. Faça o bitmap distinto.

    ![Simples Projeto Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. Na janela **Propriedades,** **altere a ação 'Criar'** do bitmap para **Recurso Incorporado**.

4. Em *SimpleProjectNode.cs,* adicione `using` as seguintes diretivas:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Adicione o seguinte campo estático `SimpleProjectNode` e construtor à classe.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Adicione a seguinte propriedade ao `SimpleProjectNode` início da aula.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Substitua o construtor de instâncias pelo seguinte código.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   Durante a `SimpleProjectNode` construção estática, recupera o bitmap do nó do projeto dos recursos do manifesto de montagem e armazena-o em um campo privado para uso posterior. Observe a sintaxe do caminho da <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> imagem. Para ver os nomes dos recursos manifestos <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> incorporados em uma montagem, use o método. Quando este método é `SimpleProject` aplicado à montagem, os resultados devem ser os seguintes:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Recursos.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Durante a construção `ProjectNode` de instâncias, a classe base carrega *Resources.imagelis.bmp*, no qual são incorporados comumente usados 16 x 16 bitmaps de *Resources\imagelis.bmp*. Esta lista de bitmap `SimpleProjectNode` `ImageHandler.ImageList`si fica disponível para como . `SimpleProjectNode`anexa o bitmap do nó do projeto à lista. A compensação do bitmap do nó do projeto na lista de imagens é armazenada em cache para uso posterior como o valor da propriedade pública. `ImageIndex` O Visual Studio usa essa propriedade para determinar qual bitmap exibir como ícone do nó do projeto.

## <a name="test-the-custom-project-node-icon"></a>Teste o ícone de nó de projeto personalizado
 Teste sua fábrica de projetos para ver se ele cria uma hierarquia de projeto que tenha seu ícone de nó de projeto personalizado.

### <a name="to-test-the-custom-project-node-icon"></a>Para testar o ícone de nó de projeto personalizado

1. Comece a depurar e, na instância experimental, crie um novo SimpleProject.

2. No projeto recém-criado, observe que *SimpleProjectNode.bmp* é usado como ícone do nó do projeto.

     ![Nó de projeto simples do novo projeto](../extensibility/media/simpleprojnewprojectnode.png "SimplesProjNewProjectNode")

3. Abra *Program.cs* no editor de códigos. Você deve ver o código fonte que se assemelha ao seguinte código.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     Observe que os parâmetros do modelo $nameSpace$ e $className$ não possuem novos valores. Você aprenderá como implementar a substituição do parâmetro do modelo na próxima seção.

## <a name="substitute-template-parameters"></a>Parâmetros de modelo substituto
 Em uma seção anterior, você registrou o modelo `ProvideProjectFactory` de projeto no Visual Studio usando o atributo. Registrar o caminho de uma pasta de modelo desta maneira permite que você habilite a substituição de parâmetros básicos do modelo, substituindo e expandindo a `ProjectNode.AddFileFromTemplate` classe. Para obter mais informações, consulte [Nova geração de projetos: Sob o capô, parte dois](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Agora adicione código `AddFileFromTemplate` de substituição à classe.

### <a name="to-substitute-template-parameters"></a>Para substituir parâmetros de modelo

1. No arquivo *SimpleProjectNode.cs,* adicione `using` a seguinte diretiva.

   ```csharp
   using System.IO;
   ```

2. Substitua `AddFileFromTemplate` o método usando o seguinte código.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. Defina um ponto de ruptura `className` no método, logo após a declaração de atribuição.

   As instruções de atribuição determinam valores razoáveis para um namespace e um novo nome de classe. As `ProjectNode.FileTemplateProcessor.AddReplace` duas chamadas do método substituem os valores correspondentes do parâmetro do modelo usando esses novos valores.

## <a name="test-the-template-parameter-substitution"></a>Teste a substituição do parâmetro do modelo
 Agora você pode testar a substituição do parâmetro do modelo.

### <a name="to-test-the-template-parameter-substitution"></a>Para testar a substituição do parâmetro do modelo

1. Comece a depurar e, na instância experimental, crie um novo SimpleProject.

2. A execução pára no `AddFileFromTemplate` ponto de ruptura do método.

3. Examine os valores para os `nameSpace` parâmetros. `className`

   - `nameSpace`é dado o \<valor do elemento RootNamespace> no *\Templates\Projects\SimpleProject\SimpleProject.myproj* project template file. Neste caso, o `MyRootNamespace`valor é .

   - `className`é dado o valor do nome do arquivo de origem da classe, sem a extensão do nome do arquivo. Neste caso, o primeiro arquivo a ser copiado para a pasta de destino é *AssemblyInfo.cs;* portanto, o valor do `AssemblyInfo`className é .

4. Remova o ponto de ruptura e pressione **F5** para continuar a execução.

    O Visual Studio deve terminar de criar um projeto.

5. Abra *Program.cs* no editor de códigos. Você deve ver o código fonte que se assemelha ao seguinte código.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    Observe que o namespace é agora `MyRootNamespace` `Program`e o nome da classe é agora .

6. Comece a depuração do projeto. O novo projeto deve compilar, executar e exibir "Hello VSX!!!" na janela do console.

    ![Comando de Projeto Simples](../extensibility/media/simpleprojcommand.png "Comando SimpleProj")

   Parabéns! Você implementou um sistema básico de projeto gerenciado.
