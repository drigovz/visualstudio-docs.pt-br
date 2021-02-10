---
title: Implantando extensões para as ferramentas do SharePoint no Visual Studio | Microsoft Docs
description: Implantar extensões para ferramentas do SharePoint no Visual Studio. Use projetos de VSIX (Visual Studio Extension) para criar pacotes VSIX.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6a899bcc132b9229c1046dee5793278f79ea9e5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948889"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Implantar extensões para as ferramentas do SharePoint no Visual Studio

Para implantar uma extensão de ferramentas do SharePoint, crie um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de VSIX (extensão) que contém o assembly de extensão e todos os outros arquivos que você deseja distribuir com a extensão. Um pacote VSIX é um arquivo compactado que segue o padrão OPC (Open Packaging Conventions). Os pacotes VSIX têm a extensão *. vsix* .

Depois de criar um pacote VSIX, outros usuários podem executar o arquivo. vsix para instalar a extensão. Quando um usuário instala sua extensão, todos os arquivos são instalados na pasta%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Para implantar a extensão, você pode carregar o pacote VSIX no site [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , ou pode distribuir o pacote para seus clientes por outros meios, como hospedar o pacote em um compartilhamento de rede ou em algum outro site.

Para obter mais informações sobre como criar pacotes VSIX e implantá-los no [Visual Studio Marketplace](https://marketplace.visualstudio.com/), consulte [enviando extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Você pode criar um pacote VSIX usando o modelo de **projeto VSIX** no Visual Studio ou pode criar um pacote VSIX manualmente.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Usar projetos VSIX para criar pacotes VSIX

Você pode usar o modelo de **projeto VSIX** fornecido pelo SDK do Visual Studio para criar pacotes VSIX para extensões de ferramentas do SharePoint. O uso de um projeto VSIX fornece vários benefícios sobre a criação manual de um pacote VSIX:

- O Visual Studio gera automaticamente o pacote VSIX quando você cria o projeto. Tarefas como adicionar os arquivos de implantação ao pacote e criar o arquivo [Content_Types]. xml para o pacote são feitas para você.

- Você pode configurar o projeto VSIX para incluir a saída da compilação de seu projeto de extensão e outros arquivos, como modelos de projeto e modelos de item, no pacote VSIX.

Para obter mais informações sobre como usar um projeto VSIX, consulte [modelo de projeto VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organizar seus projetos

Por padrão, os projetos VSIX geram apenas pacotes VSIX, não assemblies. Portanto, você normalmente não implementa uma extensão de ferramentas do SharePoint em um projeto VSIX. Geralmente, você trabalha com pelo menos dois projetos:

- Um projeto VSIX.

- Um projeto de biblioteca de classes que implementa sua extensão.

Você também pode trabalhar com projetos adicionais para determinados tipos de extensões:

- Um projeto de biblioteca de classes que implementa qualquer comando do SharePoint que é usado por sua extensão. Para obter instruções que demonstram esse cenário, consulte [passo a passos: estender Gerenciador de servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Um modelo de item ou projeto de modelo de projeto que cria um modelo de item ou modelo de projeto, se sua extensão define um novo tipo de item de projeto do SharePoint. Para obter instruções que demonstram esse cenário, consulte [Walkthrough: criar um item de projeto de ação personalizada com um modelo de item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Um projeto de biblioteca de classes que implementa um assistente personalizado para um modelo de item ou modelo de projeto, se sua extensão incluir um modelo. Para obter instruções que demonstram esse cenário, consulte [Walkthrough: criar um item de projeto de ação personalizada com um modelo de item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Se você incluir todos os projetos na mesma solução do Visual Studio, poderá modificar o arquivo Source. Extension. vsixmanifest no projeto VSIX para incluir a saída da compilação dos projetos da biblioteca de classes.

### <a name="edit-the-vsix-manifest"></a>Editar o manifesto do VSIX

Você deve editar o arquivo Source. Extension. vsixmanifest no projeto VSIX para incluir entradas para todos os itens que você deseja incluir em sua extensão. Quando você abre o arquivo Source. Extension. vsixmanifest em seu menu de atalho, o arquivo aparece em um designer que fornece uma interface do usuário para editar o XML no arquivo. Para obter mais informações, consulte o [Designer de manifesto do VSIX](../extensibility/vsix-manifest-designer.md).

Você deve adicionar entradas ao arquivo Source. Extension. vsixmanifest para os seguintes itens:

- O assembly de extensão.

- O assembly que implementa os comandos do SharePoint que são usados por sua extensão.

- Todos os modelos de projeto ou modelos de item associados à sua extensão.

- Um assistente personalizado para um modelo associado à sua extensão.

Os procedimentos a seguir descrevem como adicionar entradas ao arquivo. vsixmanifest para cada um desses itens.

#### <a name="to-include-the-extension-assembly"></a>Para incluir o assembly de extensão

1. No projeto VSIX, abra o menu de atalho do arquivo Source. Extension. vsixmanifest e, em seguida, escolha **abrir**.

     O arquivo é aberto no designer

2. Na guia **ativos** do editor, escolha o botão **novo** .

     A caixa de diálogo **Adicionar novo ativo** é aberta.

3. Na lista **tipo** , escolha **Microsoft. VisualStudio. MefComponent**.

4. Na lista **origem** , execute uma das seguintes etapas:

    - Se o assembly de extensão for criado a partir de um projeto que está na mesma solução que o projeto VSIX, escolha **um projeto na solução atual**. Na lista **projeto** , escolha o nome do projeto.

    - Se o assembly de extensão estiver incluído como um arquivo em seu projeto, escolha **arquivo no sistema de arquivos**. Na lista **caminho** , insira o caminho completo para o arquivo de assembly de extensão ou use o botão **procurar** para localizar e escolher o arquivo de assembly.

5. Clique no botão **OK**.

#### <a name="to-include-a-sharepoint-command-assembly"></a>Para incluir um assembly de comando do SharePoint

1. No projeto VSIX, abra o menu de atalho do arquivo Source. Extension. vsixmanifest e, em seguida, escolha o botão **abrir** .

     O arquivo é aberto no designer.

2. Na seção **ativos** do editor, escolha o botão **novo** .

     A caixa de diálogo **Adicionar novo ativo** é aberta.

3. Na caixa **tipo** , digite **SharePoint. Commands. v4**.

4. Na lista **origem** , execute uma das seguintes etapas:

    - Se o assembly de comando for criado a partir de um projeto que está na mesma solução que o projeto VSIX, escolha **um projeto na solução atual**. Na lista **projeto** , escolha o nome do projeto.

    - Se o assembly de comando estiver incluído como um arquivo em seu projeto, escolha **arquivo no sistema de arquivos**. Na lista **caminho** , insira o caminho completo para o arquivo de assembly de extensão ou use o botão **procurar** para localizar e escolher o arquivo de assembly.

5. Clique no botão **OK**.

#### <a name="to-include-a-template-that-you-create"></a>Para incluir um modelo que você criar

1. No projeto VSIX, abra o menu de atalho do arquivo Source. Extension. vsixmanifest e, em seguida, escolha o botão **abrir** .

     O arquivo é aberto no designer.

2. Na seção **ativos** do editor, escolha o botão **novo** .

     A caixa de diálogo **Adicionar novo ativo** é aberta.

3. Na lista **tipo** , escolha **Microsoft. VisualStudio. ProjectTemplate** ou **Microsoft. VisualStudio. ItemTemplate**.

4. Na lista **origem** , escolha **um projeto na solução atual**.

5. Na lista **projeto** , escolha o nome do projeto e, em seguida, escolha o botão **OK** .

6. No **Gerenciador de soluções**, abra o menu de atalho para o modelo de projeto ou projeto de modelo de item e escolha **descarregar projeto**.

7. Abra o menu de atalho para o nó do projeto novamente e escolha **Editar**_YourTemplateProjectName_**. csproj** ou **Editar**_YourTemplateProjectName_**. vbproj**.

8. Localize o seguinte `VSTemplate` elemento no arquivo de projeto.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Substitua esse elemento pelo XML a seguir.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     O `OutputSubPath` elemento especifica pastas adicionais no caminho em que o modelo de projeto é criado quando você cria o projeto. As pastas especificadas aqui garantem que o modelo de item estará disponível somente quando os clientes abrirem a caixa de diálogo **Adicionar novo projeto** , expandir o nó do **SharePoint** e, em seguida, escolher o nó **2010** .

10. Salve e feche o arquivo.

11. No **Gerenciador de soluções**, abra o menu de atalho para o modelo de projeto ou projeto de modelo de item e, em seguida, escolha **recarregar projeto**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Para incluir um modelo que você cria manualmente

1. No projeto VSIX, adicione uma nova pasta ao projeto para conter o modelo.

2. Nessa nova pasta, crie as seguintes subpastas e, em seguida, adicione o arquivo de modelo (. zip) à pasta de *identificação de localidade* .

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *ID da Localidade*

     *YourTemplateName*. zip

     Por exemplo, se você tiver um modelo de item chamado ContosoCustomAction.zip que dá suporte à localidade inglês (Estados Unidos), o caminho completo poderá ser *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. Em **Gerenciador de soluções**, escolha o arquivo de modelo (*YourTemplateName*. zip).

4. Na janela **Propriedades** , defina a propriedade **ação de compilação** como **conteúdo**.

5. Abra o menu de atalho para o arquivo Source. Extension. vsixmanifest e, em seguida, escolha **abrir**.

     O arquivo é aberto no designer.

6. Na seção **ativos** do editor, escolha o botão **novo** .

     A caixa de diálogo **Adicionar novo ativo** é aberta.

7. Na lista **tipo** , escolha **Microsoft. VisualStudio. ItemTemplate** ou **Microsoft. VisualStudio. ProjectTemplate**.

8. Na lista **origem** , escolha **arquivo em sistema de arquivos**.

9. No campo **caminho** , insira o caminho completo para o assembly (por exemplo, *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip* ou use o botão **procurar** para localizar e escolher o assembly e, em seguida, escolha o botão **OK** .

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Para incluir um assistente para um modelo de projeto ou modelo de item

1. No projeto VSIX, abra o menu de atalho do arquivo Source. Extension. vsixmanifest e, em seguida, escolha **abrir**.

     O arquivo é aberto no designer.

2. Na seção **ativos** do editor, escolha o botão **novo** .

     A caixa de diálogo **Adicionar novo ativo** é aberta.

3. Na lista **tipo** , escolha **Microsoft. VisualStudio. assembly**.

4. Na lista **origem** , execute uma das seguintes etapas:

    - Se o assembly do assistente for criado a partir de um projeto que está na mesma solução que o projeto VSIX, escolha **um projeto na solução atual**. Na lista **projeto** , escolha o nome do projeto.

    - Se o assembly do assistente for incluído como um arquivo em seu projeto, escolha **arquivo no sistema de arquivos**. No campo **caminho** , insira o caminho completo para o arquivo do assembly ou use o botão **procurar** para localizar e escolher o assembly.

5. Clique no botão **OK**.

### <a name="related-walkthroughs"></a>Instruções relacionadas

A tabela a seguir lista orientações explicativas que demonstram como usar um projeto VSIX para implantar diferentes tipos de extensões de ferramentas do SharePoint.

|Tipo de extensão|Instruções relacionadas|
|--------------------|--------------------------|
|Uma extensão que inclui apenas o assembly de extensão|[Walkthrough: estender um tipo de item de projeto do SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Walkthrough: criar uma extensão de projeto do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Walkthrough: chamar o modelo de objeto de cliente do SharePoint em uma extensão Gerenciador de Servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Uma extensão que inclui comandos do SharePoint|[Walkthrough: criar uma etapa de implantação personalizada para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Walkthrough: estender Gerenciador de Servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Walkthrough: criar um item de projeto de coluna de site com um modelo de projeto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Uma extensão que inclui um modelo do Visual Studio|[Walkthrough: criar um item de projeto de ação personalizada com um modelo de item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Walkthrough: criar um item de projeto de coluna de site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Uma extensão que inclui um assistente de modelo|[Walkthrough: criar um item de projeto de ação personalizada com um modelo de item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Walkthrough: criar um item de projeto de coluna de site com um modelo de projeto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Criar pacotes VSIX manualmente

Se você quiser criar manualmente o pacote VSIX para sua extensão de ferramentas do SharePoint, execute as seguintes etapas:

1. Crie o arquivo extension. vsixmanifest e o arquivo [Content_Types]. xml em uma nova pasta. Para obter mais informações, consulte [anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2. No Windows Explorer, clique com o botão direito do mouse na pasta que contém os dois arquivos XML, clique em enviar para e clique em pasta compactada (zipada). Renomeie o arquivo. zip resultante para filename. vsix, em que filename é o nome do arquivo redistribuível que instala o pacote.

3. Adicione seu assembly de extensão ao pacote VSIX. Se a extensão incluir um comando do SharePoint, adicione também o assembly que implementa o comando do SharePoint ao pacote VSIX.

4. Modifique o arquivo extension. vsixmanifest:

    - Adicione um `Microsoft.VisualStudio.MefComponent` elemento sob o `Assets` elemento e, em seguida, defina o valor do novo elemento como o caminho relativo do assembly que implementa sua extensão no pacote VSIX. Para obter mais informações, consulte [elemento MEFComponent (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Se sua extensão incluir um comando do SharePoint que chama o modelo de objeto do servidor para SharePoint, adicione um `Microsoft.VisualStudio.Assembly` elemento sob o `Assets` elemento. Defina o valor do novo elemento como o caminho relativo do assembly que implementa o comando do SharePoint no pacote VSIX. Para obter mais informações, consulte [elemento Asset (esquema VSX)](/previous-versions/dd393737(v=vs.110)).

    - Se sua extensão incluir um modelo de projeto ou modelo de item, adicione um `ProjectTemplate` `ItemTemplate` elemento ou sob o `Assets` elemento. Defina o valor do novo elemento como o caminho relativo da pasta que contém o modelo no pacote VSIX. Para obter mais informações, consulte [elemento ProjectTemplate (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) e [elemento ITEMTEMPLATE (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Se sua extensão incluir um assistente personalizado para um modelo de projeto ou modelo de item, adicione um `Assembly` elemento sob o `Assets` elemento. Defina o valor do novo elemento como o caminho relativo do assembly no pacote VSIX e, em seguida, defina o `AssemblyName` atributo como o nome completo do assembly (incluindo a versão, a cultura e o token de chave pública). Para obter mais informações, consulte [elemento Dependency (esquema VSX)](/previous-versions/dd393682(v=vs.110)).

### <a name="example"></a>Exemplo

O exemplo a seguir mostra o conteúdo de um arquivo extension. vsixmanifest para uma extensão de ferramentas do SharePoint. A extensão é implementada em um assembly chamado Contoso.ProjectExtension.dll. A extensão inclui um assembly de comando do SharePoint chamado Contoso.ExtensionCommands.dll e um modelo de item em uma pasta denominada itens de **modelo** no pacote VSIX. Este exemplo pressupõe que ambos os assemblies estejam na mesma pasta que o arquivo de extensão. vsixmanifest no pacote VSIX.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Consulte também

- [Estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Estenda o nó conexões do SharePoint no Gerenciador de Servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Chamar para os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Extensões de depuração para as ferramentas do SharePoint no Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)