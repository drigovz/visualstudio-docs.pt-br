---
title: Criando um Kit de Desenvolvimento de Software | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739597"
---
# <a name="create-a-software-development-kit"></a>Crie um kit de desenvolvimento de software

Um kit de desenvolvimento de software (SDK) é uma coleção de APIs que você pode referenciar como um único item no Visual Studio. A caixa de diálogo **Gerenciador de** referência lista todos os SDKs relevantes para o projeto. Quando você adiciona um SDK a um projeto, as APIs estão disponíveis no Visual Studio.

Existem dois tipos de SDKs:

- Os SDKs da plataforma são componentes obrigatórios para o desenvolvimento de aplicativos para uma plataforma. Por exemplo, [!INCLUDE[win81](../debugger/includes/win81_md.md)] o SDK [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] é necessário para desenvolver aplicativos.

- Os SDKs de extensão são componentes opcionais que estendem uma plataforma, mas não são obrigatórios para o desenvolvimento de aplicativos para essa plataforma.

As seções a seguir descrevem a infra-estrutura geral de SDKs e como criar uma plataforma SDK e uma extensão SDK.

## <a name="platform-sdks"></a>SDKs de plataforma

Os SDKs da plataforma são necessários para desenvolver aplicativos para uma plataforma. Por exemplo, [!INCLUDE[win81](../debugger/includes/win81_md.md)] o SDK é [!INCLUDE[win81](../debugger/includes/win81_md.md)]necessário para desenvolver aplicativos para .

### <a name="installation"></a>Instalação

