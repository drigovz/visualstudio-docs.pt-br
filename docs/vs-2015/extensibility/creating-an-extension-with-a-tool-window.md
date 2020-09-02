---
title: Criando uma extensão com uma janela de ferramentas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431843"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Criando uma extensão com uma janela de ferramentas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Neste procedimento, você aprende a usar o modelo de projeto VSIX e o modelo de item da **janela de ferramentas personalizada** para criar uma extensão com uma janela de ferramentas.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Criando uma janela de ferramentas  
  
1. Crie um projeto VSIX chamado **FirstWindow**. Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **novo projeto** em **Visual C#/extensibilidade**.  
  
2. Quando o projeto for aberto, adicione um modelo de item da janela de ferramentas chamado **FirstWindow**. Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar/novo item**. Na caixa de diálogo **Adicionar novo item** , vá para **Visual C#/extensibilidade** e selecione **janela de ferramenta personalizada**. No campo **nome** na parte inferior da janela, altere o nome do arquivo da janela de ferramentas para **FirstWindow.cs**.  
  
3. Compile o projeto e comece a depuração.  
  
     A instância experimental do Visual Studio é exibida. Para obter mais informações sobre a instância experimental, consulte [a instância experimental](../extensibility/the-experimental-instance.md).  
  
4. Na instância experimental, vá para **exibição/outras janelas**.  
  
     Você deverá ver um item de menu para **FirstWindow**. Clique.  
  
     Você deve ver uma janela de ferramentas com o título **FirstWindow** e um botão dizendo **Click me!.**
