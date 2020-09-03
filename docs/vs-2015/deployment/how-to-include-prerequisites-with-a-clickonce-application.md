---
title: 'Como: incluir pré-requisitos com um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9639da1f735095f6d04a59d1f2302f822423e006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557682"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Como incluir pré-requisitos com um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Antes que possa distribuir o software necessário com um aplicativo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], primeiro você deverá baixar os pacotes de instalador desses pré-requisitos em seu computador de desenvolvimento. Quando você publica um aplicativo e escolhe **baixar pré-requisitos do mesmo local que o meu aplicativo**, ocorrerá um erro se os pacotes do instalador não estiverem na pasta **pacotes** .  
  
> [!NOTE]
> Para adicionar um pacote do instalador para o .NET Framework, consulte [.NET Framework guia de implantação para desenvolvedores](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Para adicionar um pacote de instalador ao usar Package.xml  
  
1. No Explorador de Arquivos, abra a pasta **Pacotes**.  
  
     Por padrão, o caminho é C:\Program Files\Microsoft Visual Studio 14.0 \ SDK\Bootstrapper\Packages em um sistema de 32 bits e C:\Arquivos de programas (x86) \Microsoft Visual Studio 14.0 \ SDK\Bootstrapper\Packages em um sistema de 64 bits.  
  
2. Abra a pasta do pré-requisito que você deseja adicionar e, em seguida, abra a pasta do idioma da versão instalada de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (por exemplo, **en** para inglês).  
  
3. No Bloco de Notas, abra o arquivo **Package.xml**.  
  
4. Localize o elemento **Name** que contém `http://go.microsoft.com/fwlink` e copie a URL. Inclua a parte **LinkID**.  
  
    > [!NOTE]
    > Se nenhum elemento de **nome** contiver `http://go.microsoft.com/fwlink` , abra o arquivo **Product.xml** na pasta raiz para obter o pré-requisito e localize a cadeia de caracteres **fwlink** .  
  
    > [!IMPORTANT]
    > Alguns pré-requisitos têm vários pacotes de instalador (por exemplo, para sistemas de 32 bits ou 64 bits). Se vários elementos **Name** contiverem **fwlink**, você deverá repetir as etapas restantes para cada um deles.  
  
5. Cole a URL na barra de endereços de seu navegador e, quando a execução ou gravação for solicitada, escolha **Salvar**.  
  
     Essa etapa baixará o arquivo do instalador em seu computador.  
  
6. Copie o arquivo na pasta raiz do pré-requisito.  
  
     Por exemplo, para o pré-requisito Windows Installer 4.5, copie o arquivo na pasta \Packages\WindowsInstaller4_5.  
  
     Agora você poderá distribuir o pacote de instalador com seu aplicativo.  
  
## <a name="see-also"></a>Consulte Também  
 [Como instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