Todos os SDKs da plataforma serão instalados no *HKLM\Software\Microsoft\Microsoft SDKs\\[TPI]\v[TPV]\\ @InstallationFolder = [raiz do SDK]*. Assim, o [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK está instalado no *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.

### <a name="layout"></a>Layout

Os SDKs da plataforma têm o seguinte layout:

```
\[InstallationFolder root]
            SDKManifest.xml
            \References
                  \[config]
                        \[arch]
            \DesignTime
                  \[config]
                        \[arch]
```

| Nó | Descrição |
|------------------------| - |
| *Pasta de referências* | Contém binários que contêm APIs que podem ser codificados contra. Isso pode incluir arquivos ou conjuntos de metadados do Windows (WinMD). |
| *Pasta DesignTime* | Contém arquivos que são necessários apenas na hora da pré-execução/depuração. Estes podem incluir docs XML, bibliotecas, cabeçalhos, binários de tempo de design de caixa de ferramentas, artefatos MSBuild e assim por diante<br /><br /> Os documentos XML seriam, idealmente, colocados na pasta *\DesignTime,* mas os documentos XML para referências continuarão a ser colocados ao lado do arquivo de referência no Visual Studio. Por exemplo, o doc XML para uma referência<em>\\\Referências [config]\\[arch]\sample.dll</em> será *\Referências\\[config]\\[arch]\sample.xml*, e a versão localizada desse doc será *\Referências\\[config]\\[arch]\\[locale]\sample.xml*. |
| *Pasta de configuração* | Só pode haver três pastas: *Debug*, *Retail* e *CommonConfiguration*. Os autores do SDK podem colocar seus arquivos em *CommonConfiguration* se o mesmo conjunto de arquivos SDK deve ser consumido, independentemente da configuração que o consumidor SDK será alvo. |
| *Pasta de arquitetura* | Qualquer pasta *de arquitetura* suportada pode existir. O Visual Studio suporta as seguintes arquiteturas: x86, x64, ARM e neutra. Nota: Mapas Win32 para x86 e mapas AnyCPU para neutro.<br /><br /> O MSBuild só fica em *\CommonConfiguration\neutral* para SDKs de plataforma. |
| *SDKManifest.xml* | Este arquivo descreve como o Visual Studio deve consumir o SDK. Veja o Manifesto SDK para: [!INCLUDE[win81](../debugger/includes/win81_md.md)]<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Nome do display:** O valor que o Navegador de Objeto exibe na lista Procurar.<br /><br /> **Identidade da plataforma:** A existência deste atributo diz ao Visual Studio e ao MSBuild que o SDK é uma plataforma SDK e que as referências adicionadas a partir dele não devem ser copiadas localmente.<br /><br /> **TargetFramework:** Este atributo é usado pelo Visual Studio para garantir que apenas projetos que visam os mesmos Frameworks especificados no valor deste atributo possam consumir o SDK.<br /><br /> **MinVSVersion:** Este atributo é usado pelo Visual Studio para consumir apenas os SDKs que se aplicam a ele.<br /><br /> **Referência:** Este atributo deve ser especificado apenas para as referências que contêm controles. Para obter informações sobre como especificar se uma referência contém controles, consulte abaixo. |

## <a name="extension-sdks"></a>SDKs de extensão

As seções a seguir descrevem o que você precisa fazer para implantar um SDK de extensão.

### <a name="installation"></a>Instalação

Os SDKs de extensão podem ser instalados para um usuário específico ou para todos os usuários sem especificar uma chave de registro. Para instalar um SDK para todos os usuários, use o seguinte caminho:

*%Arquivos de programa%\Plataforma-alvo do Microsoft SDKs\<\>\v<número\>da versão da plataforma \ExtensionSDKs*

Para uma instalação específica do usuário, use o seguinte caminho:

*%USERPROFILE%\AppData\Local\Microsoft SDKs\<\>destino plataforma de\>destino \v<número de versão da plataforma \ExtensionSDKs*

Se você quiser usar um local diferente, você deve fazer uma de duas coisas:

1. Especifique-o em uma chave de registro:

     **HKLM\Software\Microsoft\Microsoft\<SDKs alvo plataforma alvo>\v número de versão da plataforma<\>\ExtensionSDKs\<SDKName>\<SDKVersion>**\

     e adicionar uma subchave (Padrão) `<path to SDK><SDKName><SDKVersion>`que tenha um valor de .

2. Adicione a propriedade `SDKReferenceDirectoryRoot` MSBuild ao seu arquivo de projeto. O valor desta propriedade é uma lista delimitada de diretórios em que os SDKs de extensão que você deseja referenciar residem.

### <a name="installation-layout"></a>Layout de instalação

Os SDKs de extensão têm o seguinte layout de instalação:

```
\<ExtensionSDKs root>
           \<SDKName>
                 \<SDKVersion>
                        SDKManifest.xml
                        \References
                              \<config>
                                    \<arch>
                        \Redist
                              \<config>
                                    \<arch>
                        \DesignTime
                               \<config>
                                     \<arch>

```

1. \\<SDKName\> \\<SDKVersion\>: o nome e a versão da extensão SDK é derivado dos nomes de pasta correspondentes no caminho para a raiz SDK. O MSBuild usa essa identidade para encontrar o SDK no disco, e o Visual Studio exibe essa identidade na caixa de diálogo **Propriedades** e **Gerenciador de** referências.

2. *Pasta de referências:* os binários que contêm as APIs. Estes podem ser arquivos ou conjuntos de metadados do Windows (WinMD).

3. *Pasta redist:* os arquivos necessários para tempo de execução/depuração e devem ser embalados como parte do aplicativo do usuário. Todos os binários devem ser colocados abaixo *de \redist\\ \> \\<config\><arco*, e os nomes binários devem ter o seguinte formato para garantir a exclusividade: *]*\<empresa>. \<> do produto. \<> propósito. \<>de extensão <em>. Por exemplo, *Microsoft.Cpp.Build.dll</em>. Todos os arquivos com nomes que possam colidir com nomes de arquivos de outros SDKs (por exemplo, javascript, css, pri, xaml, png e jpg files) devem ser colocados abaixo <em>de\\ \redist<\> \\ config<\> \\ arco<\> \* sdkname, exceto para os arquivos que estão associados aos controles XAML. Esses arquivos devem ser colocados\\ abaixo de\> \\ *\redist<config<arch\> \\<componentname\></em>.

