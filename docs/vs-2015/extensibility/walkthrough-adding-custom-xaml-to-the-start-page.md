---
title: 'Walkthrough: adicionando XAML personalizado à página inicial | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b2de492bd1eddf4bf18e4824cdb64de4241fa5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674118"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Passo a passo: adicionando XAML personalizado à página inicial
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial mostra como criar uma página inicial personalizada do Visual Studio que contém um navegador da Web.  
  
## <a name="adding-custom-xaml"></a>Adicionando XAML personalizado  
  
1. Crie uma página inicial seguindo as instruções em [criando uma página inicial personalizada](../extensibility/creating-a-custom-start-page.md).  
  
2. No arquivo MainWindow. XAML, localize a \<Grid> seção.  
  
3. Adicione um \<TabControl> elemento e um \<TabItem> dentro do \< Grid> elemento, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4. Adicione um segundo \<TabItem> , com um \<Button> elemento que abre um novo projeto:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Testando a página inicial personalizada  
  
1. Pressione F5.  
  
     A instância experimental do Visual Studio é aberta, com a página inicial personalizada instalada, mas não selecionada.  
  
2. Na instância experimental do Visual Studio, abra a página **ferramentas/opts/Environment** .  
  
3. Selecione **inicialização**. Na lista **Personalizar página inicial** , selecione o arquivo. XAML e clique em **OK**.  
  
4. No menu **Exibir** , clique em **página inicial**.  
  
5. Clique na guia **Bing** .  
  
     Você deve ver uma página da Web do Bing.  
  
6. Clique na guia **MyButton** .  
  
     Você deve ver um botão **MyProject** , que abre a caixa de diálogo **novo projeto** .  
  
7. Feche a instância experimental.  
  
## <a name="applying-the-custom-start-page"></a>Aplicando a página inicial personalizada  
  
#### <a name="to-test-the-custom-start-page"></a>Para testar a página inicial personalizada  
  
1. Em **ferramentas/opções/ambiente**, selecione **inicialização**. Na lista **Personalizar página inicial** , selecione o arquivo. XAML e clique em **OK**.  
  
## <a name="next-steps"></a>Próximas etapas  
 A página inicial do Visual Studio agora contém uma guia que exibe uma guia de navegador da Web e uma guia MyButton. Você pode criar páginas iniciais personalizadas que têm outras funcionalidades usando o modelo *code-behind* para adicionar um. dll personalizado, conforme mostrado em [adicionando controle de usuário à página inicial](../extensibility/adding-user-control-to-the-start-page.md). Você pode compartilhar páginas iniciais personalizadas com outros usuários publicando o arquivo. vsix resultante no site da [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou em outro compartilhamento de rede ou site da Web. Para obter mais informações, consulte [implantando páginas iniciais personalizadas](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Personalizando a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controles de contêiner do WPF](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)
