---
title: 'Passo a passo: Adicionando XAML personalizado à página inicial | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697690"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Passo a passo: Adicione XAML personalizado à página inicial

Este passo a passo mostra como criar uma página inicial personalizada do Visual Studio que contenha um navegador da Web.

## <a name="add-custom-xaml"></a>Adicionar XAML personalizado

1. Crie uma página inicial seguindo as instruções em [Criar uma página inicial personalizada](../extensibility/creating-a-custom-start-page.md).

2. No arquivo *MainWindow.xaml,* \<encontre a seção Grade>.

3. Adicione \<um elemento tabControl \<> e um \<> TabItem dentro do elemento> de Grade, como mostrado no exemplo a seguir.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Adicione um \<segundo> tabitem, com um \<elemento Button> que abre um novo projeto:

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

## <a name="test-the-custom-start-page"></a>Teste a página inicial personalizada

1. Pressione **F5**.

     A instância experimental do Visual Studio é aberta, com a página inicial personalizada instalada, mas não selecionada.

2. Na instância experimental do Visual Studio, abra a página **Ferramentas /Opções/ Meio Ambiente.**

3. Selecione **Inicialização**. Na lista **Personalizar página inicial,** selecione seu arquivo *.xaml* e clique em **OK**.

4. No menu **Exibir,** clique **em Iniciar página**.

5. Clique na aba **Bing.**

     Você deveria ver uma página do Bing.

6. Clique na guia **MyButton.**

     Você deve ver um botão **MyProject,** que abre a caixa de diálogo **Novo Projeto.**

7. Feche a instância experimental.

Para aplicar a página inicial personalizada, em Ambiente de**Opções de** > **Environment** **Ferramentas,** > selecione **Inicialização**. Na lista **Personalizar página inicial,** selecione seu arquivo *.xaml* e clique em **OK**.

## <a name="next-steps"></a>Próximas etapas

A página inicial do Visual Studio agora contém uma guia que exibe uma guia do navegador da Web e uma guia MyButton. Você pode criar páginas iniciais personalizadas que tenham outras funcionalidades usando o modelo *de código atrás* para adicionar um .dll personalizado, como mostrado em Adicionar controle de usuário à página [inicial](../extensibility/adding-user-control-to-the-start-page.md). Você pode compartilhar páginas iniciais personalizadas com outros usuários publicando o arquivo .vsix resultante no site do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou em outro site ou compartilhamento de rede. Para obter mais informações, consulte [Implantando páginas iniciais personalizadas](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Confira também

- [Personalize a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)
- [Controles de contêiner WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
