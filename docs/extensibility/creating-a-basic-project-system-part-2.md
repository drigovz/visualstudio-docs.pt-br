---
title: Criando um sistema básico de projetos, parte 2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739715"
---
# <a name="create-a-basic-project-system-part-2"></a>Crie um sistema básico de projeto, parte 2
O primeiro passo a passo desta série, [Criar um sistema básico de projeto, parte 1,](../extensibility/creating-a-basic-project-system-part-1.md)mostra como criar um sistema básico de projeto. Esse passo a passo se baseia no sistema básico do projeto adicionando um modelo do Visual Studio, uma página de propriedade e outros recursos. Você deve completar o primeiro passo antes de começar este.

Este passo a passo ensina como criar um tipo de projeto que tenha a extensão do nome do arquivo do projeto *.myproj*. Para completar o passo a passo, você não precisa criar seu próprio idioma porque o passo a passo é emprestado do sistema de projeto Visual C# existente.

Este passo a passo ensina como realizar essas tarefas:

- Crie um modelo do Visual Studio.

- Implante um modelo do Visual Studio.

- Crie um nó filho tipo projeto na caixa de diálogo **Projeto** Novo.

- Habilite a substituição de parâmetros no modelo do Visual Studio.

- Crie uma página de propriedade do projeto.

> [!NOTE]
> As etapas deste passo a passo são baseadas em um projeto C#. No entanto, exceto para especificidades como extensões de nome de arquivo e código, você pode usar as mesmas etapas para um projeto Visual Basic.

## <a name="create-a-visual-studio-template"></a>Crie um modelo do Visual Studio
- [Crie um sistema básico de projeto, a parte 1](../extensibility/creating-a-basic-project-system-part-1.md) mostra como criar um modelo básico de projeto e adicioná-lo ao sistema de projetos. Ele também mostra como registrar este modelo <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> no Visual Studio usando o atributo, que grava o caminho completo da pasta * \\Templates\Projects\SimpleProject\\ * no registro do sistema.

Usando um modelo do Visual Studio *(arquivo .vstemplate)* em vez de um modelo básico de projeto, você pode controlar como o modelo aparece na caixa de diálogo **Do Novo Projeto** e como os parâmetros do modelo são substituídos. Um arquivo *.vstemplate* é um arquivo XML que descreve como os arquivos de origem devem ser incluídos quando um projeto é criado usando o modelo do sistema de projeto. O próprio sistema de projeto é construído coletando o arquivo *.vstemplate* e os arquivos de origem em um arquivo *.zip,* e implantado copiando o arquivo *.zip* para um local que é conhecido pelo Visual Studio. Esse processo é explicado com mais detalhes mais tarde neste passo a passo.

1. Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra a solução SimpleProject que você criou seguindo [Criar um sistema básico de projeto, parte 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. No arquivo *SimpleProjectPackage.cs,* encontre o atributo ProvideProjectFactory. Substitua o segundo parâmetro (o nome do projeto) por nulo, e o quarto parâmetro (o caminho para a pasta de modelo de projeto) por ". \\\NullPath", da seguinte forma.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Adicionar um arquivo XML chamado *SimpleProject.vstemplate* à pasta * \\Templates\Projects\SimpleProject.\\ *

4. Substitua o conteúdo do *SimpleProject.vstemplate pelo* seguinte código.

    ```xml
    <VSTemplate Version="2.0.0" Type="Project"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
      <TemplateData>
        <Name>SimpleProject Application</Name>
        <Description>
          A project for creating a SimpleProject application
        </Description>
        <Icon>SimpleProject.ico</Icon>
        <ProjectType>SimpleProject</ProjectType>
      </TemplateData>
      <TemplateContent>
        <Project File="SimpleProject.myproj" ReplaceParameters="true">
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">
            Program.cs
          </ProjectItem>
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">
            AssemblyInfo.cs
          </ProjectItem>
        </Project>
      </TemplateContent>
    </VSTemplate>
    ```

5. Na janela **Propriedades,** selecione todos os cinco arquivos da pasta * \\Templates\Projects\SimpleProject\\ * e defina a **Ação de Compilação** para **ZipProject**.

    ![Pasta de projeto simples](../extensibility/media/simpproj2.png "SimpProj2")

    A \<seção TemplateData> determina a localização e a aparência do tipo de projeto SimpleProject na caixa de diálogo **Novo Projeto,** da seguinte forma:

- O \<elemento Name> nomeia o modelo do projeto como simplesdo project application.

- O \<elemento Descrição> contém a descrição que aparece na caixa de diálogo **Novo Projeto** quando o modelo do projeto é selecionado.

- O \<elemento Ícone> especifica o ícone que aparece junto com o tipo de projeto SimpleProject.

- O \<elemento ProjectType> nomeia o tipo Projeto na caixa de diálogo **Projeto** Novo. Este nome substitui o parâmetro nome do projeto do atributo ProvideProjectFactory.

  > [!NOTE]
  > O \<elemento ProjectType> `LanguageVsTemplate` deve `ProvideProjectFactory` corresponder ao argumento do atributo no arquivo SimpleProjectPackage.cs.

  A \<seção TemplateContent> descreve esses arquivos gerados quando um novo projeto é criado:

- *SimpleProject.myproj*

- *Module.vb*

- *AssemblyInfo.cs*

  Todos os `ReplaceParameters` três arquivos foram definidos como verdadeiros, o que permite a substituição de parâmetros. O *arquivo* `OpenInEditor` Program.cs definiu como verdadeiro, o que faz com que o arquivo seja aberto no editor de código quando um projeto é criado.

  Para obter mais informações sobre os elementos no esquema Visual Studio Template, consulte a referência do [esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Se um projeto tiver mais de um modelo do Visual Studio, cada modelo está em uma pasta separada. Cada arquivo nessa pasta deve ter a **Ação de Compilação** definida como **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Adicionando um arquivo mínimo .vsct
 O Visual Studio deve ser executado no modo de configuração para reconhecer um modelo novo ou modificado do Visual Studio. O modo de configuração requer a presença de um arquivo *.vsct.* Portanto, você deve adicionar um arquivo *mínimo .vsct* ao projeto.

1. Adicione um arquivo XML chamado *SimpleProject.vsct* ao projeto SimpleProject.

2. Substitua o conteúdo do arquivo *SimpleProject.vsct* pelo seguinte código.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Defina a ação de **compilação** deste arquivo como **VSCTCompile**. Você pode fazer isso apenas no arquivo *.csproj,* não na janela **Propriedades.** Certifique-se de que a Ação de **compilação** deste arquivo está definida como **Nenhuma** neste momento.

    1. Clique com o botão direito do mouse no nó SimpleProject e clique em **Editar SimpleProject.csproj**.

    2. No arquivo *.csproj,* localize o item *SimpleProject.vsct.*

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Altere a ação de compilação para **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. o arquivo do projeto e fechar o editor.

    5. Salve o nó SimpleProject e, em seguida, no **Solution Explorer** clique em **Recarregar projeto**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Examine as etapas de compilação do modelo do Visual Studio
 O sistema de compilação de projeto VSPackage normalmente executa o Visual Studio no modo de configuração quando o arquivo *.vstemplate* é alterado ou o projeto que contém o arquivo *.vstemplate* é reconstruído. Você pode seguir configurando o nível de verbosidade do MSBuild para Normal ou superior.

1. No menu **Ferramentas** , clique em **Opções**.

2. Expanda o nó **Projetos e Soluções** e selecione **Build and Run**.

3. Definir **verbosidade de construção de projeto MSBuild** como **normal**. Clique em **OK**.

4. Reconstrua o projeto SimpleProject.

    A etapa de compilação para criar o arquivo de projeto *.zip* deve se assemelhar ao exemplo a seguir.

```
ZipProjects:
1>  Zipping ProjectTemplates
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip
1>ZipItems:
1>  Zipping ItemTemplates
1>  SimpleProject ->
```

## <a name="deploy-a-visual-studio-template"></a>Implantar um modelo do Visual Studio
Os modelos do Visual Studio não contêm informações de caminho. Portanto, o arquivo *modelo .zip* deve ser implantado em um local conhecido pelo Visual Studio. A localização da pasta ProjectTemplates é tipicamente *<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates*.

Para implantar sua fábrica de projetos, o programa de instalação deve ter privilégios de administrador. Ele implanta modelos sob o nó de instalação do Visual Studio: *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Teste um modelo do Visual Studio
Teste sua fábrica de projetos para ver se ele cria uma hierarquia de projeto usando o modelo do Visual Studio.

1. Redefinir a instância experimental do Visual Studio SDK.

    Em [!INCLUDE[win7](../debugger/includes/win7_md.md)]: No menu **Iniciar,** encontre a pasta **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** e selecione **Redefinir a instância experimental do Microsoft Visual Studio**.

    Em versões posteriores do Windows: Na tela **Iniciar,** **digite \<Redefinir a versão do Microsoft Visual Studio> Instância Experimental**.

2. Uma janela de solicitação de comando é exibida. Quando você vir as palavras **Pressione qualquer tecla para continuar,** clique **EM ENTER**. Depois que a janela fechar, abra o Visual Studio.

3. Reconstrua o projeto SimpleProject e comece a depurar. A instância experimental aparece.

4. Na instância experimental, crie um projeto SimpleProject. Na caixa de diálogo **Novo Projeto,** selecione **SimpleProject**.

5. Você deve ver uma nova instância do SimpleProject.

    ![Nova instância do projeto simples](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Minha nova instância do projeto](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Criar um nó filho tipo projeto
Você pode adicionar um nó de criança a um nó tipo de projeto na caixa de diálogo **Projeto** Novo. Por exemplo, para o tipo de projeto SimpleProject, você pode ter nós de filho para aplicativos de console, aplicativos de janela, aplicativos web e assim por diante.

Os nós de crianças são criados alterando o arquivo do projeto e adicionando \<outputSubPath> crianças aos elementos \<zipproject>. Quando um modelo é copiado durante a compilação ou implantação, cada nó filho se torna uma subpasta da pasta de modelos de projeto.

Esta seção mostra como criar um nó de criança console para o tipo de projeto SimpleProject.

1. Renomeie os * \\modelos\Projetos\Pasta SimpleProject\\ * para * \\\\Templates\Projects\ConsoleApp*.

2. Na janela **Propriedades,** selecione todos os cinco arquivos na pasta * \\Templates\Projects\ConsoleApp\\ * e certifique-se de que a **Ação de compilação** está definida como **ZipProject**.

3. No arquivo SimpleProject.vstemplate, adicione a seguinte linha \<no final da seção TemplateData>, pouco antes da tag de fechamento.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Isso faz com que o modelo de aplicativo de console apareça tanto no nó do filho console quanto no nó pai simpleProject, que é um nível acima do nó filho.

4. Salvar o arquivo *SimpleProject.vstemplate.*

5. No arquivo *.csproj,* adicione \<OutputSubPath> a cada um dos elementos do ZipProject. Descarregue o projeto, como antes, e edite o arquivo do projeto.

6. Localize \<os elementos> do ZipProject. A \<cada elemento zipproject \<>, adicione um elemento de> OutputSubPath e dê-lhe o valor console. O Projeto Zip

    ```
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    ```

7. Adicionar \<este> do PropertyGroup ao arquivo do projeto:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Salve o arquivo do projeto e recarregue o projeto.

## <a name="test-the-project-type-child-node"></a>Teste o nó infantil tipo projeto
Teste o arquivo de projeto modificado para ver se o nó de criança **console** aparece na caixa de diálogo **Novo Projeto.**

1. Execute a **ferramenta 'Redefinir a** instância experimental do Microsoft Visual Studio'.

2. Reconstrua o projeto SimpleProject e comece a depurar. A instância experimental deve aparecer

3. Na caixa de diálogo **Projeto Novo,** clique no nó **SimpleProject.** O modelo **de aplicativo** do console deve aparecer no painel **Templates.**

4. Expanda o nó **SimpleProject.** O nó de criança **console** deve aparecer. O modelo **SimpleProject Application** continua a aparecer no painel **Templates.**

5. Clique **em Cancelar** e parar de depurar.

    ![Rollup de projeto simples](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Nó do console do projeto simples](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Parâmetros de modelo de projeto substituto
- [Criando um sistema de projeto básico,](../extensibility/creating-a-basic-project-system-part-1.md) a `ProjectNode.AddFileFromTemplate` parte 1 mostrou como substituir o método para fazer um tipo básico de substituição de parâmetrode modelo. Esta seção ensina como usar os parâmetros de modelo visual studio mais sofisticados.

Quando você cria um projeto usando um modelo do Visual Studio na caixa de diálogo **Novo Projeto,** os parâmetros do modelo são substituídos por strings para personalizar o projeto. Um parâmetro de modelo é um token especial que começa e termina com um sinal de dólar, por exemplo, $time$. Os dois parâmetros a seguir são especialmente úteis para permitir a personalização em projetos baseados no modelo:

- $GUID[1-10]$ é substituído por um novo Guid. Você pode especificar até 10 GUIDs exclusivos, por exemplo, $guid1$.

- $safeprojectname$ é o nome fornecido por um usuário na caixa de diálogo **Projeto Novo,** modificada para remover todos os caracteres e espaços inseguros.

  Para obter uma lista completa dos parâmetros de modelo, consulte [Parâmetros de modelo](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Para substituir parâmetros de modelo de projeto

1. No arquivo *SimpleProjectNode.cs,* `AddFileFromTemplate` remova o método.

2. No arquivo * \\Templates\Projects\ConsoleApp\SimpleProject.myproj,* \<localize a propriedade RootNamespace> e altere seu valor para $safeprojectname$.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. No * \\arquivo Templates\Projects\SimpleProject\Program.cs,* substitua o conteúdo do arquivo pelo seguinte código:

    ```
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace $safeprojectname$
    {
        [Guid("$guid1$")]
        public class $safeprojectname$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

4. Reconstrua o projeto SimpleProject e comece a depurar. A instância experimental deve aparecer.

5. Crie um novo aplicativo SimpleProject Console. (No **painel de tipos de projeto,** selecione **SimpleProject**. Em **modelos instalados pelo Visual Studio,** selecione **Aplicativo de console**.)

6. No projeto recém-criado, *abra Program.cs*. Ele deve se parecer com algo parecido com o seguinte (os valores GUID em seu arquivo diferem.):

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace Console_Application1
    {
        [Guid("00000000-0000-0000-00000000-00000000)"]
        public class Console_Application1
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="create-a-project-property-page"></a>Criar uma página de propriedade de projeto
Você pode criar uma página de propriedade para o seu tipo de projeto para que os usuários possam visualizar e alterar propriedades em projetos que são baseados no seu modelo. Esta seção mostra como criar uma página de propriedade independente de configuração. Esta página de propriedade básica usa uma grade de propriedades para exibir as propriedades públicas que você expõe na sua classe de página de propriedade.

Obtenha sua classe de `SettingsPage` página de propriedade da classe base. A grade de propriedades `SettingsPage` fornecida pela classe está ciente dos tipos de dados mais primitivos e sabe como exibi-los. Além disso, `SettingsPage` a classe sabe como persistir os valores de propriedade para o arquivo do projeto.

A página de propriedade criada nesta seção permite alterar e salvar essas propriedades do projeto:

- AssemblyName

- OutputType

- Rootnamespace.

1. No arquivo *SimpleProjectPackage.cs,* `ProvideObject` adicione esse `SimpleProjectPackage` atributo à classe:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Isso registra a classe `GeneralPropertyPage` de página de propriedade com COM.

2. No arquivo *SimpleProjectNode.cs,* adicione esses dois métodos `SimpleProjectNode` substituídos à classe:

    ```csharp
    protected override Guid[] GetConfigurationIndependentPropertyPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    protected override Guid[] GetPriorityProjectDesignerPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    ```

    Ambos os métodos retornam uma matriz de GUIDs de página de propriedade. O GENERALPropertyPage GUID é o único elemento na matriz, de modo que a caixa de diálogo Páginas de **propriedade** mostrará apenas uma página.

3. Adicione um arquivo de classe chamado *GeneralPropertyPage.cs* ao projeto SimpleProject.

4. Substitua o conteúdo deste arquivo usando o seguinte código:

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Project;
    using System.ComponentModel;

    namespace SimpleProject
    {
        [ComVisible(true)]
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]
        public class GeneralPropertyPage : SettingsPage
        {
            private string assemblyName;
            private OutputType outputType;
            private string defaultNamespace;

            public GeneralPropertyPage()
            {
                this.Name = "General";
            }

            [Category("AssemblyName")]
            [DisplayName("AssemblyName")]
            [Description("The output file holding assembly metadata.")]
            public string AssemblyName
            {
                get { return this.assemblyName; }
            }
            [Category("Application")]
            [DisplayName("OutputType")]
            [Description("The type of application to build.")]
            public OutputType OutputType
            {
                get { return this.outputType; }
                set { this.outputType = value; this.IsDirty = true; }
            }
            [Category("Application")]
            [DisplayName("DefaultNamespace")]
            [Description("Specifies the default namespace for added items.")]
            public string DefaultNamespace
            {
                get { return this.defaultNamespace; }
                set { this.defaultNamespace = value; this.IsDirty = true; }
            }

            protected override void BindProperties()
            {
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    A `GeneralPropertyPage` classe expõe as três propriedades públicas AssemblyName, OutputType e RootNamespace. Como o AssemblyName não tem método definido, ele é exibido como uma propriedade somente leitura. OutputType é uma constante enumerada, por isso aparece como lista de parada.

    A `SettingsPage` classe `ProjectMgr` base fornece para persistir as propriedades. O `BindProperties` método `ProjectMgr` é usa para recuperar os valores de propriedade persistidos e definir as propriedades correspondentes. O `ApplyChanges` método `ProjectMgr` usa para obter os valores das propriedades e persistiu-as para o arquivo do projeto. O método de `IsDirty` conjunto de propriedades define-se como verdadeiro para indicar que as propriedades devem ser perpersistentes. A persistência ocorre quando você salva o projeto ou a solução.

5. Reconstrua a solução SimpleProject e comece a depurar. A instância experimental deve aparecer.

6. Na instância experimental, crie um novo SimpleProject Application.

7. O Visual Studio chama sua fábrica de projetos para criar um projeto usando o modelo do Visual Studio. O novo arquivo *Program.cs* é aberto no editor de código.

8. Clique com o botão direito do mouse no nó do projeto no **Solution Explorer**e clique em **Propriedades**. A caixa de diálogo **Páginas da Propriedade** é exibida.

    ![Página de propriedade do projeto simples](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Teste a página de propriedade do projeto
Agora você pode testar se você pode modificar e alterar os valores de propriedade.

1. Na caixa de diálogo **Páginas de propriedade do MyConsoleApplication,** altere o **'''' DefaultNamespace** para **MyApplication**.

2. Selecione a propriedade **OutputType** e selecione **Biblioteca de classe**.

3. Clique em **Aplicar** e em **OK**.

4. Reabra a caixa de diálogo **Páginas** de propriedade e verifique se suas alterações foram persistidas.

5. Feche a instância experimental do Visual Studio.

6. Reabra a instância experimental.

7. Reabra a caixa de diálogo **Páginas** de propriedade e verifique se suas alterações foram persistidas.

8. Feche a instância experimental do Visual Studio.
    ![Feche a instância experimental](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
