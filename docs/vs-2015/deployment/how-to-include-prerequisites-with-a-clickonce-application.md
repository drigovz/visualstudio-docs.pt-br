---
title: 'Como: Incluir pré-requisitos com um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdeb1b847b746807c80509f4390daf445f65d90f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697667"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Como: Incluir pré-requisitos com um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Antes que possa distribuir o software necessário com um aplicativo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], primeiro você deverá baixar os pacotes de instalador desses pré-requisitos em seu computador de desenvolvimento. Quando você publicar um aplicativo e escolha **baixar os pré-requisitos no mesmo local que meu aplicativo**, ocorrerá um erro se os pacotes de instalador não estiverem na **pacotes** pasta.  
  
> [!NOTE]
> Para adicionar um pacote do instalador para o .NET Framework, consulte [guia de implantação do .NET Framework para desenvolvedores](https://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
## <a name="Package"></a> Para adicionar um pacote de instalador ao usar Package.xml  
  
1. No Explorador de Arquivos, abra a pasta **Pacotes**.  
  
     Por padrão, o caminho é C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages em um sistema de 32 bits e C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages em um sistema de 64 bits.  
  
2. Abra a pasta do pré-requisito que você deseja adicionar e, em seguida, abra a pasta do idioma da versão instalada de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (por exemplo, **en** para inglês).  
  
3. No Bloco de Notas, abra o arquivo **Package.xml**.  
  
4. Localize o **nome** elemento que contém **http://go.microsoft.com/fwlink** e copie a URL. Inclua a parte **LinkID**.  
  
    > [!NOTE]
    > Se nenhum **nome** elemento contém **http://go.microsoft.com/fwlink** , abra o **Product** arquivo na pasta raiz do pré-requisito e localize o **fwlink** cadeia de caracteres.  
  
    > [!IMPORTANT]
    > Alguns pré-requisitos têm vários pacotes de instalador (por exemplo, para sistemas de 32 bits ou 64 bits). Se vários elementos **Name** contiverem **fwlink**, você deverá repetir as etapas restantes para cada um deles.  
  
5. Cole a URL na barra de endereços de seu navegador e, quando a execução ou gravação for solicitada, escolha **Salvar**.  
  
     Essa etapa baixará o arquivo do instalador em seu computador.  
  
6. Copie o arquivo na pasta raiz do pré-requisito.  
  
     Por exemplo, para o pré-requisito Windows Installer 4.5, copie o arquivo na pasta \Packages\WindowsInstaller4_5.  
  
     Agora você poderá distribuir o pacote de instalador com seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
