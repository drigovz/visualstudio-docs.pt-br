---
title: Instalar o SDK do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1da992ebdb5c3d4e0381cdc388dcf6ad5d2af66c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091142"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalando o SDK do Visual Studio como parte de uma instalação do Visual Studio  
 Se você quiser incluir VSSDK em sua instalação do Visual Studio, você deve fazer uma instalação personalizada.  
  
> [!NOTE]
>  O executável de instalação, o SDK do Visual Studio é chamado **ferramentas de extensibilidade do Visual Studio**.  
  
1. Inicie a instalação do Visual Studio 2015. Você pode instalar qualquer edição do Visual Studio, exceto Express.  
  
2. Na primeira tela, selecione **personalizado**, e não **padrão**. Clique em **Avançar**.  
  
3. Você deve ver uma exibição de árvore de recursos personalizados. Abra **ferramentas comuns**. Você deve ver **ferramentas de extensibilidade do Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Verifique **ferramentas de extensibilidade do Visual Studio** , em seguida, clique em **próxima** e continuar a instalação.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalando o SDK do Visual Studio depois de instalar o Visual Studio  
 Se você decidir instalar o SDK do Visual Studio depois de concluir a instalação do Visual Studio, você deve seguir o procedimento a seguir:  
  
1. Vá para **painel de controle / programas / programas e recursos**e procure **Visual Studio 2015**. Você pode instalar o SDK do Visual Studio para qualquer edição do Visual Studio 2015, exceto Express.  
  
2. Clique com botão direito **Visual Studio 2015**e, em seguida, clique em **alteração**. Você deve ver a página de instalação.  
  
3. Siga o mesmo procedimento como em **instalando o SDK do Visual Studio como parte de uma instalação do Visual Studio** acima.  
  
4. Clique o **ferramentas de extensibilidade do Visual Studio** link para instalar o SDK do Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalar o SDK do Visual Studio de uma solução  
 Se você abrir uma solução com um projeto de extensibilidade sem precisar instalar primeiro o VSSDK, você será solicitado por uma barra de informações realçado acima do Gerenciador de soluções. Ele deve ser algo semelhante ao seguinte:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalar o SDK do Visual Studio na linha de comando  
 Você pode instalar VSSDK da linha de comando usando o **/installselectableitems.** alternar com o instalador do Visual Studio. Para obter detalhes sobre como usar parâmetros de linha de comando com o instalador, consulte [instalar o Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Aqui está como instalar silenciosamente usando o instalador do Visual Studio 2015 Community VSSDK:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Observe que você deve usar o instalador do Visual Studio que corresponde à sua versão instalada do Visual Studio. Por exemplo, se você tiver o Visual Studio Enterprise instalado em seu computador, você deve executar o instalador do Visual Studio Enterprise (vs_enterprise.exe).
