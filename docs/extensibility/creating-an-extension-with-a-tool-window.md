---
title: Criando uma extensão com uma janela de ferramentas | Microsoft Docs
description: Saiba como usar o modelo de projeto VSIX e o modelo de item da janela de ferramentas personalizada para criar uma extensão com uma janela de ferramentas.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b03b7a4941609462fca27bebf67d8ad2a8f7044
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944915"
---
# <a name="create-an-extension-with-a-tool-window"></a>Criar uma extensão com uma janela de ferramentas

Neste procedimento, você aprende a usar o modelo de projeto VSIX e o modelo de item da **janela de ferramentas personalizada** para criar uma extensão com uma janela de ferramentas.

## <a name="prerequisites"></a>Pré-requisitos

 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Criar uma janela de ferramentas

1. Crie um projeto VSIX chamado **FirstWindow**. Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **novo projeto** pesquisando por "VSIX".

2. Quando o projeto for aberto, adicione um modelo de item da janela de ferramentas chamado **MyWindow**. Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar**  >  **novo item**. Na caixa de diálogo **Adicionar novo item** , vá para extensibilidade do **Visual C#**  >   e selecione **janela de ferramenta personalizada**. No campo **nome** na parte inferior da janela, altere o nome do arquivo da janela de ferramentas para *MyWindow.cs*.

3. Compile o projeto e comece a depuração.

   A instância experimental do Visual Studio é exibida. Para obter mais informações sobre a instância experimental, consulte [a instância experimental](../extensibility/the-experimental-instance.md).

4. Na instância experimental, vá para **Exibir**  >  **outras janelas**.

   Você deverá ver um item de menu para **MyWindow**. Clique.

   Você deve ver uma janela de ferramentas com o título **MyWindow** e um botão dizendo **Click me!.**
