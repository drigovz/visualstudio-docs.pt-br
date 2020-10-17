---
title: Criar um arquivo de projeto do MSBuild do zero
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35b05410c1a9ac36273a43481929a3be463d8af1
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136687"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Passo a passo: Criar um arquivo de projeto do MSBuild do zero

As linguagens de programação que tenham como destino o .NET Framework usam arquivos de projetos do MSBuild para descrever e controlar o processo de compilação de aplicativos. Quando você usa o Visual Studio para criar um arquivo de projeto do MSBuild, o XML apropriado é adicionado ao arquivo automaticamente. Entretanto, talvez você ache útil compreender como o XML é organizado e como é possível alterá-lo para controlar uma compilação.

 Para obter informações sobre como criar um arquivo de projeto para um projeto C++, consulte [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Este passo a passo mostra como criar um arquivo de projeto básico de forma incremental, usando somente um editor de texto. Este passo a passo possui as seguintes etapas:

1. Estenda a variável de ambiente PATH.

2. Criar um arquivo de origem de aplicativo mínimo.

3. Criar um arquivo de projeto MSBuild mínimo.

4. Compilar o aplicativo usando o arquivo de projeto.

5. Adicionar propriedades para controlar a compilação.

6. Controlar a compilação alterando os valores de propriedade.

7. Adicionar destinos à compilação.

8. Controlar a compilação especificando destinos.

9. Compilar de forma incremental.

Este passo a passo mostra como compilar o projeto no prompt de comando e como examinar os resultados. Para saber mais sobre o MSBuild e como executá-lo no prompt de comandos, confira [Passo a passo: Usar o MSBuild](../msbuild/walkthrough-using-msbuild.md).

Para concluir o passo a passos, você deve ter o Visual Studio instalado porque ele inclui o MSBuild e o compilador do Visual C#, que são necessários para o passo a passos.

## <a name="extend-the-path"></a>Estender o caminho

Para poder usar o MSBuild, você deve estender a variável de ambiente PATH para incluir todas as ferramentas necessárias. Você pode usar o **prompt de comando do desenvolvedor para o Visual Studio**. Pesquise por ele no Windows 10 na caixa de pesquisa na barra de tarefas do Windows. Para configurar o ambiente em um prompt de comando comum ou em um ambiente de script, execute *VSDevCmd.bat* na subpasta *Common7/Tools* de uma instalação do Visual Studio.

## <a name="create-a-minimal-application"></a>Criar um aplicativo mínimo

 Esta seção mostra como criar um arquivo de origem do aplicativo C# mínimo usando um editor de texto.

1. No prompt de comando, navegue até a pasta na qual você deseja criar o aplicativo, por exemplo, *\Meus documentos \\ * ou *\Desktop \\ *.

2. Digite **MD HelloWorld** para criar uma subpasta *chamada \\ \HelloWorld*.

3. Digite **cd HelloWorld** para mudar para a nova pasta.

4. Inicie o Bloco de Notas ou outro editor de texto e digite o código a seguir.

    ```csharp
    using System;

    class HelloWorld
    {
        static void Main()
        {
    #if DebugConfig
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");
    #endif

            Console.WriteLine("Hello, world!");
        }
    }
    ```

5. Salve esse arquivo de código-fonte e nomeie-o *HelloWorld.cs*.

6. Compile o aplicativo digitando **csc helloworld.cs** no prompt de comando.

7. Teste o aplicativo digitando **helloworld** no prompt de comando.

     A mensagem **Hello, world!** deve ser exibida.

8. Exclua o aplicativo digitando **del helloworld.exe** no prompt de comando.

## <a name="create-a-minimal-msbuild-project-file"></a>Criar um arquivo de projeto MSBuild mínimo

 Agora que você possui um arquivo de origem de aplicativo mínimo, poderá criar um arquivo de projeto mínimo para compilar o aplicativo. Esse arquivo de projeto contém os seguintes elementos:

- O nó raiz `Project` necessário.

- Um nó `ItemGroup` para conter elementos do item.

- Um elemento do item que se refere ao arquivo de origem do aplicativo.

- Um nó `Target` para conter tarefas que são necessárias para compilar o aplicativo.

- Um elemento `Task` para iniciar o compilador do Visual C# para compilar o aplicativo.

### <a name="to-create-a-minimal-msbuild-project-file"></a>Para criar um arquivo de projeto MSBuild mínimo

1. No editor de texto, substitua o texto existente usando estas duas linhas:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Insira este nó `ItemGroup` como um elemento filho do nó `Project`:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Observe que este `ItemGroup` já contém um elemento do item.

3. Adicione um nó `Target` como um elemento filho do nó `Project`. Nomeie o nó `Build`.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Insira este elemento da tarefa como um elemento filho do nó `Target`:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Salve esse arquivo de projeto e nomeie-o *HelloWorld. csproj*.

O seu arquivo de projeto mínimo deve se assemelhar ao seguinte código:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

As tarefas no destino Compilar são executadas em sequência. Nesse caso, a tarefa `Csc` do compilador do Visual C# é a única tarefa. Ela espera que uma lista de arquivos de origem seja compilada e isso ocorre pelo valor do item `Compile`. O `Compile` Item faz referência a apenas um arquivo de origem, *HelloWorld.cs*.

> [!NOTE]
> No elemento item, você pode usar o caractere curinga asterisco ( \* ) para fazer referência a todos os arquivos que têm a extensão de nome de arquivo *. cs* , da seguinte maneira:
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="build-the-application"></a>Compilar o aplicativo

 Agora, para compilar o aplicativo, use o arquivo de projeto recém-criado.

1. No prompt de comando, digite **MSBuild HelloWorld. csproj-t:Build**.

     Ele compila o destino Compilar do arquivo de projeto Helloworld chamando o compilador do Visual C# para criar o aplicativo Helloworld.

2. Teste o aplicativo digitando **helloworld**.

     A mensagem **Hello, world!** deve ser exibida.

> [!NOTE]
> Você pode ver mais detalhes sobre a compilação aumentando o nível de detalhamento. Para configurar o nível de detalhamento como "detalhado", digite este comando no prompt de comando:
>
> **MSBuild HelloWorld. csproj-t:Build-detalhes: detalhado**

## <a name="add-build-properties"></a>Adicionar propriedades de compilação

 Você pode adicionar propriedades de compilação ao arquivo de projeto para controlar ainda mais a compilação. Agora, adicione estas propriedades:

- Uma propriedade `AssemblyName` para especificar o nome do aplicativo.

- Uma propriedade `OutputPath` para especificar uma pasta para conter o aplicativo.

### <a name="to-add-build-properties"></a>Para adicionar propriedades de compilação

1. Exclua o aplicativo existente digitando **del helloworld.exe** no prompt de comando.

2. No arquivo de projeto, insira este elemento `PropertyGroup` imediatamente depois de abrir o elemento `Project`:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Adicione esta tarefa no destino Compilar, imediatamente antes da tarefa `Csc`:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     A tarefa `MakeDir` cria uma pasta que é chamada pela propriedade `OutputPath`, contanto que não exista atualmente nenhuma pasta com esse nome.

4. Adicione esse atributo `OutputAssembly` à tarefa `Csc`:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     Isso instrui o compilador do Visual C# a produzir um assembly que é chamado pela propriedade `AssemblyName` e para colocá-lo na pasta que é chamada pela propriedade `OutputPath`.

5. Salve suas alterações.

O seu arquivo de projeto deve agora se assemelhar ao seguinte código:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
> Recomendamos que você adicione um delimitador de caminho de barra invertida (\\) no final do nome da pasta ao especificá-lo no elemento `OutputPath`, em vez de adicioná-lo ao atributo `OutputAssembly` da tarefa `Csc`. Portanto,
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly="$(OutputPath)$(AssemblyName).exe" />`
>
> é melhor que
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Testar as propriedades de compilação

 Agora, você pode compilar o aplicativo usando o arquivo de projeto no qual usou as propriedades de compilação para especificar a pasta de saída e o nome do aplicativo.

1. No prompt de comando, digite **MSBuild HelloWorld. csproj-t:Build**.

     Isso cria a *pasta \\ \Bin* e, em seguida, invoca o compilador Visual C# para criar o aplicativo *MSBuildSample* e o coloca na pasta *\Bin \\ * .

2. Para verificar se a *pasta \\ \Bin* foi criada e se ela contém o aplicativo *MSBuildSample* , digite **dir Bin**.

3. Exclua o aplicativo digitando **Bin\MSBuildSample**.

     A mensagem **Hello, world!** deve ser exibida.

## <a name="add-build-targets"></a>Adicionar destinos de compilação

 Em seguida, adicione mais dois destinos ao arquivo de projeto, como a seguir:

- Um destino Limpar que exclui arquivos antigos.

- Um destino Recompilar que usa o atributo `DependsOnTargets` para forçar a tarefa Limpar a executar a tarefa Compilar.

Agora que você tem vários destinos, poderá configurar o destino Compilar como o destino padrão.

### <a name="to-add-build-targets"></a>Para adicionar destinos de compilação

1. No arquivo de projeto, adicione esses dois destinos imediatamente após o destino Compilar:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     O destino Limpar chama a tarefa Excluir para excluir o aplicativo. O destino Recompilar não é executado até que o destino Limpar e o destino Compilar tenham sido executados. Embora o destino Recompilar não tenha tarefas, ele faz com que o destino Limpar seja executado antes do destino Compilar.

2. Adicione esse atributo `DefaultTargets` ao elemento `Project` inicial:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Isso configura o destino Compilar como o destino padrão.

O seu arquivo de projeto deve agora se assemelhar ao seguinte código:

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Clean" >
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
</Project>
```

## <a name="test-the-build-targets"></a>Testar os destinos de compilação

 Você pode experimentar os novos destinos de compilação para testar esses recursos do arquivo de projeto:

- Compilando a compilação padrão.

- Configurando o nome do aplicativo no prompt de comando.

- Excluindo o aplicativo antes de outro aplicativo ser compilado.

- Excluindo o aplicativo sem compilar outro aplicativo.

### <a name="to-test-the-build-targets"></a>Para testar os destinos de compilação

1. No prompt de comando, digite **MSBuild HelloWorld. csproj-p:AssemblyName = Greetings**.

     Como você não usou a opção **-t** para definir explicitamente o destino, o MSBuild executa o destino de compilação padrão. A opção **-p** substitui a `AssemblyName` propriedade e dá a ela o novo valor, `Greetings` . Isso faz com que um novo aplicativo, *Greetings.exe*, seja criado na *pasta \\ \Bin* .

2. Para verificar se a *pasta \\ \Bin* contém o aplicativo *MSBuildSample* e o novo aplicativo *Greetings* , digite **dir Bin**.

3. Teste o aplicativo Greetings digitando **Bin\Greetings**.

     A mensagem **Hello, world!** deve ser exibida.

4. Exclua o aplicativo MSBuildSample digitando **MSBuild HelloWorld. csproj-t:Clean**.

     Isso executa a tarefa Limpar para remover o aplicativo que tem o `AssemblyName` valor da propriedade `MSBuildSample` padrão.

5. Exclua o aplicativo Greetings digitando **MSBuild HelloWorld. csproj-t:clean-p:AssemblyName = Greetings**.

     Isso executa a tarefa Limpar para remover o aplicativo que tem o valor da propriedade especificado **AssemblyName**, `Greetings`.

6. Para verificar se a *pasta \\ \Bin* agora está vazia, digite **dir Bin**.

7. Digite **msbuild**.

     Embora um arquivo de projeto não seja especificado, o MSBuild cria o arquivo *HelloWorld. csproj* porque há apenas um arquivo de projeto na pasta atual. Isso faz com que o aplicativo *MSBuildSample* seja criado na *pasta \\ \Bin* .

     Para verificar se a *pasta \\ \Bin* contém o aplicativo *MSBuildSample* , digite **dir Bin**.

## <a name="build-incrementally"></a>Compilar de forma incremental

 Você pode informar ao MSBuild para compilar um destino somente se os arquivos de origem ou os arquivos de destino do qual dependem o destino tiverem sido alterados. O MSBuild usa o carimbo de data/hora de um arquivo para determinar se ele foi alterado.

### <a name="to-build-incrementally"></a>Para compilar de forma incremental

1. No arquivo de projeto, adicione esses atributos ao destino Compilar inicial:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Isso especifica que o destino Compilar depende dos arquivos de entrada especificados no grupo de itens `Compile` e que o destino de saída é o arquivo de aplicativo.

     O destino Compilar resultante deve se assemelhar ao seguinte código:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Teste o destino da compilação digitando **MSBuild-v:d** no prompt de comando.

     Lembre-se de que *HelloWorld. csproj* é o arquivo de projeto padrão e esse Build é o destino padrão.

     A opção **-v:d** especifica uma descrição detalhada para o processo de compilação.

     Estas linhas devem ser exibidas:

     **Ignorando o destino de "Build" porque todos os arquivos de saída estão atualizados em relação aos arquivos de entrada.**

     **Arquivos de entrada: HelloWorld.cs**

     **Arquivos de saída: BinMSBuildSample.exe**

     O MSBuild ignora o destino Compilar, pois nenhum dos arquivos de origem foi alterado desde a última compilação do aplicativo.

## <a name="c-example"></a>Exemplo de C#

O exemplo a seguir mostra um arquivo de projeto que compila um aplicativo C# e registra uma mensagem que contém o nome do arquivo de saída.

### <a name="code"></a>Código

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files of type CSFile -->
        <CSC
            Sources = "@(CSFile)"
            OutputAssembly = "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="visual-basic-example"></a>Exemplo do Visual Basic

O exemplo a seguir mostra um arquivo de projeto que compila um aplicativo Visual Basic e registra uma mensagem que contém o nome do arquivo de saída.

### <a name="code"></a>Código

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldVB</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <VBFile Include = "consolehwvb1.vb"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual Basic compilation using input files of type VBFile -->
        <VBC
            Sources = "@(VBFile)"
            OutputAssembly= "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the VBC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </VBC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="whats-next"></a>E agora?

 O Visual Studio pode fazer automaticamente muito do trabalho que é mostrado neste passo a passo. Para saber como usar o Visual Studio para criar, editar, compilar e testar arquivos de projeto MSBuild, confira [Passo a passo: Usar o MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Confira também

- [Visão geral do MSBuild](../msbuild/msbuild.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
