---
title: 'Como: Incluir pré-requisitos com um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b83272cedce161ce9122d5877ab4afecca1b3ec
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998502"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Como: Incluir pré-requisitos com um aplicativo ClickOnce
Antes que possa distribuir o software necessário com um aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], primeiro você deverá baixar os pacotes de instalador desses pré-requisitos em seu computador de desenvolvimento. Quando você publicar um aplicativo e escolher **Baixar pré-requisitos da mesma localização que meu aplicativo baixa**, ocorrerá um erro se os pacotes de instalador não estiverem na pasta **Pacotes**.  
  
> [!NOTE]
>  Para adicionar um pacote do instalador para o .NET Framework, consulte [guia de implantação do .NET Framework para desenvolvedores](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
##  <a name="Package"></a> Para adicionar um pacote de instalador ao usar Package.xml  
  
1. No Explorador de Arquivos, abra a pasta **Pacotes**.  
  
    Por padrão, o caminho é *C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* em um sistema de 32 bits e *C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* em um sistema de 64 bits.  
  
2. Abra a pasta do pré-requisito que você deseja adicionar e, em seguida, abra a pasta do idioma da versão instalada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (por exemplo, **en** para inglês).  
  
3. No Bloco de Notas, abra o arquivo *Package.xml*.  
  
4. Localize o **nome** elemento que contém **http://go.microsoft.com/fwlink**e copie a URL. Inclua a parte **LinkID**.  
  
   > [!NOTE]
   >  Se nenhum **nome** elemento contém **http://go.microsoft.com/fwlink**, abra o **Product** arquivo na pasta raiz do pré-requisito e localize o **fwlink** cadeia de caracteres.  
  
   > [!IMPORTANT]
   >  Alguns pré-requisitos têm vários pacotes de instalador (por exemplo, para sistemas de 32 bits ou 64 bits). Se vários elementos **Name** contiverem **fwlink**, você deverá repetir as etapas restantes para cada um deles.  
  
5. Cole a URL na barra de endereços de seu navegador e, quando a execução ou gravação for solicitada, escolha **Salvar**.  
  
    Essa etapa baixará o arquivo do instalador em seu computador.  
  
6. Copie o arquivo na pasta raiz do pré-requisito.  
  
    Por exemplo, para o pré-requisito Windows Installer 4.5, copie o arquivo na pasta *\Packages\WindowsInstaller4_5*.  
  
    Agora você poderá distribuir o pacote de instalador com seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)