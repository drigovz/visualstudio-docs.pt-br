---
title: Como especificar onde o Visual Studio 2015 copia arquivos | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8759145dd4a7647cad6e9964ae1f1c97d333b626
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65226165"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Como especificar onde o Visual Studio copiará os arquivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você publica um aplicativo usando o ClickOnce, a `Publish Location` propriedade especifica o local onde os arquivos de aplicativo e o manifesto são colocados. Pode ser um caminho de arquivo ou o caminho para um servidor FTP.

 Você pode especificar a `Publish Location` Propriedade na página **publicar** do designer de **projeto**ou usando o assistente de publicação. Para obter mais informações, consulte [como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Ao instalar mais de uma versão de um aplicativo usando o ClickOnce, a instalação moverá as versões anteriores do aplicativo para uma pasta chamada Arquivo, no local de publicação especificado. O arquivamento de versões anteriores dessa maneira mantém o diretório de instalação livre de pastas da versão anterior.

### <a name="to-specify-a-publishing-location"></a>Para especificar um local de publicação

1. Com um projeto selecionado no **Gerenciador de soluções**, no menu **projeto** , clique em **Propriedades**.

2. Clique na guia **Publicar**.

3. No campo **publicar local** , insira o local de publicação usando um dos seguintes formatos:

   - Para publicar em um compartilhamento de arquivos ou caminho de disco, insira o caminho usando um caminho UNC ( \\ \Server\ApplicationName) ou um caminho de arquivo (C:\Deploy\ApplicationName).

   - Para publicar em um servidor FTP, insira o caminho usando o formato FTP: \/ /ftp.Microsoft.com/ApplicationName.

     Observe que o texto deve estar presente na caixa **local de publicação** para que o botão procurar (**...**) funcione.

## <a name="see-also"></a>Consulte Também
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md) [como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
