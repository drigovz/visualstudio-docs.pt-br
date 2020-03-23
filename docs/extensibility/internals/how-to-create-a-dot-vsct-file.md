---
title: 'Como: Criar um . Arquivo Vsct | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3155ff69db461e652b11ff6e8ec6d405000244f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303165"
---
# <a name="how-to-create-a-vsct-file"></a>Como: Criar um arquivo .vsct

Existem várias maneiras de criar uma configuração de tabela de comando visual studio baseada em XML *(.vsct).*

- Você pode criar um novo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage no modelo do pacote.

- Você pode usar o compilador de configuração de tabela de comando baseado em XML, *Vsct.exe,* para gerar um arquivo a partir de um arquivo *.ctc* existente.

- Você pode usar *Vsct.exe* para gerar um arquivo *.vsct* a partir de um arquivo *.cto* existente.

- Você pode criar manualmente um novo arquivo *.vsct.*

  Este artigo explica como criar manualmente um novo arquivo *.vsct.*

### <a name="to-manually-create-a-new-vsct-file"></a>Para criar manualmente um novo arquivo .vsct

1. Inicie o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. No menu **Arquivo** , aponte para **Novo**e clique em **Arquivo**.

3. No **painel Modelos,** clique em **Arquivo XML** e clique em **Abrir**.

4. No **menu Exibir,** clique **em Propriedades** para exibir as propriedades do arquivo XML.

5. Na janela **Propriedades,** clique no botão **Procurar** na propriedade **Schemas.**

6. Na lista de esquemas XSD, selecione o esquema *vsct.xsd.* Se ele não estiver na lista, clique em **Adicionar** e, em seguida, encontre o arquivo em uma unidade local. Clique **em OK** quando terminar.

7. No arquivo XML, digite *<CommandTable* e pressione **Tab**. Feche a tag *>* digitando .

    Esta ação cria um arquivo *básico .vsct.*

8. Preencha os elementos do arquivo XML que você deseja adicionar, de acordo com a referência do [esquema VSCT XML](../../extensibility/vsct-xml-schema-reference.md). Para obter mais informações, consulte [Arquivos Author .vsct](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Como: Criar um arquivo .vsct a partir de um arquivo .ctc existente

Você pode criar um arquivo *.vsct* baseado em XML a partir de um arquivo de origem da tabela de comando *.ctc* existente. Ao fazer isso, você pode aproveitar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] novo formato de compilador da tabela de comando baseado em XML (VSCT).

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Para criar um arquivo .vsct a partir de um arquivo .ctc

1. Obtenha uma cópia da língua Perl.

2. Obtenha uma cópia do *ConvertCTCToVSCT.pl*de script Perl, normalmente localizado no caminho de instalação do * \<Visual Studio SDK>\VisualStudioIntegration\Tools\bin* folder.

3. Obtenha uma cópia do arquivo de origem *.ctc* que deseja converter.

4. Coloque os arquivos no mesmo diretório.

5. Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] janela de comando prompt, navegue até o diretório.

6. Type

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    onde *PkgCmd.ctc* é o nome do arquivo *.ctc* e *PkgCmd.vsct* é o nome do arquivo *.vsct* que você deseja criar.

    Esta ação cria um novo arquivo de origem da tabela de comando *.vsct* XML. Você pode compilar o arquivo usando *Vsct.exe*, o compilador VSCT, como qualquer outro arquivo *.vsct.*

   > [!NOTE]
   > Você pode melhorar a legibilidade do arquivo *.vsct* reformatando os comentários XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Como: Criar um arquivo .vsct a partir de um arquivo .cto existente

Você pode criar um arquivo *.vsct* baseado em XML a partir de um arquivo binário *.cto* existente. Fazer isso permite que você aproveite o novo formato de compilador de tabela de comando. Esse processo funciona mesmo se o arquivo *.cto* foi compilado a partir de um arquivo *.ctc.* Você pode editar e compilar o arquivo *.vsct* em outro arquivo .cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Para criar um arquivo .vsct a partir de um arquivo .cto

1. Obter cópias do arquivo *.cto* e seu arquivo *.ctsym* correspondente.

2. Coloque os arquivos no mesmo diretório do compilador *vsct.exe.*

3. No prompt de comando do Visual Studio, vá para o diretório que contém os arquivos *.cto* e *.ctsym.*

4. Type

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     onde \<\> ctofilename é o nome do \<arquivo\> *.cto,* vsctfilename é o nome do \<arquivo *.vsct* que você deseja criar, e symfilename\> é o nome do arquivo *.ctsym.*

     Este processo cria um novo arquivo de compilador de tabela de comando *.vsct* XML. Você pode editar e compilar o arquivo com *vsct.exe*, o compilador vsct, como qualquer outro arquivo *.vsct.*

## <a name="compile-the-code"></a>Compilar o código
 Simplesmente adicionar um *arquivo .vsct* a um projeto não faz com que ele seja compilado. Você deve incorporá-lo no processo de construção.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para adicionar um arquivo .vsct à compilação do projeto

1. Abra seu arquivo de projeto no editor. Se o projeto estiver carregado, você deve descarregá-lo primeiro.

2. Adicione um [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contenha um `VSCTCompile` elemento, como mostrado no exemplo a seguir.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     O `ResourceName` elemento deve ser `Menus.ctmenu`sempre definido para .

3. Se o projeto contiver um arquivo `EmbeddedResource` *.resx,* adicione um elemento que contenha um `MergeWithCTO` elemento, conforme mostrado no exemplo a seguir:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Esta marcação deve `ItemGroup` ir dentro do elemento que contém recursos incorporados.

4. Abra o arquivo do pacote, geralmente chamado * \<\>ProjectName Package.cs* ou * \<ProjectName\>Package.vb*, no editor.

5. Adicione `ProvideMenuResource` um atributo à classe de pacotes, como mostrado no exemplo a seguir.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     O primeiro valor do parâmetro deve `ResourceName` corresponder ao valor do atributo definido no arquivo do projeto.

## <a name="see-also"></a>Confira também
- [Arquivos autor .vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referência de esquema VSCT XML](../../extensibility/vsct-xml-schema-reference.md)