---
title: Integração com o Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631192"
---
# <a name="visual-studio-integration-msbuild"></a>Integração com o Visual Studio (MSBuild)

O Visual Studio hospeda o MSBuild para carregar e construir projetos gerenciados. Como o MSBuild é responsável pelo projeto, quase qualquer projeto no formato MSBuild pode ser usado com sucesso no Visual Studio, mesmo que o projeto tenha sido de autoria de uma ferramenta diferente e tenha um processo de construção personalizado.

 Este artigo descreve aspectos específicos da hospedagem MSBuild do Visual Studio que devem ser considerados ao personalizar projetos e *arquivos .targets* que você deseja carregar e construir no Visual Studio. Isso ajudará você a garantir que recursos do Visual Studio, como o IntelliSense e o trabalho de depuração para o seu projeto personalizado.

 Para obter informações sobre projetos C++, consulte [arquivos do Projeto](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Extensões de nome do arquivo de projeto

 O *MSBuild.exe* reconhece extensões de nome de arquivo de projeto que correspondem ao padrão *.\*proj*. No entanto, o Visual Studio reconhece apenas um subconjunto dessas extensões de nome de arquivo de projeto, que determinam o sistema de projeto específico do idioma que carregará o projeto. O Visual Studio não possui um sistema de projeto msbuild neutro em linguagem.

 Por exemplo, o sistema de projeto C# carrega arquivos *.csproj,* mas o Visual Studio não é capaz de carregar um arquivo *.xxproj.* Um arquivo de projeto para arquivos de origem em uma linguagem arbitrária deve usar a mesma extensão que os arquivos de projeto Visual Basic ou C# a serem carregados no Visual Studio.

## <a name="well-known-target-names"></a>Nomes de destinos bem conhecidos

 Clicar no comando **Construir** no Visual Studio executará o destino padrão no projeto. Geralmente, esse destino também é denominado `Build`. Os comandos **Recompilar** ou **Limpar** farão com que ocorra uma tentativa de executar um destino de nome igual no projeto. O comando **Publicar** executará um destino nomeado como `PublishOnly` no projeto.

## <a name="configurations-and-platforms"></a>Configurações e plataformas

 As configurações são representadas em projetos MSBuild por propriedades agrupadas em um `PropertyGroup` elemento que contém um `Condition` atributo. O Visual Studio analisa essas condições para criar uma lista de configurações de projetos e plataformas a serem exibidas. Para extrair essa lista com êxito, é necessário que as condições tenham um formato semelhante ao seguinte:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 O Visual Studio analisa `PropertyGroup`as `ItemGroup` `Import`condições em elementos de propriedade e itens para este fim.

## <a name="additional-build-actions"></a>Ações de compilação adicionais

 O Visual Studio permite alterar o nome do tipo de item de um arquivo em um projeto com a propriedade **Build Action** da janela **Propriedades File.** Os nomes de tipo de item **Compile**, **EmbeddedResource**, **Content** e **None** sempre estarão listados no menu, juntamente com quaisquer outros nomes de tipo de item que já estejam no projeto. Para garantir a disponibilidade dos nomes de tipo de item personalizados nesse menu, é possível adicionar os nomes a um tipo de item de nome `AvailableItemName`. Por exemplo, adicionar o seguinte ao arquivo de projeto adicionará o tipo personalizado **JScript** a esse menu para todos os projetos que o importarem:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Alguns nomes de tipo de item são especiais para o Visual Studio, mas não estão listados neste dropdown.

## <a name="in-process-compilers"></a>Compiladores em processo

 Quando possível, o Visual Studio tentará usar a versão em processo do compilador Visual Basic para aumentar o desempenho. (Não aplicável a C#.) Para que isso funcione corretamente, as seguintes condições devem ser atendidas:

- Em um alvo do projeto, deve `Vbc` haver uma tarefa nomeada para projetos Visual Basic.

- O parâmetro `UseHostCompilerIfAvailable` da tarefa deve ser definido como true.

## <a name="design-time-intellisense"></a>IntelliSense do Tempo de Design

 Para obter suporte ao IntelliSense no Visual Studio antes que uma compilação tenha gerado um conjunto de saídas, as seguintes condições devem ser atendidas:

- Deve haver um destino com o nome `Compile`.

- É necessário que o destino `Compile` ou uma de suas dependências chame a tarefa do compilador do projeto, como `Csc` ou `Vbc`.

- O destino `Compile` ou uma de suas dependências deve fazer com que o compilador receba todos os parâmetros necessários para o IntelliSense, em particular, todas as referências.

- As condições listadas na seção [Compiladores em processo](#in-process-compilers) devem ser cumpridas.

## <a name="build-solutions"></a>Compilar soluções

 Dentro do Visual Studio, o arquivo de solução e o pedido de construção de projetos são controlados pelo próprio Visual Studio. Ao construir uma solução com *msbuild.exe* na linha de comando, o MSBuild analisa o arquivo de solução e ordena a construção do projeto. Em ambos os casos, os projetos são compilados individualmente em ordem de dependência e as referências projeto a projeto não são percorridas. Por outro lado, quando projetos individuais são compilados com o *msbuild.exe*, as referências projeto a projeto são percorridas.

 Ao construir dentro do `$(BuildingInsideVisualStudio)` Visual Studio, a propriedade é definida como `true`. Isso pode ser usado no projeto ou em arquivos *.targets* para fazer com que o build se comporte de maneira diferente.

## <a name="display-properties-and-items"></a>Exibir propriedades e itens

 Visual Studio reconhece certos nomes e valores de propriedade. Por exemplo, a seguinte propriedade de um projeto fará com que **Aplicativos do Windows** apareçam na caixa **Tipo de Aplicativo** no **Designer de Projeto**.

```xml
<OutputType>WinExe</OutputType>
```

 O valor da propriedade pode ser editado no **Designer de Projeto** e salvo no arquivo de projeto. Se tal propriedade receber um valor inválido por edição manual, o Visual Studio mostrará um aviso quando o projeto estiver carregado e substituirá o valor inválido por um valor padrão.

 Visual Studio entende padrões para algumas propriedades. Essas propriedades não serão mantidas no arquivo de projeto, a menos que eles tenham valores não padrão.

 Propriedades com nomes arbitrários não são exibidas no Visual Studio. Para modificar propriedades arbitrárias no Visual Studio, você deve abrir o arquivo do projeto no editor XML e editá-los manualmente. Para saber mais, confira a seção [Editar arquivos de projeto no Visual Studio](#edit-project-files-in-visual-studio) mais adiante neste tópico.

 Os itens definidos no projeto com nomes de tipo de item arbitrários são exibidos por padrão no **Gerenciador de Soluções**, em seus respectivos nós de projeto. Para ocultar um item da exibição, defina os metadados `Visible` como `false`. Por exemplo, o item a seguir participará do processo de build, mas não será exibido no **Gerenciador de Soluções**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Os `Visible` metadados são ignorados pelo **Solution Explorer** para projetos C++. Os itens serão sempre mostrados, mesmo que `Visible` seja definido como falso.

 Os itens declarados em arquivos importados para o projeto não serão exibidos por padrão. Os itens criados durante o processo de build nunca serão exibidos no **Gerenciador de Soluções**.

## <a name="conditions-on-items-and-properties"></a>Condições em itens e propriedades

 Durante o build, todas as condições serão plenamente respeitadas.

 Ao determinar os valores de propriedade a serem exibidos, as propriedades que o Visual Studio considera dependentes de configuração são avaliadas de forma diferente das propriedades que considera independentes da configuração. Para propriedades que considera a configuração dependente, o Visual Studio define as `Configuration` propriedades e `Platform` as propriedades adequadamente e instrui o MSBuild a reavaliar o projeto. Para as propriedades consideradas independentes da configuração, não é possível determinar como as condições serão avaliadas.

 As expressões condicionais de itens sempre serão ignoradas com a finalidade de decidir se o item deve ser exibido no **Gerenciador de Soluções**.

## <a name="debugging"></a>Depuração

 Para encontrar e iniciar o conjunto de saída e anexar o `OutputPath` `AssemblyName`depurador, o Visual Studio precisa das propriedades e `OutputType` definidas corretamente. Não será possível anexar o depurador se o processo de build não fizer com que o compilador gere um arquivo *.pdb*.

## <a name="design-time-target-execution"></a>Execução de destino do tempo de design

 O Visual Studio tenta executar alvos com certos nomes quando carrega um projeto. Esses destinos incluem `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` e `CopyRunEnvironmentFiles`. O Visual Studio executa esses alvos para que o compilador possa ser inicializado para fornecer o IntelliSense, o depurador pode ser inicializado e as referências exibidas no Solution Explorer podem ser resolvidas. Se esses alvos não estiverem presentes, o projeto carregará e construirá corretamente, mas a experiência de tempo de projeto no Visual Studio não será totalmente funcional.

## <a name="edit-project-files-in-visual-studio"></a>Editar arquivos de projeto no Visual Studio

 Para editar um projeto MSBuild diretamente, você pode abrir o arquivo do projeto no editor Do Visual Studio XML.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Para descarregar e editar um arquivo de projeto no Visual Studio

1. No **Gerenciador de Soluções**, abra o menu de atalho do projeto e, em seguida, escolha **Descarregar Projeto**.

     O projeto está marcado como **(indisponível)**.

2. No **Gerenciador de Soluções**, abra o menu de atalho do projeto indisponível e, em seguida, escolha **Editar \<Arquivo de Projeto>**.

     O arquivo de projeto será aberto no Editor de XML do Visual Studio.

3. Edite, salve e feche o arquivo de projeto.

4. No **Gerenciador de Soluções**, abra o menu de atalho do projeto indisponível e, em seguida, escolha **Recarregar Projeto**.

## <a name="intellisense-and-validation"></a>IntelliSense e validação

 Ao usar o editor XML para editar arquivos de projeto, o IntelliSense e a validação são acionados pelos arquivos do esquema MSBuild. Estes são instalados no cache do esquema, que pode ser encontrado no * \<diretório de instalação do Visual Studio>\Xml\Schemas\1033\MSBuild*.

 Os principais tipos de MSBuild são definidos no *Microsoft.Build.Core.xsd* e os tipos comuns usados pelo Visual Studio são definidos no *Microsoft.Build.CommonTypes.xsd*. Para personalizar os esquemas a fim de obter o IntelliSense e a validação para nomes, propriedades e tarefas de tipo de item personalizados, é possível editar o *Microsoft.Build.xsd* ou criar um esquema próprio que inclua CommonTypes ou esquemas de Núcleo. Ao criar um esquema próprio, será necessário direcionar o editor de XML a encontrá-lo por meio da janela **Propriedades**.

## <a name="edit-loaded-project-files"></a>Como editar arquivos de projeto carregados

 O Visual Studio armazena em cache o conteúdo de arquivos de projeto e arquivos importados por arquivos do projeto. Se você editar um arquivo de projeto carregado, o Visual Studio solicitará automaticamente que você recarregue o projeto para que as alterações entrem em vigor. No entanto, se um arquivo importado por um projeto carregado for editado, não haverá solicitação de recarregamento e será necessário descarregar e recarregar o projeto manualmente para que as alterações tenham efeito.

## <a name="output-groups"></a>Grupos de saída

 Vários alvos definidos no *Microsoft.Common.targets* têm nomes terminando `OutputGroups` ou `OutputGroupDependencies`. O Visual Studio chama esses alvos para obter listas específicas de saídas de projetos. Por exemplo, o destino `SatelliteDllsProjectOutputGroup` cria uma lista de todos os assemblies satélites que um build criará. Esses grupos de saída são usados por recursos como publicação, implantação e referências projeto a projeto. Projetos que não os definem serão carregados e construídos no Visual Studio, mas alguns recursos podem não funcionar corretamente.

## <a name="reference-resolution"></a>Resolução de referência

 Resolução de referência é o processo de usar os itens de referência armazenados em um arquivo de projeto para localizar assemblies reais. O Visual Studio deve acionar a resolução de referência para mostrar propriedades detalhadas para cada referência na janela **Propriedades.** A lista a seguir descreve os três tipos de referências e como elas são resolvidas.

- Referências do assembly:

   O sistema de projeto chama um destino com o nome conhecido `ResolveAssemblyReferences`. Esse destino deve produzir itens com o nome de tipo de item `ReferencePath`. Cada um desses itens deve ter uma especificação de item (o valor do atributo `Include` de um item) que contém o caminho completo para a referência. Os itens devem ter todos os metadados dos itens de entrada aprovados, além dos novos metadados a seguir:

  - `CopyLocal`, que indica se o assembly deve ser copiado para a pasta de saída, definido como true ou false.

  - `OriginalItemSpec`, que contém a especificação de item original da referência.

  - `ResolvedFrom`, definido como "{TargetFrameworkDirectory}" se ele tiver sido resolvido por meio do diretório do .NET Framework.

- Referências COM:

   O sistema de projeto chama um destino com o nome conhecido `ResolveCOMReferences`. Esse destino deve produzir itens com o nome de tipo de item `ComReferenceWrappers`. Cada um desses itens deve ter uma especificação de item que contém o caminho completo para o assembly de interoperabilidade da referência COM. Os itens devem ter todos os metadados dos itens de entrada aprovados, além dos novos metadados com o nome `CopyLocal`, que indicam se o assembly deve ser copiado para a pasta de saída, definido como true ou false.

- Referências nativas

   O sistema de projeto chama um destino com o nome conhecido `ResolveNativeReferences`. Esse destino deve produzir itens com o nome de tipo de item `NativeReferenceFile`. Os itens devem ter todos os metadados dos itens de entrada aprovados, além de uma nova parte de metadados com o nome `OriginalItemSpec`, que contém a especificação de item original da referência.

## <a name="performance-shortcuts"></a>Atalhos de desempenho

 Se você usar o Visual Studio IDE para iniciar a depuração (escolhendo a tecla F5 ou escolhendo **Debug** > **Start Debugging** na barra de menu) ou para construir seu projeto (por exemplo, **Build** > **Build Solution),** o processo de compilação usa uma verificação de atualização rápida para melhorar o desempenho. Em alguns casos nos quais builds personalizados criam arquivos que, por sua vez, são compilados, a verificação de atualização rápida não identificará os arquivos alterados corretamente. Projetos que precisam de verificações de atualização mais completas podem desligue a verificação rápida configurando a variável de ambiente `DISABLEFASTUPTODATECHECK=1`. Como alternativa, os projetos podem definir isso como uma propriedade de MSBuild no projeto ou em um arquivo importado pelo projeto.

 A atualização rápida não se aplica a builds regulares no Visual Studio e o projeto será compilado como se o build tivesse sido invocado por meio do prompt de comando.

## <a name="see-also"></a>Confira também

- [Como: Estender o processo de construção do Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Iniciar um build pelo IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Registrar extensões do .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)
- [Elemento-alvo (MSBuild)](../msbuild/target-element-msbuild.md)
- [Tarefa csc](../msbuild/csc-task.md)
- [Tarefa VBC](../msbuild/vbc-task.md)
