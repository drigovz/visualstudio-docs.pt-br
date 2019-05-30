---
title: 'Passo a passo: Adicionar XAML personalizado à página inicial | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 543faf9cf122e77cce6242f95008b777cd5666b2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322775"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Passo a passo: Adicionar XAML personalizado à página inicial

Este passo a passo mostra como criar uma página de início personalizada do Visual Studio que contém um navegador da Web.

## <a name="add-custom-xaml"></a>Adicionar XAML personalizado

1. Criar uma página inicial, seguindo as instruções em [criar uma página inicial personalizada](../extensibility/creating-a-custom-start-page.md).

2. No *MainWindow. XAML* do arquivo, localize o \<grade > seção.

3. Adicionar um \<TabControl > elemento e um \<TabItem > dentro de \< grade > elemento, conforme mostrado no exemplo a seguir.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Adicione um segundo \<TabItem >, com um \<botão > elemento que abre um novo projeto:

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

## <a name="test-the-custom-start-page"></a>Testar a página inicial personalizada

1. Pressione **F5**.

     A instância experimental do Visual Studio é aberto com a página inicial personalizada instalada, mas não selecionada.

2. Na instância experimental do Visual Studio, abra o **/Ferramentas opções / ambiente** página.

3. Selecione **inicialização**. Sobre o **Personalizar página inicial** lista, selecione sua *. XAML* de arquivo e, em seguida, clique em **Okey**.

4. Sobre o **modo de exibição** menu, clique em **Start Page**.

5. Clique o **Bing** guia.

     Você deve ver uma página da web do Bing.

6. Clique o **MyButton** guia.

     Você deve ver uma **MyProject** botão que abre o **novo projeto** caixa de diálogo.

7. Feche a instância experimental.

Para aplicar a página inicial personalizada, na **ferramentas** > **opções** > **ambiente**, selecione **inicialização**. Sobre o **Personalizar página inicial** lista, selecione sua *. XAML* de arquivo e, em seguida, clique em **Okey**.

## <a name="next-steps"></a>Próximas etapas

A página de início do Visual Studio agora contém uma guia que exibe uma guia de MyButton e uma guia do navegador da Web. Você pode criar páginas iniciais personalizadas que têm outras funcionalidades usando o *de lógica* modelo para adicionar um arquivo. dll personalizado, conforme mostrado na [adicionando o controle de usuário para a página início](../extensibility/adding-user-control-to-the-start-page.md). Você pode compartilhar páginas iniciais personalizadas com outros usuários ao publicar o arquivo. VSIX resultante para o [Visual Studio Marketplace](https://marketplace.visualstudio.com/) site da Web ou para outro site da Web ou de rede no compartilhamento. Para obter mais informações, consulte [implantação de páginas de inicialização personalizada](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Consulte também

- [Personalizar a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)
- [Controles de contêiner do WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)