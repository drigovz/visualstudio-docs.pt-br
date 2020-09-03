---
title: Criando sua própria página inicial | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: jillfra
ms.openlocfilehash: fba7f1e0801b6f977d47b13af025538f5d2fe031
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850987"
---
# <a name="creating-your-own-start-page"></a>Criando sua própria página inicial
Você pode criar uma página inicial personalizada usando o modelo de projeto página inicial ou criando uma página inicial em branco.  
  
 O designer XAML pode não fornecer representações visuais totalmente precisas de páginas iniciais personalizadas devido a dependências no modelo de aplicativo do Visual Studio.  
  
## <a name="using-the-project-template"></a>Usando o modelo de projeto  
 O modelo de projeto página inicial cria um projeto de página inicial que é uma cópia completa da página inicial do Visual Studio. Em seguida, você pode editar a página inicial para suas especificações.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Para criar uma página inicial personalizada usando o modelo de projeto de página inicial  
  
1. Baixe e instale o [modelo de projeto página inicial](https://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) da galeria do Visual Studio.  
  
    > [!WARNING]
    > Neste momento, o modelo de projeto página inicial do Visual Studio 2010 não foi atualizado. Para obter informações sobre como atualizar esse modelo, consulte [como: atualizar uma página inicial personalizada do Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2. Depois de instalar o modelo, crie um novo projeto de página inicial com ele.  
  
3. No painel esquerdo da caixa de diálogo novo projeto, em **modelos instalados**, expanda o nó **outros tipos de projeto** e clique em **extensibilidade**.  
  
4. No painel central, clique em **página inicial personalizada**e, em seguida, nomeie o projeto e clique em **OK**.  
  
     O Visual Studio cria um projeto de página inicial que é uma cópia completa da página inicial do Visual Studio.  
  
5. Em **Gerenciador de soluções**, abra **Startpage. XAML**.  
  
6. Edite StartPage. XAML.  
  
     Você pode exibir seu trabalho pressionando F5 para abrir uma instância experimental do Visual Studio com a página inicial personalizada instalada.  
  
## <a name="creating-a-blank-start-page"></a>Criando uma página inicial em branco  
 A maneira mais fácil de criar uma página inicial em branco é usar o modelo de projeto página inicial e, em seguida, remover o conteúdo.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Para criar uma página inicial em branco usando o modelo de projeto de página inicial  
  
1. Crie um projeto de página inicial usando o modelo de projeto de página inicial, conforme descrito no procedimento anterior.  
  
2. Abra StartPage. XAML.  
  
3. Remova todo o conteúdo da página, deixando apenas os elementos XML externos e o elemento de grade que o contém <xref:System.Windows.Controls.Grid> , para que o arquivo. XAML seja semelhante ao exemplo a seguir.  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. Remova os arquivos de suporte que você não pretende usar.  
  
    Você deve manter os arquivos. vsix e. pkgdef para fins de implantação.  
  
   Como alternativa, você pode criar uma página inicial em branco criando um arquivo XAML com a estrutura de marca correta a ser reconhecida pelo Visual Studio. Em seguida, você pode adicionar marcação e code-behind para obter a aparência e a funcionalidade desejadas. Para obter mais informações, consulte [criando uma página inicial personalizada](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testando e aplicando a página inicial personalizada  
 Não defina a instância primária para executar a página de início personalizada até verificar se ela não falha. Quando você tiver testado a página inicial personalizada, poderá aplicá-la ao seu sistema repetindo as três últimas etapas deste procedimento na instância primária do Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Para testar uma página inicial personalizada  
  
1. Pressione F5.  
  
    A instância experimental do Visual Studio é aberta com a nova página inicial instalada, mas não selecionada.  
  
2. Na instância experimental do Visual Studio, no menu **ferramentas** , clique em **Opções**.  
  
3. Na caixa de diálogo **Opções** , em **ambiente**, selecione **inicialização**. Em seguida, na lista **Personalizar página inicial** , selecione o arquivo. XAML e clique em **OK**.  
  
4. No menu **Exibir** , clique em **página inicial**.  
  
    A página de início de trabalho é exibida. Você deve fechar a instância experimental, copiar novamente todos os arquivos alterados e, em seguida, abrir novamente a instância experimental para ver novas alterações.  
  
   Você pode compartilhar sua página inicial personalizada carregando o arquivo. vsix do diretório bin\Debug para o site [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou para outro site ou compartilhamento de intranet. Para obter mais informações, consulte [implantando páginas iniciais personalizadas](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Personalizando a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Adicionar XAML personalizado à página inicial](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
