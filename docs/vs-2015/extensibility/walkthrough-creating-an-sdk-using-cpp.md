---
title: 'Walkthrough: Criando um SDK usando C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202065"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Passo a passo: criando um SDK usando C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial mostra como criar um SDK de biblioteca matemática C++ nativo, empacotar o SDK como um VSIX (extensão do Visual Studio) e, em seguida, usá-lo para criar um aplicativo. O passo a passo é dividido nestas etapas:  
  
- [Para criar as bibliotecas de Windows Runtime e nativas](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Para criar o projeto de extensão NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Para criar um aplicativo de exemplo que usa a biblioteca de classes](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passos, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Para criar as bibliotecas de Windows Runtime e nativas  
  
1. Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2. Na lista de modelos, expanda **Visual C++**, **Windows Store**e, em seguida, selecione o modelo **dll (aplicativos da Windows Store)** . Na caixa **nome** , especifique `NativeMath` e, em seguida, escolha o botão **OK** .  
  
3. Atualize NativeMath. h para corresponder ao código a seguir.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Atualize NativeMath. cpp para corresponder a este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. No **Gerenciador de soluções**, abra o menu de atalho da **solução ' NativeMath '** e escolha **Adicionar**, **novo projeto**.  
  
6. Na lista de modelos, expanda **Visual C++** e, em seguida, selecione o modelo de **componente de Windows Runtime** . Na caixa **nome** , especifique `NativeMathWRT` e, em seguida, escolha o botão **OK** .  
  
7. Atualize Class1. h para corresponder a este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Atualize Class1. cpp para corresponder a este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Para criar o projeto de extensão NativeMathVSIX  
  
1. No **Gerenciador de soluções**, abra o menu de atalho da **solução ' NativeMath '** e escolha **Adicionar**, **novo projeto**.  
  
2. Na lista de modelos, expanda **Visual C#**, **extensibilidade**e, em seguida, selecione **pacote VSIX**. Na caixa **nome** , especifique **NativeMathVSIX**e, em seguida, escolha o botão **OK** .  
  
3. Quando o designer de manifesto do VSIX aparecer, feche-o.  
  
4. No **Gerenciador de soluções**, abra o menu de atalho para **Source. Extension. vsixmanifest**e escolha **Exibir código**.  
  
5. Use o XML a seguir para substituir o XML existente.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. No **Gerenciador de soluções**, abra o menu de atalho para o projeto **NativeMathVSIX** e, em seguida, escolha **Adicionar**, **novo item**.  
  
7. Na lista de **itens do Visual C#**, expanda **dados**e, em seguida, selecione **arquivo XML**. Na caixa **nome** , especifique `SDKManifest.xml` e, em seguida, escolha o botão **OK** .  
  
8. Use esse XML para substituir o conteúdo do arquivo:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. No **Gerenciador de soluções**, no projeto **NativeMathVSIX** , crie esta estrutura de pastas:  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. No **Gerenciador de soluções**, abra o menu de atalho da **solução ' NativeMath '** e, em seguida, escolha **abrir pasta no explorador de arquivos**.  
  
11. No **Explorador de arquivos**, copie \NativeMath\NativeMath.h e, em **Gerenciador de soluções**, no projeto **NativeMathVSIX** , Cole-o na pasta \DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Copie \Debug\NativeMath\NativeMath.lib e cole-o na pasta \DesignTime\Debug\x86\.  
  
     Copie \Debug\NativeMath\NativeMath.dll e cole-o na pasta \Redist\Debug\x86\  
  
     Copie DebugNativeMathWRTNativeMathWRT.dll e cole-o na pasta RedistDebugx86  
  
     Copie DebugNativeMathWRTNativeMathWRT. winmd e cole-o na pasta ReferencesCommonConfigurationNeutral.  
  
     Copie DebugNativeMathWRTNativeMathWRT. pri e cole-o na pasta ReferencesCommonConfigurationNeutral.  
  
12. Na pasta \DesignTime\Debug\x86\, crie um arquivo de texto chamado NativeMathSDK. props e cole o seguinte conteúdo nele:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Na barra de menus, escolha **Exibir**, **outras janelas**, **janela Propriedades** (teclado: escolha a tecla F4).  
  
14. Em **Gerenciador de soluções**, selecione o arquivo **NativeMathWRT. winmd** . Na janela **Propriedades** , altere a propriedade **ação de compilação** para **conteúdo**e, em seguida, altere a propriedade **incluir na VSIX** para **true**.  
  
     Repita esse processo para o arquivo **SimpleMath. pri** .  
  
     Repita esse processo para o arquivo **NativeMath. lib** .  
  
     Repita esse processo para o arquivo **NativeMathSDK. props** .  
  
15. Em **Gerenciador de soluções**, selecione o arquivo **NativeMath. h** . Na janela **Propriedades** , altere a propriedade **include in VSIX** para **true**.  
  
     Repita esse processo para o arquivo de **NativeMath.dll** .  
  
     Repita esse processo para o arquivo de **NativeMathWRT.dll** .  
  
     Repita esse processo para o arquivo de **SDKManifest.xml** .  
  
16. Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
17. No **Gerenciador de soluções**, abra o menu de atalho para o projeto **NativeMathVSIX** e, em seguida, escolha **abrir pasta no explorador de arquivos**.  
  
18. No **Explorador de arquivos**, navegue até a pasta \bin\Debug\ e execute NativeMathVSIX. vsix para iniciar a instalação.  
  
19. Escolha o botão **instalar** , aguarde a conclusão da instalação e reinicie o Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Para criar um aplicativo de exemplo que usa a biblioteca de classes  
  
1. Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2. Na lista de modelos, expanda **Visual C++**, **Windows Store**e, em seguida, selecione **aplicativo em branco**. Na caixa **nome** , especifique **NativeMathSDKSample**e, em seguida, escolha o botão **OK** .  
  
3. No **Gerenciador de soluções**, abra o menu de atalho para o projeto **NativeMathSDKSample** e, em seguida, escolha **Adicionar**, **referência**.  
  
4. Na página **Propriedades comuns**, **estrutura e referências** , na lista de tipos de referência, expanda **Windows**e selecione **extensões**. No painel de detalhes, selecione a extensão **SDK do Math nativo** e, em seguida, escolha o botão **Adicionar nova referência** .  
  
5. Na caixa de diálogo **Adicionar referência** , marque a caixa de seleção **SDK de matemática nativa** e escolha o botão **OK** .  
  
6. Exiba as propriedades do projeto para NativeMathSDKSample.  
  
    As propriedades que você definiu em NativeMathSDK. props foram aplicadas quando você adicionou a referência. Você pode verificar isso examinando a propriedade **diretórios do vc + +** das propriedades de **configuração**do projeto.  
  
7. No **Gerenciador de soluções**, Abra MainPage. XAML e, em seguida, use o XAML a seguir para substituir seu conteúdo:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Atualize MainPage. XAML. h para corresponder a este código:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Atualize MainPage. XAML. cpp para corresponder a este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Escolha a tecla F5 para executar o aplicativo.  
  
11. No aplicativo, insira dois números, selecione uma operação e, em seguida, escolha o **=** botão.  
  
     O resultado correto é exibido.  
  
    Este tutorial mostrou como criar e usar um SDK de extensão para chamar uma [!INCLUDE[wrt](../includes/wrt-md.md)] biblioteca e uma não [!INCLUDE[wrt](../includes/wrt-md.md)] biblioteca.  
  
## <a name="next-steps"></a>Próximas etapas  
  
## <a name="see-also"></a>Consulte Também  
 [Walkthrough: Criando um SDK usando C# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Criar um Software Development Kit](../extensibility/creating-a-software-development-kit.md)
