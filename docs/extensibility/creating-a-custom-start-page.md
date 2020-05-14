---
title: Criando uma página inicial personalizada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739634"
---
# <a name="creating-a-custom-start-page"></a>Criando uma página inicial personalizada

Você pode criar uma página inicial personalizada seguindo as etapas deste documento.

## <a name="create-a-blank-start-page"></a>Criar uma página inicial em branco

Primeiro, faça uma página inicial em branco criando um arquivo *.xaml* que tenha uma estrutura de tag que o Visual Studio reconhecerá. Em seguida, adicione marcação e código para produzir a aparência e funcionalidade desejada.

1. Crie um novo projeto do tipo **WPF Application** **(Visual C#** > **Windows Desktop).**

2. Adicione uma `Microsoft.VisualStudio.Shell.14.0`referência a .

3. Abra o arquivo XAML no editor XML \<e altere \<o elemento> janela de nível superior para um elemento> UserControl sem remover nenhuma das declarações de namespace.

4. Remova `x:Class` a declaração do elemento de nível superior. Isso torna o conteúdo XAML compatível com a janela de ferramentas do Visual Studio que hospeda a Página Inicial.

5. Adicione as seguintes declarações de \<namespace ao elemento de> de controle de usuário de nível superior.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Esses namespaces permitem que você acesse os comandos, controles e configurações de IA do Visual Studio. Para obter mais informações, consulte [Adicionar comandos do Visual Studio a uma página inicial](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     O exemplo a seguir mostra a marcação no arquivo *.xaml* para uma página inicial em branco. Qualquer conteúdo personalizado deve <xref:System.Windows.Controls.Grid> ir para o elemento interno.

    ```vb
    <UserControl
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        xmlns:local="clr-namespace:StartPageHost"
        mc:Ignorable="d"
         Height="350" Width="525">
        <Grid>
        <!--Add content here.-->
        </Grid>
    </UserControl>
    ```

6. Adicione controles ao \<elemento vazio UserControl> para preencher sua Página inicial personalizada. Para obter informações sobre como adicionar funcionalidades específicas ao Visual Studio, consulte [Adicionar comandos do Visual Studio a uma página inicial](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Teste e aplique a página inicial personalizada

Não defina a instância principal do Visual Studio para executar a página inicial personalizada até verificar se ela não trava o Visual Studio. Em vez disso, teste-o na instância experimental.

### <a name="to-test-a-manually-created-custom-start-page"></a>Para testar uma página inicial personalizada criada manualmente

1. Copie seu arquivo XAML e quaisquer arquivos de texto ou arquivos de marcação de suporte para a pasta *%USERPROFILE%\Meus Documentos\Visual Studio 2015\StartPages.\\ *

2. Se a página inicial fizer referência a quaisquer controles ou tipos em conjuntos que não estejam instalados pelo Visual Studio, copie os conjuntos e cole-os em *{Pasta de instalação do Visual Studio}\Common7\IDE\PrivateAssemblies\\*.

3. Em um prompt de comando do Visual Studio, **digite devenv /rootsufix Exp** para abrir uma instância experimental do Visual Studio.

4. Na instância experimental, vá para a página**Iniciar** o**Ambiente** > **de Opções** >  **de Ferramentas** > e selecione seu arquivo XAML a partir da **lista inicialização** da página inicial.

5. No menu **Exibir,** clique **em Iniciar página**.

     Sua página inicial personalizada deve ser exibida. Se você quiser alterar qualquer arquivo, você deve fechar a instância experimental, fazer as alterações, copiar e colar os arquivos alterados e, em seguida, reabrir a instância experimental para visualizar as alterações.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Para aplicar a página inicial personalizada na instância primária do Visual Studio

- Depois de testar sua Página Inicial e encontrá-la estável, use a opção **Personalizar página inicial** na caixa de diálogo **Opções** para selecioná-la como a página inicial na instância principal do Visual Studio

## <a name="see-also"></a>Confira também

- [Passo a passo: Adicione XAML personalizado à página inicial](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Adicione o controle do usuário à página inicial](../extensibility/adding-user-control-to-the-start-page.md)
- [Adicionar comandos do Visual Studio a uma página inicial](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Passo a passo: Salve as configurações do usuário em uma página inicial](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Implantar páginas iniciais personalizadas](../extensibility/deploying-custom-start-pages.md)
