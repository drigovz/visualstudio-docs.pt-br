---
title: 'Como: Verificar se há atualizações do aplicativo programaticamente usando a API de implantação do ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ac7a5665b287f51e59d99d21802acc252a55a99a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928402"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Como: Verificar se há atualizações do aplicativo programaticamente usando a API de implantação do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce oferece duas maneiras de atualizar um aplicativo quando ele é implantado. No primeiro método, você pode configurar a implantação do ClickOnce para verificar automaticamente as atualizações em determinados intervalos. No segundo método, você pode escrever código que usa o <xref:System.Deployment.Application.ApplicationDeployment> classe para verificar se há atualizações com base em um evento, como uma solicitação de usuário.  
  
 Os procedimentos a seguir mostram alguns códigos para executar uma atualização através de programação e também descrevem como configurar sua implantação de ClickOnce para habilitar as verificações de atualização através de programação.  
  
 Para atualizar um aplicativo ClickOnce por meio de programação, você deve especificar um local para atualizações. Isso às vezes é chamado como um provedor de implantação. Para obter mais informações sobre como definir essa propriedade, consulte [escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Você também pode usar a técnica descrita abaixo para implantar seu aplicativo de um local, mas atualizá-la de outro. Para obter mais informações, confira [Como: Especifique um local alternativo para atualizações da implantação](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Para verificar atualizações programaticamente  
  
1.  Crie um novo aplicativo de formulários do Windows usando suas ferramentas de linha de comando ou visual preferidas.  
  
2.  Crie qualquer botão, o item de menu, ou outro item de interface do usuário que você deseja que os usuários selecionem para verificar se há atualizações. Manipulador de eventos do item, chame o método a seguir para verificar e instalar atualizações.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3.  Compile o aplicativo.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Usando Mage.exe para implantar um aplicativo que verifica se há atualizações de forma programática  
  
-   Siga as instruções para implantar seu aplicativo usando Mage.exe conforme explicado em [passo a passo: Como implantar manualmente aplicativos ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Ao chamar Mage.exe para gerar o manifesto de implantação, certifique-se de usar a opção de linha de comando `providerUrl`e para especificar a URL em que o ClickOnce deve verificar por atualizações. Se seu aplicativo será atualizada da [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), por exemplo, sua chamada para gerar o manifesto de implantação pode ser assim:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Usando MageUI.exe para implantar um aplicativo que verifica se há atualizações de forma programática  
  
-   Siga as instruções para implantar seu aplicativo usando Mage.exe conforme explicado em [passo a passo: Como implantar manualmente aplicativos ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Sobre o **opções de implantação** guia, defina o **local inicial** campo ao manifesto do aplicativo ClickOnce deve verificar se há atualizações. No **opções de atualização** guia, desmarque as **este aplicativo deve verificar por atualizações** caixa de seleção.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Seu aplicativo deve ter permissões de confiança total para usar a atualização através de programação.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Especifique um local alternativo para atualizações da implantação](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
