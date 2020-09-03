---
title: Publicar uma extensão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201975"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Passo a passo: publicando uma extensão do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Observação**: a galeria do Visual Studio está sendo substituída pelo Visual Studio Marketplace. Consulte a versão mais recente deste tópico para obter detalhes.

Este tutorial mostra como publicar uma extensão do Visual Studio na galeria do Visual Studio. Quando você adiciona sua extensão à galeria, os desenvolvedores podem usar **extensões e atualizações** para procurar por extensões novas e atualizadas.

## <a name="prerequisites"></a>Pré-requisitos
 Para seguir este passo a passos, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Criar uma extensão do Visual Studio
 Nesse caso, usaremos uma extensão VSPackage padrão, mas as mesmas etapas são válidas para cada tipo de extensão.

1. Crie um VSPackage em C# chamado `TestPublishing` que tenha um comando de menu. Para obter mais informações, consulte [criando uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Testar a extensão
 Antes de distribuir a extensão, crie-a e teste-a para verificar se ela está instalada corretamente na instância experimental do Visual Studio.

1. No Visual Studio, inicie a depuração. para abrir uma instância experimental do Visual Studio.

2. Na instância experimental, vá para o menu **ferramentas** e clique em **Gerenciador de extensões**. A extensão TestPublishing deve aparecer no painel central e ser habilitada.

3. No menu **ferramentas** , verifique se você vê o comando de teste.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publicar a extensão na galeria do Visual Studio
 Agora você pode publicar a extensão na galeria do Visual Studio.

1. Certifique-se de que você criou a versão de lançamento da extensão e que ela está atualizada.

2. Em um navegador da Web, abra o site do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

3. No canto superior direito, clique em **entrar**.

4. Use seu conta Microsoft para entrar. Se você não tiver um conta Microsoft, poderá criar um neste ponto.

5. Clique em **Carregar**.

6. Na **etapa 1: tipo de extensão**, selecione **ferramenta** e clique em **Avançar**.

7. Na **etapa 2: carregar**, você pode optar por carregar diretamente na galeria do Visual Studio ou apenas adicionar um link para seu próprio site. Nesse caso, selecione **eu gostaria de carregar minha ferramenta**. A caixa **selecionar seu controle** é exibida. Clique em **procurar** e selecione TestPublish. vsix na pasta \bin\release do projeto. Clique em **Avançar**.

8. Na **etapa 3: informações básicas**, campos do arquivo Source. Extension. vsixmanifest são exibidos. Selecione uma **categoria** apropriada e adicione **marcas** para ajudar os usuários a localizar sua extensão. Talvez você queira adicionar um resumo e uma descrição mais detalhados (a descrição deve ter pelo menos 280 caracteres). Deixe **tipo de extensão** como **não sendo uma extensão da Microsoft e uma** categoria de **custo** como **avaliação**.

9. Leia o contrato de contribuição na parte inferior da página e selecione **concordo**.

10. Clique em **criar contribuição**. Isso exibirá a página que sua extensão terá na galeria do Visual Studio, com uma mensagem informando que a página ainda não foi publicada.

11. Clique em **Publicar**.

12. Pesquise a sua extensão na galeria do Visual Studio. A listagem para a extensão TestPublish deve aparecer.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Instalar a extensão da galeria do Visual Studio
 Agora que a extensão foi publicada, instale-a no Visual Studio e teste-a lá.

1. No Visual Studio, no menu **ferramentas** , clique em **extensões e atualizações**.

2. Clique em **online** e procure por TestPublish. A listagem para a extensão TestPublish deve aparecer.

3. Clique em **Download**. Depois que a extensão for baixada, clique em **instalar**.

4. Para concluir a instalação, reinicie o Visual Studio.

## <a name="removing-the-extension"></a>Removendo a extensão
 Você pode remover a extensão da galeria do Visual Studio e do seu computador.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Para remover a extensão da galeria do Visual Studio

1. Abra o site [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

2. No canto superior direito, clique em **meu Extenions**. A listagem para TestPublish é exibida.

3. Clique em **Excluir**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Para remover a extensão do seu computador

1. No Visual Studio, no menu **ferramentas** , clique em **Gerenciador de extensões**.

2. Selecione TestPublish e clique em **desinstalar**.

3. Para concluir a desinstalação, reinicie o Visual Studio.
