---
title: Criando uma extensão com uma janela de ferramentas | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739545"
---
# <a name="create-an-extension-with-a-tool-window"></a>Crie uma extensão com uma janela de ferramenta

Neste procedimento, você aprende a usar o modelo de projeto VSIX e o modelo de item **custom tool window** para criar uma extensão com uma janela de ferramenta.

## <a name="prerequisites"></a>Pré-requisitos

 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Criar uma janela de ferramenta

1. Crie um projeto VSIX chamado **FirstWindow**. Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Projeto Novo** procurando por "vsix".

2. Quando o projeto for aberto, adicione um modelo de item de janela de ferramenta chamado **MyWindow**. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Na **caixa de diálogo Adicionar novo item,** vá para A**Extensibilidade** **Visual C#** > e selecione **Janela de ferramenta personalizada**. No **campo Nome,** na parte inferior da janela, altere o nome do arquivo da janela da ferramenta para *MyWindow.cs*.

3. Compile o projeto e comece a depuração.

   A instância experimental do Visual Studio aparece. Para obter mais informações sobre a instância experimental, consulte [A instância experimental](../extensibility/the-experimental-instance.md).

4. Na instância experimental, vá para **Exibir** > **outros Windows**.

   Você deve ver um item de menu para **MyWindow**. Clique.

   Você deve ver uma janela de ferramenta com o título **MyWindow** e um botão dizendo **Clique em Mim!.**
