---
title: Localizando comandos do menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c879072b55729e249b1aecd665d6f470f4138a75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686131"
---
# <a name="localizing-menu-commands"></a>Localizando comandos de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode fornecer texto localizado para comandos de menu e barra de ferramentas criando arquivos. vsct localizados e arquivos. resx localizados para seu VSPackage e, em seguida, atualizando os arquivos de projeto para incorporar as alterações.  
  
 Para obter informações sobre como localizar a experiência de instalação, consulte [localizando pacotes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localizando nomes de comando  
 No VSPackages, os comandos de menu e os botões da barra de ferramentas são definidos no arquivo. vsct.  
  
1. Em **Gerenciador de soluções**, altere o nome do arquivo. vsct de *filename*. vsct para *filename*. en-US. vsct.  
  
2. Faça uma cópia de *filename*. en-US. vsct para cada idioma localizado.  
  
    Nomeie cada cópia de *nome de arquivo*. *Locale*. vsct, em que *locale* é um nome de cultura específico. Para obter uma lista de valores de nome de cultura, consulte [IDs de localidade atribuídas pela Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Esse *nome de arquivo*. Os arquivos *locale*. vsct conterão o texto de menu localizado para o pacote.  
  
3. Abra cada *nome de arquivo*. Arquivo *locale*. vsct para localizar o texto.  
  
   1. Modifique os valores do elemento [ButtonText](../extensibility/buttontext-element.md) conforme apropriado para o idioma específico.  
  
   2. Se você fornecer ícones localizados, modifique os valores de [bitmap](../extensibility/bitmap-element.md) para apontar para os arquivos de destino.  
  
      O exemplo a seguir mostra o texto do botão inglês e espanhol de um comando para abrir uma janela de ferramenta do Gerenciador de árvore de família.  
  
      [FamilyTree. en-US. vsct]  
  
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
  
    [FamilyTree.es-ES. vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>Localizando outros recursos de texto  
 Recursos de texto diferentes de nomes de comando são definidos em arquivos de recurso (. resx).  
  
1. Renomeie VSPackage. resx para VSPackage. en-US. resx.  
  
2. Faça uma cópia do arquivo VSPackage. en-US. resx para cada idioma localizado.  
  
     Nomeie cada cópia VSPackage. *Locale*. resx, em que *locale* é um nome de cultura específico.  
  
3. Renomeie Resources. resx para Resources. en-US. resx.  
  
4. Faça uma cópia do arquivo Resources. en-US. resx para cada idioma localizado.  
  
     Nomeie cada recurso de cópia. *Locale*. resx, em que *locale* é um nome de cultura específico.  
  
5. Abra cada arquivo. resx para modificar os valores da cadeia de caracteres conforme apropriado para o idioma e a cultura específicos. O exemplo a seguir mostra a definição de recurso localizado para a barra de título de uma janela de ferramenta.  
  
     [Resources. en-US. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Incorporando recursos localizados ao projeto  
 Você deve modificar o arquivo assemblyinfo.cs e o arquivo de projeto para incorporar os recursos localizados.  
  
1. No nó **Propriedades** no **Gerenciador de Soluções**, abra AssemblyInfo.cs ou AssemblyInfo. vb no editor.  
  
2. Adicione a entrada a seguir.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Isso define inglês americano como o idioma padrão.  
  
3. Descarregue o projeto.  
  
4. Abra o arquivo de projeto no editor.  
  
5. Localize o `ItemGroup` elemento que contém `EmbeddedResource` elementos.  
  
6. No `EmbeddedResource` elemento que chama VSPackage. en-US. resx, substitua o `ManifestResourceName` elemento por um `LogicalName` elemento, definido como `VSPackage.en-US.Resources` , da seguinte maneira.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. Para cada idioma localizado, copie o  `EmbeddedResource` elemento para VSPackage. en-US e defina o atributo **include** e o elemento **LogicalName** da cópia para a localidade de destino, conforme mostrado no exemplo a seguir.  
  
8. Para cada `VSCTCompile` elemento localizado, adicione um `ResourceName` elemento que aponte para `Menus.ctmenu` , conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Salve o arquivo de projeto e recarregue o projeto.  
  
10. Compile o projeto.  
  
     Isso cria um assembly principal e assemblies de recurso para cada idioma. Para obter informações sobre como localizar o processo de implantação, consulte [localizando pacotes VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Estendendo menus e comandos](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalização e localização](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
