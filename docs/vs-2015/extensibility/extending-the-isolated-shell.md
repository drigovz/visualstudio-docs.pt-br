---
title: Estendendo o Shell isolado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838416"
---
# <a name="extending-the-isolated-shell"></a>Estender o Shell isolado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode estender o Shell isolado do Visual Studio adicionando um VSPackage, uma parte de componente Managed Extensibility Framework (MEF) ou um projeto VSIX genérico ao seu aplicativo de shell isolado.  
  
> [!NOTE]
> As etapas a seguir pressupõem que você criou um aplicativo de shell isolado básico usando o modelo de projeto isolado do shell do Visual Studio. Para obter mais informações sobre este modelo de projeto, consulte [passo a passos: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Locais para o modelo de projeto de pacote do Visual Studio  
 O modelo de projeto de pacote do Visual Studio pode ser encontrado em três locais diferentes na caixa de diálogo **novo projeto** :  
  
1. Em **Visual Basic**, **extensibilidade**. O idioma padrão do projeto é Visual Basic.  
  
2. Em **Visual C#**, **extensibilidade**. O idioma padrão do projeto é C#.  
  
3. Em **outros tipos de projeto**, **extensibilidade**. O idioma padrão do projeto é C++.  
  
## <a name="adding-a-vspackage"></a>Adicionando um VSPackage  
 Você pode adicionar um VSPackage ao seu aplicativo de shell isolado. As etapas a seguir mostram como criar um que adiciona comandos de menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Para adicionar um novo VSPackage  
  
1. Adicione um projeto de pacote do Visual Studio chamado `MenuCommandsPackage` .  
  
2. Na página **informações básicas do VSPackage** do assistente, defina **nome da empresa** como `Fabrikam` e **nome do VSPackage** como `FabrikamMenuCommands` . Escolha o botão **Avançar**.  
  
3. Na próxima página, selecione **comando de menu** e, em seguida, escolha **Avançar**.  
  
4. Na página seguinte, defina o **nome do comando** como `Fabrikam Command` e a **ID de comando** para e `cmdidFabrikamCommand` escolha **Avançar**.  
  
5. Na página **selecionar opções do projeto de teste** , desmarque as opções de teste e, em seguida, escolha o botão **concluir** .  
  
6. No projeto ShellExtensionsVSIX, abra o arquivo Source. Extension. vsixmanifest.  
  
     A seção de **ativos** deve conter uma entrada para o projeto VSShellStub. AboutBoxPackage.  
  
7. Escolha o botão **novo** .  
  
8. Na janela **Adicionar novo ativo** , na lista **tipo** , selecione **Microsoft. VisualStudio. VSPackage**.  
  
9. Na lista **origem** , verifique se **um projeto na solução atual** está selecionado. Na caixa de listagem **projeto** , selecione **MenuCommandsPackage**.  
  
10. Salve e feche o arquivo.  
  
11. Recompile a solução e inicie a depuração do Shell isolado.  
  
12. Na barra de menus, escolha o menu **ferramentas** e, em seguida, o **comando Fabrikam**.  
  
     Uma caixa de mensagem deve aparecer.  
  
13. Pare a depuração do aplicativo.  
  
## <a name="adding-a-mef-component-part"></a>Adicionando uma parte do componente do MEF  
 As etapas a seguir mostram como adicionar uma parte de componente do MEF ao seu aplicativo de shell isolado.  
  
#### <a name="to-add-a-mef-component"></a>Para adicionar um componente MEF  
  
1. Na caixa de diálogo **Adicionar novo projeto** , em **Visual C#**, **extensibilidade**, use o modelo de **margem do editor** para adicionar um projeto. Nomeie-o `ShellEditorMargin`.  
  
2. No projeto ShellExtensionsVSIX, abra o arquivo Source. Extension. vsixmanifest no modo de exibição de Design, não o modo de exibição de código.  
  
3. Na `Asset` seção, escolha **adicionar conteúdo**.  
  
4. Na janela **Adicionar novo ativo** , na lista **tipo** , selecione **Microsoft. VisualStudio. MefComponent**.  
  
5. Na lista **origem** , verifique se **um projeto na solução atual** está selecionado. Na caixa de listagem **projeto** , selecione **ShellEditorMargin**.  
  
6. Salve e feche o arquivo.  
  
7. Recompile a solução e inicie a depuração do Shell isolado.  
  
8. Abra um arquivo de texto.  
  
     Uma margem verde que contém as palavras "Olá, mundo!" deve ser exibido na parte inferior da janela de arquivo de texto.  
  
9. Pare a depuração do aplicativo.  
  
## <a name="adding-a-generic-vsix-project"></a>Adicionando um projeto VSIX genérico  
  
#### <a name="to-add-a-generic-vsix-project"></a>Para adicionar um projeto VSIX genérico  
  
1. Na caixa de diálogo **Adicionar novo projeto** , em **Visual C#**, **extensibilidade**, use o modelo **VSIXProject** para adicionar um projeto. Nomeie-o `EmptyVSIX`.  
  
2. No projeto ShellExtensionsVSIX, abra o arquivo Source. Extensions. vsixmanifest no modo de exibição de Design, não o modo de exibição de código.  
  
3. Na `Assets` seção, escolha **novo**.  
  
4. Na janela **Adicionar novo ativo** , na lista **tipo** , selecione o tipo de conteúdo que você deseja adicionar.  
  
5. Em **origem**, verifique se a opção **um projeto na solução atual** está selecionada. Na caixa de listagem, selecione o nome do seu projeto VSIX.  
  
6. Salve e feche o arquivo.  
  
7. Se esse projeto incluir código compilado, você deverá editar o projeto para que o assembly seja incluído na saída.  
  
    1. Descarregue o projeto VSIX e abra o arquivo de projeto.  
  
    2. No primeiro `<PropertyGroup>` bloco, altere o valor de `<CopyBuildOutputToOutputDirectory>` para `true` .  
  
    3. Salve e recarregue o projeto.  
  
8. Compile e execute a solução.  
  
## <a name="see-also"></a>Consulte Também  
 [Passo a passo: criar um aplicativo básico de Shell isolado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
