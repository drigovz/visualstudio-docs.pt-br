---
title: Localização de comandos de menu | Microsoft Docs
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702955"
---
# <a name="localize-menu-commands"></a>Menu localize comandos

Você pode fornecer texto localizado para comandos de menu e barra de ferramentas criando arquivos *.vsct* localizados e arquivos *.resx localizados* para o seu VSPackage e, em seguida, atualizando os arquivos do projeto para incorporar as alterações.

Para obter informações sobre como localizar a experiência de instalação, consulte [os pacotes Localize VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localize nomes de comando

Em VSPackages, os comandos de menu e os botões da barra de ferramentas são definidos no arquivo *.vsct.*

1. No **Solution Explorer,** altere o nome do arquivo *.vsct* de *filename.vsct* para *filename.en-US.vsct*.

2. Faça uma cópia do *filename.en-US.vsct* para cada idioma localizado.

    Nomeie cada *nome de arquivo de cópia.{ Locale}.vsct*, onde *{Locale}* é um nome de cultura particular. Para obter uma lista de valores de nome de cultura, consulte [IDs](/windows/uwp/publish/supported-languages)locais atribuídos pela Microsoft .

    Esses *nomes de arquivo. Os arquivos Locale.vsct* conterão o texto do menu localizado para o pacote.

3. Abra cada *nome de arquivo. Arquivo Locale.vsct* para localizar o texto.

   1. Modifique os valores do elemento [ButtonText](../extensibility/buttontext-element.md) conforme apropriado para o idioma específico.

   2. Se você fornecer ícones localizados, modifique os valores do [Bitmap](../extensibility/bitmap-element.md) para apontar para os arquivos de destino.

      O exemplo a seguir mostra o texto do botão em inglês e espanhol para um comando para abrir uma janela de ferramenta do Family Tree Explorer.

      [*FamilyTree.en-US.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Localize outros recursos de texto

Os recursos de texto que não sejam nomes de comando são definidos em arquivos de recursos *(.resx).*

1. Renomear *VSPackage.resx* para *VSPackage.en-US.resx*.

2. Faça uma cópia do arquivo *VSPackage.en-US.resx* para cada idioma localizado.

     Nomeie cada cópia *VSPackage.{ Locale}.resx*, onde *{Locale}* é um nome de cultura particular.

3. Renomear *Resources.resx* para *Resources.en-US.resx*.

4. Faça uma cópia do arquivo *Resources.en-US.resx* para cada idioma localizado.

     Nomeie cada cópia *Resources.{ Locale}.resx*, onde *{Locale}* é um nome de cultura particular.

5. Abra cada arquivo *.resx* para modificar os valores de seqüência conforme apropriado para a linguagem e cultura específicas. O exemplo a seguir mostra a definição de recurso localizado para a barra de título de uma janela de ferramenta.

     [*Resources.en-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Incorporar recursos localizados ao projeto

Você deve modificar o arquivo *assemblyinfo.cs* e o arquivo do projeto para incorporar os recursos localizados.

1. Do nó **Propriedades** no **Solution Explorer**, *abra assemblyinfo.cs* ou *assemblyinfo.vb* no editor.

2. Adicione a seguinte entrada.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Isso define o inglês dos EUA como o idioma padrão.

3. Descarregue o projeto.

4. Abra o arquivo do projeto no editor.

5. No elemento `Project` raiz, `PropertyGroup` adicione um `UICulture` elemento com um elemento que corresponda à sua linguagem padrão.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Isso define o inglês dos EUA como a cultura de ui padrão para controles WPF (Windows Presentation Foundation).

6. Localize `ItemGroup` o `EmbeddedResource` elemento que contém elementos.

7. No `EmbeddedResource` elemento que chama *VSPackage.en-US.resx,* substitua o `ManifestResourceName` elemento por um `LogicalName` elemento definido como `VSPackage.en-US.Resources`:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Para cada idioma localizado, `EmbeddedResource` copie `VsPackage.en-US`o elemento para e defina o atributo **Incluir** e o elemento **LogicalName** da cópia para o local de destino.

9. A cada `VSCTCompile` elemento localizado, `ResourceName` adicione um `Menus.ctmenu`elemento que aponte, como mostrado no exemplo a seguir:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Salve o arquivo do projeto e recarregue o projeto.

11. Compile o projeto.

     Isso cria uma montagem principal e montagens de recursos para cada idioma. Para obter informações sobre como localizar o processo de implantação, consulte [os pacotes Localize VSIX](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Confira também

- [Estender menus e comandos](../extensibility/extending-menus-and-commands.md)
- [Globalize e localize aplicativos](../ide/globalizing-and-localizing-applications.md)
