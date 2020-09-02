---
title: 'Como: criar um. Arquivo vsct | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158346"
---
# <a name="how-to-create-a-vsct-file"></a>Como criar um arquivo .Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Há várias maneiras de criar um arquivo de configuração de tabela de comando (. vsct) do Visual Studio baseado em XML.  
  
- Você pode criar um novo VSPackage no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] modelo de pacote.  
  
- Você pode usar o compilador de configuração de tabela de comando baseado em XML, Vsct.exe, para gerar um arquivo de um arquivo. CTC existente.  
  
- Você pode usar Vsct.exe para gerar um arquivo. vsct de um arquivo. CTO existente.  
  
- Você pode criar manualmente um novo arquivo. vsct.  
  
  Este tópico explica como criar um novo arquivo. vsct manualmente.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Para criar manualmente um novo arquivo. vsct  
  
1. Inicie o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2. No menu **Arquivo** , aponte para **Novo**e clique em **Arquivo**.  
  
3. No painel **modelos** , clique em **arquivo XML** e, em seguida, clique em **abrir**.  
  
4. No menu **Exibir** , clique em **janela de propriedades** para exibir as propriedades do arquivo XML.  
  
5. Na janela **Propriedades** , clique no botão procurar (...) na propriedade esquemas.  
  
6. Na lista de esquemas XSD, selecione o esquema vsct. xsd. Se não estiver na lista, clique em **Adicionar** e localize o arquivo em uma unidade local. Clique em **OK** quando terminar.  
  
7. No arquivo XML, digite `<CommandTable` e pressione Tab. Feche a marca digitando `>` .  
  
     Isso cria um arquivo. vsct básico.  
  
8. Preencha os elementos do arquivo XML que você deseja adicionar, de acordo com o [esquema vsct](../../extensibility/vsct-xml-schema-reference.md). Para obter mais informações, consulte [criação. Arquivos vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Simplesmente adicionar um arquivo. vsct a um projeto não faz com que ele seja compilado. Você deve incorporá-lo no processo de compilação.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para adicionar um arquivo. vsct à compilação do projeto  
  
1. Abra o arquivo de projeto no editor. Se o projeto for carregado, você deverá descarregá-lo primeiro.  
  
2. Adicione um [elemento do grupo](../../msbuild/itemgroup-element-msbuild.md) de itens que contém um elemento VSCTCompile, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     O elemento resourceName sempre deve ser definido como `Menus.ctmenu` .  
  
3. Se o seu projeto contiver um arquivo. resx, adicione um elemento EmbeddedResource que contém um elemento MergeWithCTO, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Essa marcação deve estar dentro do elemento rowgroup que contém recursos incorporados.  
  
4. Abra o arquivo de pacote, normalmente chamado de *projectname*Package.cs ou *ProjectName*Package. vb, no editor.  
  
5. Adicione um atributo ProvideMenuResource à classe de pacote, conforme mostrado no exemplo a seguir.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     O primeiro valor do parâmetro deve corresponder ao valor do atributo resourceName que você definiu no arquivo de projeto.  
  
## <a name="see-also"></a>Consulte Também  
 [Criação. Arquivos vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabela de comandos do Visual Studio (. Arquivos de vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Como: criar um. Arquivo vsct de um existente. Arquivo CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Como: criar um. Arquivo vsct de um existente. Arquivo CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Referência do esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)
