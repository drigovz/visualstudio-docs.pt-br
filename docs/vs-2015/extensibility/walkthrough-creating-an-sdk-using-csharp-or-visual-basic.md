---
title: 'Walkthrough: Criando um SDK usando C# ou Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558211"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Passo a passo: criando um SDK usando C# ou Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Neste tutorial, você aprenderá a criar um SDK de biblioteca de matemática simples usando o Visual C# e, em seguida, empacotará o SDK como uma extensão do Visual Studio (VSIX). Você concluirá os seguintes procedimentos:  
  
- [Para criar o componente de Windows Runtime SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [Para criar o projeto de extensão SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [Para criar um aplicativo de exemplo que usa a biblioteca de classes](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passos, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="createClassLibrary"></a>Para criar o componente de Windows Runtime SimpleMath  
  
1. Na barra de menus, escolha **arquivo**, **novo**, **novo projeto**.  
  
2. Na lista de modelos, expanda **Visual C#**  ou **Visual Basic**, escolha o nó **Windows Store** e, em seguida, escolha o modelo de **componente de Windows Runtime** .  
  
3. Na caixa **nome** , especifique **SimpleMath**e, em seguida, escolha o botão **OK** .  
  
4. No **Gerenciador de soluções**, abra o menu de atalho para o nó do projeto **SimpleMath** e escolha **Propriedades**.  
  
5. Renomeie **Class1.cs** para **Arithmetic.cs** e atualize-o para corresponder ao seguinte código:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. No **Gerenciador de soluções**, abra o menu de atalho do nó da **solução ' SimpleMath '** e escolha **Configuration Manager**.  
  
     A caixa de diálogo **Configuration Manager** é aberta.  
  
7. Na lista **configuração de solução ativa** , escolha **liberar**.  
  
8. Na coluna **configuração** , verifique se **SimpleMath** linha está definida como **liberar**e, em seguida, escolha o botão **fechar** para aceitar a alteração.  
  
    > [!IMPORTANT]
    > O SDK para o componente SimpleMath inclui apenas uma configuração. Essa configuração deve ser a compilação de versão ou os aplicativos que usam o componente não passarão na certificação para o[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. No **Gerenciador de soluções**, abra o menu de atalho para o nó do projeto **SimpleMath** e escolha **Compilar**.  
  
## <a name="createVSIX"></a>Para criar o projeto de extensão SimpleMathVSIX  
  
1. No menu de atalho do nó da **solução ' SimpleMath '** , escolha **Adicionar**, **novo projeto**.  
  
2. Na lista de modelos, expanda **Visual C#**  ou **Visual Basic**, escolha o nó **extensibilidade** e, em seguida, escolha o modelo de **projeto VSIX** .  
  
3. Na caixa **nome** , especifique **SimpleMathVSIX**e, em seguida, escolha o botão **OK** .  
  
4. Em **Gerenciador de soluções**, escolha o item **origem. extensão. vsixmanifest** .  
  
5. Na barra de menus, escolha **Exibir**, **Código**.  
  
6. Substitua o XML existente pelo seguinte XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. Em **Gerenciador de soluções**, escolha o projeto **SimpleMathVSIX** .  
  
8. Na barra de menus, escolha **projeto**, **Adicionar novo item**.  
  
9. Na lista de **itens comuns**, expanda **dados**e, em seguida, escolha **arquivo XML**.  
  
10. Na caixa **nome** , especifique `SDKManifest.xml`e, em seguida, escolha o botão **Adicionar** .  
  
11. No **Gerenciador de soluções**, abra o menu de atalho para `SDKManifest.xml`, escolha **Propriedades**e, em seguida, altere o valor da propriedade **include in VSIX** para **true**.  
  
12. Substitua o conteúdo do arquivo pelo XML a seguir:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. No **Gerenciador de soluções**, abra o menu de atalho para o projeto **SimpleMathVSIX** , escolha **Adicionar**e, em seguida, escolha **nova pasta**.  
  
14. Renomeie a pasta para `references`.  
  
15. Abra o menu de atalho para a pasta **referências** , escolha **Adicionar**e, em seguida, escolha **nova pasta**.  
  
16. Renomeie a subpasta para `commonconfiguration`, crie uma subpasta dentro dela e nomeie a subpasta `neutral`.  
  
17. Repita as quatro etapas anteriores, desta vez renomeando a primeira pasta para `redist`.  
  
     O projeto agora contém a seguinte estrutura de pastas:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. No **Gerenciador de soluções**, abra o menu de atalho para o projeto **SimpleMath** e, em seguida, escolha **abrir pasta no explorador de arquivos**.  
  
19. No **Explorador de arquivos**, navegue até a pasta bin\Release, abra o menu de atalho do arquivo SimpleMath. winmd e, em seguida, escolha **copiar**.  
  
20. Em **Gerenciador de soluções**, Cole o arquivo na pasta references\commonconfiguration\neutral no projeto **SimpleMathVSIX** .  
  
21. Repita a etapa anterior, colando o arquivo SimpleMath. pri na pasta redist\commonconfiguration\neutral do projeto **SimpleMathVSIX** .  
  
22. Em **Gerenciador de soluções**, escolha **SimpleMath. winmd**.  
  
23. Na barra de menus, escolha **Exibir**, **Propriedades** (teclado: escolha a tecla F4).  
  
24. Na janela **Propriedades** , altere a propriedade **ação de compilação** para **conteúdo**e, em seguida, altere a propriedade **incluir na VSIX** para **true**.  
  
25. Em **Gerenciador de soluções**, repita esse processo para **SimpleMath. pri**.  
  
26. Em **Gerenciador de soluções**, escolha o projeto **SimpleMathVSIX** .  
  
27. Na barra de menus, escolha **Compilar**, **criar SimpleMathVSIX**.  
  
28. No **Gerenciador de soluções**, abra o menu de atalho para o projeto **SimpleMathVSIX** e, em seguida, escolha **abrir pasta no explorador de arquivos**.  
  
29. No **Explorador de arquivos**, navegue até a pasta \bin\release e execute SimpleMathVSIX. vsix para instalá-lo.  
  
30. Escolha o botão **instalar** , aguarde a conclusão da instalação e reinicie o Visual Studio.  
  
## <a name="createSample"></a>Para criar um aplicativo de exemplo que usa a biblioteca de classes  
  
1. Na barra de menus, escolha **arquivo**, **novo**, **novo projeto**.  
  
2. Na lista de modelos, expanda **Visual C#**  ou **Visual Basic**e, em seguida, escolha o nó **Windows Store** .  
  
3. Escolha o modelo de **aplicativo em branco** , nomeie o projeto **ArithmeticUI**e escolha o botão **OK** .  
  
4. No **Gerenciador de soluções**, abra o menu de atalho para o projeto **ArithmeticUI** e, em seguida, escolha **Adicionar**, **referência**.  
  
5. Na lista de tipos de referência, expanda **Windows**e, em seguida, escolha **extensões**.  
  
6. No painel de detalhes, escolha a extensão do **SDK de matemática simples** .  
  
    Informações adicionais sobre o SDK são exibidas. Você pode escolher o link **mais informações** para abrir https://docs.microsoft.com, como você especificou no arquivo SDKManifest. XML anteriormente neste guia.  
  
7. Na caixa de diálogo **Gerenciador de referências** , marque a caixa de seleção **SDK de matemática simples** e escolha o botão **OK** .  
  
8. Na barra de menus, escolha **Exibir**, **pesquisador de objetos**.  
  
9. Na lista **procurar** , escolha **matemática simples**.  
  
     Agora você pode explorar o que está no SDK.  
  
10. No **Gerenciador de soluções**, Abra MainPage. XAML e substitua seu conteúdo pelo XAML a seguir:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Atualize MainPage.xaml.cs para corresponder ao seguinte código:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Escolha a tecla F5 para executar o aplicativo.  
  
13. No aplicativo, insira dois números, escolha uma operação e, em seguida, escolha o botão **=** .  
  
     O resultado correto é exibido.  
  
    Você criou e usou com êxito um SDK de extensão.  
  
## <a name="see-also"></a>Veja também  
 [Walkthrough: Criando um SDK usando C++ o](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Walkthrough: Criando um SDK usando JavaScript](walkthrough-creating-an-sdk-using-javascript.md)   
 [Criar um Software Development Kit](../extensibility/creating-a-software-development-kit.md)