4. *Pasta DesignTime:* os arquivos necessários apenas em tempo de pré-execução/depuração e não devem ser embalados como parte do aplicativo do usuário. Estes podem ser docs XML, bibliotecas, cabeçalhos, binários de tempo de design de caixas de ferramentas, artefatos MSBuild, e assim por diante. Qualquer SDK destinado ao consumo por um projeto nativo deve ter um arquivo *SDKName.props.* A seguir, mostra uma amostra deste tipo de arquivo.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>
       <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>
       <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>
       <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>
       <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>
       <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>
       <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>
     </PropertyGroup>
   </Project>

   ```

    Os documentos de referência XML são colocados ao lado do arquivo de referência. Por exemplo, o documento de referência XML para o *\\ \Referências<\> \\ config<conjunto arch\>\sample.dll* é *\Referências\\<config\> \\<arch\>\sample.xml,* e a versão localizada desse doc é *\Referências\\<config\> \\<arco\> \\<local\>\sample.xml*.

5. *Pasta de configuração:* três subpastas: *Depuração,* *Varejo*e *Configuração Comum*. Os autores do SDK podem colocar seus arquivos em *CommonConfiguration* quando o mesmo conjunto de arquivos SDK deve ser consumido, independentemente da configuração direcionada pelo consumidor SDK.

6. *Pasta de* arquitetura: as seguintes arquiteturas são suportadas: x86, x64, ARM, neutro. Mapas Win32 para x86, e mapas AnyCPU para neutro.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

O arquivo *SDKManifest.xml* descreve como o Visual Studio deve consumir o SDK. A seguir, é mostrado um exemplo:

```
<FileList>
DisplayName = "My SDK"
ProductFamilyName = "My SDKs"
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"
MinVSVersion = "14.0"
MaxPlatformVersion = "8.1"
AppliesTo = "WindowsAppContainer + WindowsXAML"
SupportPrefer32Bit = "True"
SupportedArchitectures = "x86;x64;ARM"
SupportsMultipleVersions = "Error"
CopyRedistToSubDirectory = "."
DependsOn = "SDKB, version=2.0"
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

A lista a seguir fornece os elementos do arquivo:

1. DisplayName: o valor que aparece no Gerenciador de Referência, No Solution Explorer, no Object Browser e em outros locais na interface do usuário para o Visual Studio.

2. ProductFamilyName: O nome geral do produto SDK. Por exemplo, [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] o SDK é chamado de "Microsoft.WinJS.1.0" e "Microsoft.WinJS.2.0", que pertencem à mesma família de produtos SDK, "Microsoft.WinJS". Este atributo permite que o Visual Studio e o MSBuild façam essa conexão. Se esse atributo não existir, o Nome SDK será usado como nome da família do produto.

3. FrameworkIdentity: Especifica uma dependência de uma ou mais bibliotecas de componentes do Windows. O valor deste atributo é colocado no manifesto do aplicativo de consumo. Este atributo é aplicável apenas às bibliotecas de componentes do Windows.

4. TargetFramework: Especifica os SDKs disponíveis no Gerenciador de Referência e na caixa de ferramentas. Esta é uma lista delimitada de ponto e vírgula de apelidos de quadro de destino, por exemplo ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1". Se várias versões da mesma estrutura de destino forem especificadas, o Gerenciador de referência usará a versão mais baixa especificada para fins de filtragem. Por exemplo, se ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1" for especificado, o Gerenciador de Referência usará ".NET Framework, version=v2.0". Se um perfil de quadro de destino específico for especificado, apenas esse perfil será usado pelo Gerenciador de Referência para fins de filtragem. Por exemplo, quando "Silverlight, version=v4.0, profile=WindowsPhone" é especificado, o Gerenciador de referência filtra apenas o perfil do Windows Phone; um projeto direcionado ao Quadro Silverlight 4.0 completo não vê o SDK no Gerenciador de Referência.

5. MinVSVersion: A versão mínima do Visual Studio.

6. MaxPlatformVerson: A versão máxima da plataforma de destino deve ser usada para especificar as versões da plataforma nas quais o SDK de extensão não funcionará. Por exemplo, o Microsoft Visual C++ Runtime Package v11.0 deve ser referenciado apenas por projetos do Windows 8. Assim, o MaxPlatformVersion do projeto Windows 8 é 8.0. Isso significa que o Gerenciador de referência filtra o Microsoft Visual C++ Runtime Package para [!INCLUDE[win81](../debugger/includes/win81_md.md)] um projeto do Windows 8.1, e o MSBuild lança um erro quando um projeto o faz referência. Nota: este elemento é [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]suportado a partir de .

