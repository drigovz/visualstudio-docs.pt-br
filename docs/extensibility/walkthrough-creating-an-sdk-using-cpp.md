---
title: 'Passo a passo: Criando um SDK usando C++ | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697630"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Passo a passo: Crie um SDK usando C++
Este passo a passo mostra como criar uma biblioteca de matemática C++ nativa SDK, empacotar o SDK como uma Extensão visual studio (VSIX) e, em seguida, usá-lo para criar um aplicativo. O passo a passo é dividido em estas etapas:

- [Para criar as bibliotecas nativas e do Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Para criar o projeto de extensão NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Para criar um aplicativo de exemplo que usa a biblioteca de classes](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Pré-requisitos
 Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Para criar as bibliotecas nativas e do Windows Runtime

1. Na barra de menu, escolha **Arquivo** > **Novo** > **Projeto**.

2. Na lista de modelos, expanda o **Visual C++** > **Windows Universal**e selecione o modelo **DLL (aplicativos Do Windows Universal).** Na caixa **Nome,** especifique `NativeMath`e escolha o botão **OK.**

3. Atualize *NativeMath.h* para corresponder ao seguinte código.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Atualize *NativeMath.cpp* para corresponder a este código:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. No **Solution Explorer,** abra o menu de atalho **para 'NativeMath' e**escolha **Adicionar** > **novo projeto**.

6. Na lista de modelos, expanda **o Visual C++** e selecione o modelo **componente de tempo de execução do Windows.** Na caixa **Nome,** especifique `NativeMathWRT`e escolha o botão **OK.**

7. Atualize *o Class1.h* para corresponder a este código:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Atualize *o Class1.cpp* para corresponder a este código:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Na barra de menu, escolha **Build** > **Build Solution**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Para criar o projeto de extensão NativeMathVSIX

1. No **Solution Explorer,** abra o menu de atalho **para 'NativeMath' e**escolha **Adicionar** > **novo projeto**.

2. Na lista de modelos, expanda a**Extensibilidade** **Visual C#** > e selecione **o Projeto VSIX**. Na caixa **Nome,** especifique **NativeMathVSIX**e escolha o botão **OK.**

3. No **Solution Explorer,** abra o menu de atalho para **source.extension.vsixmanifest**e, em seguida, escolha **'Código de exibição '''''**

4. Use o XML a seguir para substituir o XML existente.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. No **Solution Explorer,** abra o menu de atalho para o projeto **NativeMathVSIX** e, em seguida, escolha **Adicionar** > **novo item**.

6. Na lista de **itens Visuais C#**, expanda **dados**e selecione **Arquivo XML**. Na caixa **Nome,** especifique `SDKManifest.xml`e escolha o botão **OK.**

7. Use este XML para substituir o conteúdo do arquivo:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. No **Solution Explorer**, no projeto **NativeMathVSIX,** crie essa estrutura de pasta:

    ```xml
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

9. No **Solution Explorer,** abra o menu de atalho **para 'NativeMath' e**escolha **'Abrir pasta no File Explorer**' .

10. No **Explorador de Arquivos,** copie *$SolutionRoot$\NativeMath\NativeMath.h*e, em seguida, no **Solution Explorer**, no projeto **NativeMathVSIX,** cole-o na *pasta $SolutionRoot$\NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include.\\ *

     Copie *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*e cole-o na pasta *\\ $SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86.*

     Copie *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* e cole-o na pasta *\\ $SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.*

     Copie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* e cole-o na pasta *$SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.*
     Copie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* e cole-o na *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral* folder.

     Copie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* e cole-o na *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral* folder.

11. Na pasta *$SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86,\\ * crie um arquivo de texto chamado *NativeMathSDK.props*e cole os seguintes conteúdos nele:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Na barra de menus, escolha **Exibir** > **outras** > propriedades do**Windows (Teclado:** Escolha a tecla **F4).**

13. No **Solution Explorer,** selecione o arquivo **NativeMathWRT.winmd.** Na janela **Propriedades,** altere a propriedade **Build Action** para **Conteúdo**e altere a propriedade Incluir na propriedade **VSIX** para **True**.

     Repita este processo para o arquivo **NativeMath.h.**

     Repita este processo para o arquivo **NativeMathWRT.pri.**

     Repita este processo para o arquivo **NativeMath.Lib.**

     Repita este processo para o arquivo **NativeMathSDK.props.**

14. No **Solution Explorer,** selecione o arquivo **NativeMath.h.** Na janela **Propriedades,** altere a **propriedade Incluir em VSIX** para **True**.

     Repita este processo para o arquivo **NativeMath.dll.**

     Repita este processo para o arquivo **NativeMathWRT.dll.**

     Repita este processo para o arquivo **SDKManifest.xml.**

15. Na barra de menu, escolha **Build** > **Build Solution**.

16. No **Solution Explorer,** abra o menu de atalho para o projeto **NativeMathVSIX** e, em seguida, escolha **Abrir pasta no Explorador de arquivos**.

17. No **File Explorer,** navegue até a pasta *$SolutionRoot$\NativeMathVSIX\bin\Debug* e execute *NativeMathVSIX.vsix* para iniciar a instalação.

18. Escolha o botão **Instalar,** aguarde o término da instalação e abra o Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Para criar um aplicativo de exemplo que usa a biblioteca de classes

1. Na barra de menu, escolha **Arquivo** > **Novo** > **Projeto**.

2. Na lista de modelos, expanda o **Visual C++** > **Windows Universal** e selecione Blank **App**. Na caixa **Nome,** especifique **NativeMathSDKSample**e escolha o botão **OK.**

3. No **Solution Explorer,** abra o menu de atalho para o projeto **NativeMathSDKSample** e, em seguida, escolha **Adicionar** > **referência**.

4. Na caixa de diálogo **Adicionar referência,** na lista de tipos de referência, expanda o **Universal Windows**e selecione **Extensões**. Por fim, selecione a caixa de seleção **Nativa Matemática SDK** e escolha o botão **OK.**

5. Exibir as propriedades do projeto para NativeMathSDKSample.

    As propriedades que você definiu em *NativeMathSDK.props* foram aplicadas quando você adicionou a referência. Você pode verificar se as propriedades foram aplicadas examinando a propriedade **VC++ Directories** das Propriedades de **Configuração**do projeto.

6. No **Solution Explorer,** abra **mainpage.xaml**e use o seguinte XAML para substituir seu conteúdo:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Atualize *mainpage.xaml.h* para corresponder a este código:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Atualize *mainpage.xaml.cpp* para corresponder a este código:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Escolha a chave **F5** para executar o aplicativo.

10. No aplicativo, digite dois números, selecione uma **=** operação e escolha o botão.

     O resultado correto aparece.

    Este passo a passo mostrou como criar e usar [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] um SDK[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] de extensão para chamar em uma biblioteca e uma não-biblioteca.

## <a name="next-steps"></a>Próximas etapas

## <a name="see-also"></a>Confira também
- [Passo a passo: Crie um SDK usando C# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Crie um kit de desenvolvimento de software](../extensibility/creating-a-software-development-kit.md)
