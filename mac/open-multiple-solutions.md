---
title: Como abrir várias soluções
description: Saiba como abrir mais de uma solução no Visual Studio para Mac e como abrir mais de uma instância do aplicativo.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/02/2019
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.openlocfilehash: 4d676f6109c97ae883473a35721f9207e72a6da4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68872356"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Abrir várias soluções ou instâncias do Visual Studio para Mac

Por padrão, todos os aplicativos de um Mac, incluindo o Visual Studio para Mac, são aplicativos de _instância única_. Isso significa que se o aplicativo que você deseja usar já estiver aberto (ilustrado por um ponto sob o ícone no encaixe), selecionar o ícone novamente abrirá a instância em execução, em vez de uma nova. Caso precise de instâncias adicionais do aplicativo, solicite ao sistema para abri-las para você, conforme descrito na [próxima seção](#open-a-second-instance-of-visual-studio-for-mac).

Além disso, quando você abre uma solução, o comportamento padrão é abrir a solução em um novo workspace e fechar o workspace atual (se necessário). Substitua esse comportamento padrão mantendo o workspace atual aberto, conforme descrito na seção [Abrir uma segunda solução](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Abrir uma segunda instância do Visual Studio para Mac

Para abrir uma segunda instância do IDE (ambiente de desenvolvimento integrado), clique com o botão direito do mouse no ícone do Visual Studio no seu encaixe ou na pasta **Aplicativos** e selecione **Nova Instância**.

![Captura de tela do menu Nova Instância após clicar com o botão direito do mouse no ícone do Visual Studio](media/open-new-instance.png)

## <a name="open-a-second-solution-inside-a-single-instance"></a>Abrir uma segunda solução dentro de uma instância única

Para abrir uma segunda solução junto com a primeira solução, use as seguintes etapas:

1. Com sua primeira solução já aberta, selecione **Arquivo** > **Aberto**.
2. Navegue pelo sistema de arquivos para encontrar a solução existente.
3. Selecione o arquivo **.sln** e depois **Opções**:

    ![Captura de tela do Visual Studio para Mac, com o arquivo .sln e Opções realçados](media/open-multiple-solutions-image3.png)

4. Desmarque a caixa **Fechar workspace atual**:

    ![Captura de tela da caixa de diálogo Opções, com a caixa Fechar workspace atual desmarcada](media/open-multiple-solutions-image1.png)

5. Selecione **Abrir** para abrir a segunda solução no Painel de Soluções.

Como alternativa, se você abriu a solução recentemente, use as seguintes etapas:

1. Ir para **arquivar** > **soluções recentes**.

    ![Captura de tela do menu Soluções Recentes](media/open-multiple-solutions-image2.png)

1. Mantenha a tecla **Ctrl** pressionada e selecione a solução. Essa combinação abre a segunda solução no Painel de Soluções.

## <a name="related-video"></a>Vídeo relacionados

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