7. Aplica-se: Especifica os SDKs disponíveis no Gerenciador de Referência, especificando os tipos de projeto do Visual Studio aplicáveis. Nove valores são reconhecidos: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed e Native. O autor do SDK pode usar e ("+'), ou ("&#124;"), não ("!") operadores para especificar exatamente o escopo dos tipos de projeto que se aplicam ao SDK.

    O WindowsAppContainer identifica [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projetos para aplicativos.

8. SuportePrefer32Bit: Os valores suportados são "Verdadeiro" e "Falso". O padrão é "True". Se o valor estiver definido como "Falso", [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] o MSBuild reajusta um erro para projetos (ou um aviso para projetos de desktop) se o projeto que faz referência ao SDK tiver o Prefer32Bit ativado. Para obter mais informações sobre prefer32Bit, consulte [Build page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md) ou [Compile page, Project Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. Arquiteturas suportadas: uma lista delimitada de arquiteturas deponto e vírgula que o SDK suporta. O MSBuild exibe um aviso se a arquitetura SDK direcionada no projeto de consumo não for suportada. Se esse atributo não for especificado, o MSBuild nunca exibirá esse tipo de aviso.

10. SuportesMultipleVersions: Se este atributo estiver definido como **Erro** ou **Aviso,** o MSBuild indica que o mesmo projeto não pode referenciar várias versões da mesma família SDK. Se esse atributo não existir ou estiver definido como **Permitir,** o MSBuild não exibirá esse tipo de erro ou aviso.

11. AppX: Especifica o caminho para os pacotes de aplicativos para a biblioteca de componentes do Windows no disco. Esse valor é passado para o componente de registro da biblioteca de componentes do Windows durante a depuração local. A convenção de nomeação para o nome do arquivo é * \<Companhia>.\<> do produto. \<Arquitetura>. \<Configuração>. Versão \<>.appx*. Configuração e arquitetura são opcionais no nome do atributo e no valor do atributo se eles não se aplicarem à biblioteca de componentes do Windows. Esse valor é aplicável apenas às bibliotecas de componentes do Windows.

12. CopyRedistToSubDirectory: Especifica onde os arquivos sob a pasta *\redist* devem ser copiados em relação à raiz do pacote do aplicativo (ou seja, o local do **pacote** escolhido no assistente **Criar pacote de aplicativos)** e a raiz do layout em tempo de execução. O local padrão é a raiz do pacote do aplicativo e do layout **F5.**

13. DependSOn: Uma lista de identidades SDK que definem os SDKs dos quais este SDK depende. Este atributo aparece no painel de detalhes do Gerenciador de Referência.

14. MoreInfo: A URL da página web que fornece ajuda e mais informações. Esse valor é usado no link Mais Informações no painel direito do Gerenciador de referência.

15. Tipo de registro: Especifica o registro WinMD no manifesto do aplicativo e é necessário para o WinMD nativo, que tem uma contrapartida de implementação DLL.

16. Referência do arquivo: Especificado apenas para as referências que contêm controles ou são WinMDs nativos. Para obter informações sobre como especificar se uma referência contém controles, consulte [Especificar a localização dos itens da caixa de ferramentas](#ToolboxItems) abaixo.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Especificar a localização dos itens da caixa de ferramentas

O elemento **ToolBoxItems** do esquema *SDKManifest.xml* especifica a categoria e a localização dos itens da caixa de ferramentas em SDKs de plataforma e extensão. Os exemplos a seguir mostram como especificar diferentes locais. Isso é aplicável a referências WinMD ou DLL.

1. Coloque controles na categoria padrão da caixa de ferramentas.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Coloque controles sob um nome de categoria específico.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Coloque controles em nomes de categorias específicos.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Coloque controles em diferentes nomes de categoria em Blend e Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Enumerar controles específicos de forma diferente no Blend e visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Enumerar controles específicos e colocá-los sob o Visual Studio Common Path ou apenas no Grupo Todos os Controles.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Enumerar controles específicos e mostrar apenas um conjunto específico em ChooseItems sem que eles estão na caixa de ferramentas.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Confira também

- [Passo a passo: Crie um SDK usando C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Passo a passo: Crie um SDK usando C# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Gerenciar referências em um projeto](../ide/managing-references-in-a-project.md)
