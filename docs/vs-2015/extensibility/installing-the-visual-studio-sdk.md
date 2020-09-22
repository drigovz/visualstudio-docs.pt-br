---
title: Instalando o SDK do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839261"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalando o SDK do Visual Studio como parte de uma instalação do Visual Studio  
 Se você quiser incluir o VSSDK em sua instalação do Visual Studio, deverá fazer uma instalação personalizada.  
  
> [!NOTE]
> No executável da instalação, o SDK do Visual Studio é chamado de **ferramentas de extensibilidade do Visual Studio**.  
  
1. Inicie a instalação do Visual Studio 2015. Você pode instalar qualquer edição do Visual Studio, exceto Express.  
  
2. Na primeira tela, selecione **personalizado**, não **padrão**. Clique em **Avançar**.  
  
3. Você deve ver uma exibição de árvore de recursos personalizados. Abra **ferramentas comuns**. Você deve ver **ferramentas de extensibilidade do Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Marque **ferramentas de extensibilidade do Visual Studio** e clique em **Avançar** e continue a instalação.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalando o SDK do Visual Studio após a instalação do Visual Studio  
 Se você decidir instalar o SDK do Visual Studio após concluir a instalação do Visual Studio, siga o seguinte procedimento:  
  
1. Vá para **painel de controle/programas/programas e recursos**e procure o **Visual Studio 2015**. Você pode instalar o SDK do Visual Studio para qualquer edição do Visual Studio 2015, exceto Express.  
  
2. Clique com o botão direito do mouse em **Visual Studio 2015**e clique em **alterar**. Você deverá ver a página de instalação.  
  
3. Siga o mesmo procedimento que a instalação **do SDK do Visual Studio como parte de uma instalação do Visual Studio** acima.  
  
4. Clique no link **ferramentas de extensibilidade do Visual Studio** para instalar o SDK do Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalando o SDK do Visual Studio de uma solução  
 Se você abrir uma solução com um projeto de extensibilidade sem primeiro instalar o VSSDK, será solicitada uma barra de informações realçada acima da Gerenciador de Soluções. A saída deve ter uma aparência semelhante à que se segue:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalando o SDK do Visual Studio na linha de comando  
 Você pode instalar o VSSDK da linha de comando usando a opção **/installselectableitems.** com o instalador do Visual Studio. Para obter detalhes sobre como usar parâmetros de linha de comando com o instalador, consulte [instalando o Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Aqui está como instalar o VSSDK silenciosamente usando o instalador da Comunidade do Visual Studio 2015:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Observe que você deve usar o instalador do Visual Studio que corresponde à sua versão instalada do Visual Studio. Por exemplo, se você tiver Visual Studio Enterprise instalado em seu computador, deverá executar o instalador do Visual Studio Enterprise (vs_enterprise.exe).
